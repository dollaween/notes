# Sequelize Many to Many
Пример ассоциации таблиц Project и Tag.

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




### Model 2
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




### Controller
``` javascript

```
