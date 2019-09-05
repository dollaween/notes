# Sequelize

### Пример модели
``` javascript
import { defaultModelSettings } from '../constants/models';

module.exports = (sequelize, DataTypes) => {
    return sequelize.define('Project', {
        slug: { type: DataTypes.STRING(100), allowNull: true, defaultValue: null },
        link: { type: DataTypes.STRING(255), allowNull: true, defaultValue: null },
        title: { type: DataTypes.STRING(100), allowNull: false },
        client: { type: DataTypes.STRING(255), allowNull: true, defaultValue: null },
        problem: { type: DataTypes.STRING(255), allowNull: true, defaultValue: null },
        solution: { type: DataTypes.TEXT, allowNull: true, defaultValue: null },
        isBest: { type: DataTypes.BOOLEAN, allowNull: true, defaultValue: false },
        isDeleted: { type: DataTypes.BOOLEAN, defaultValue: false },
        imageMain: { type: DataTypes.STRING(255), allowNull: true, defaultValue: null },
        image: {
            type: DataTypes.STRING(2000),
            allowNull: true,
            defaultValue: null,
            get() {
                return this.getDataValue('image')
                    ? JSON.parse(this.getDataValue('image'))
                    : null;
            },
            set(val) {
                this.setDataValue('image', JSON.stringify(val));
            },
        },
        tags: {
            type: DataTypes.STRING,
            allowNull: true,
            get() {
                return this.getDataValue('tags')
                    ? JSON.parse(this.getDataValue('tags'))
                    : null;
            },
            set(val) {
                this.setDataValue('tags', JSON.stringify(val));
            },
        },
    }, { sequelize, ...defaultModelSettings });
};
```
