# Sequelize

### Пример модели
``` javascript
import { defaultModelSettings } from '../constants/models';

module.exports = (sequelize, DataTypes) => {
    return sequelize.define('Project', {
        title: { type: DataTypes.STRING(100), allowNull: false },
        slug: { type: DataTypes.STRING(100), allowNull: true, defaultValue: null },
        text: { type: DataTypes.TEXT, allowNull: true, defaultValue: null },
        isDeleted: { type: DataTypes.BOOLEAN, defaultValue: false },
        imageMain: { type: DataTypes.STRING(255), allowNull: true, defaultValue: null },
        deadline: {
            type: DataTypes.DATE,
            defaultValue: sequelize.literal('CURRENT_TIMESTAMP'),
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
    }, {
        sequelize,
        ...defaultModelSettings,
        timestaps: true,
    });
};
```
