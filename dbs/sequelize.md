# Sequelize

### Пример модели
``` javascript
import { defaultModelSettings } from '../constants/models';

module.exports = (sequelize, DataTypes) => {
    return sequelize.define('Project', {
        title: { type: DataTypes.STRING(100), allowNull: false },
        slug: {
            type: DataTypes.STRING(100),
            defaultValue: null,
            unique: true,
        },
        text: { type: DataTypes.TEXT, defaultValue: null },
        isDeleted: { type: DataTypes.BOOLEAN, defaultValue: false },
        imageMain: { type: DataTypes.STRING(255), defaultValue: null },
        deadline: {
            type: DataTypes.DATE,
            defaultValue: sequelize.literal('CURRENT_TIMESTAMP'),
        },
        tags: {
            type: DataTypes.STRING,
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
        ...defaultModelSettings,
        // ...options
    });
};
```


### Options
``` javascript
{
    timestaps: true,
}
```
