# Sequelize Many to Many
Пример ассоциации таблиц Project и Tag.

Методы getTags, setTags, addTags, addTag не прикрепляются к модели. Их можно получить после того, как достали запись из базы данных, например через findOne или create.

### Model 1
``` javascript
module.exports = (sequelize, DataTypes) => {
    const Project = sequelize.define('Project', {
        title: { type: DataTypes.STRING(100), allowNull: false },
    });

    Project.associate = (models) => {
        Project.belongsToMany(models.Tag, {
            as: 'tags',
            through: 'ProjectTag',
            foreignKey: 'projectId',
        });
    }

    return Project;
};
```




## Model 2
``` javascript
module.exports = (sequelize, DataTypes) => {
    const Tag = sequelize.define('Tag', {
        title: { type: DataTypes.STRING(50), allowNull: false },
    });

    Tag.associate = (models) => {
        Tag.belongsToMany(models.Project, {
            as: 'projects',
            through: 'ProjectTag',
            foreignKey: 'tagId',
        });
    }

    return Tag;
};
```





### Initialize
``` javascript
import fs from 'fs';
import path from 'path';
import { Sequelize } from 'sequelize';
import config from '../../config/database.json';

const basename = path.basename(__filename);
const db = {};

const sequelize = new Sequelize(config.database, config.username, config.password, config);


fs
    .readdirSync(__dirname)
    .filter((file) => (file.indexOf('.') !== 0) && (file !== basename) && (file.slice(-3) === '.js'))
    .forEach((file) => {
        const model = sequelize.import(path.join(__dirname, file));
        db[model.name] = model;
    });

Object.keys(db).forEach((modelName) => {
    if (db[modelName].associate) {
        db[modelName].associate(db);
    }
});

db.sequelize = sequelize;
db.Sequelize = Sequelize;

module.exports = db;

```





### Controller getOn
Достаем один project со всеми tags, связанными с ним.
В project будет добавлено свойство tags.
``` javascript
exports.get = (req, res, next) => {
    const { id } = req.query;

    if (!id)
        return next('Request should contain project ID');

    const where = { id };

    Project
        .findOne({
            where,
            include: [{
                as: 'tags',
                model: Tag,
                required: false,
                through: { attributes: [] },
            }]
        })
        .then((result) => res.json(result) )
        .catch(err => next(err));
}
```





### Controller post
Заносим project в базу данных. Связываем project и tags.
``` javascript
exports.post = async (req, res, next) => {
    try {
        const project = req.body;

        if (project.id && Number(project.id) > 0)
            return next('Project ID must be 0 or not present');

        let createdProject = await Project.create(project);

        let tags = await modelHelper.getList(Tag, project.tags, 'id');
        createdProject.setTags(tags);

        return res.status(200).json(createdProject);

    } catch (err) {
        return next(err);
    }
}
```





### modelHelper
``` javascript
const getList = async (model, arr, field) => {
    let data = null;

    if (arr) {
        let values = arr.reduce( (acc, cur) => {
            acc.push(cur[field]);
            return acc;
        }, []);

        let where = {};
        where[field] = values;

        data = await model.findAll({ where });
    }

    return data;
}


exports.getList = getList;
```





### Controller put
``` javascript
exports.put = async (req, res, next) => {
    try {
        const { id, ...project } = req.body;

        if (id === undefined) return next('Project ID is not present');
        if (Number(id) <= 0) return next('Project ID must be > 0');

        await Project.update(project, { where: { id } });
        let updatedProject = await Project.findOne({ where: { id } });

        let tags = await modelHelper.getList(Tag, project.tags, 'id');
        updatedProject.setTags(tags);

        return res.status(200).json();

    } catch (err) {
        return next(err);
    }
}
```
