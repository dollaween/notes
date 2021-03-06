# Sequelize

- [Валидация](https://sequelize.org/master/manual/models-definition.html#validations)
- [Индексы](https://sequelize.org/master/manual/models-definition.html#indexes)
- [Список хуков](https://github.com/sequelize/sequelize/blob/master/lib/hooks.js#L7)
- [Операторы сравнения](https://sequelize.org/master/manual/querying.html#operators)
- [Сортировка](https://sequelize.org/master/manual/querying.html#ordering)
- [Ассоциативные запросы](https://sequelize.org/master/manual/querying.html#relations---associations)

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


### Аттрибуты и методы
``` javascript
{
    allowNull: false,
    autoIncrement: true,
    defaultValue: null,
    unique: true,

    references: {
        model: Bar,
        key: 'id'
    },

    get() {
        const title = this.getDataValue('title');
        return title.toLowerCase();
    }

    set(val) {
        this.setDataValue('title', val.toUpperCase());
    }
}
```


### Options
``` javascript
{
    timestaps: true,
    
    getterMethods: {
        fullName() {
            return this.firstname + ' ' + this.lastname;
        }
    },
    
    setterMethods: {
        fullName(val) {
            const names = val.split(' ');
            this.setDataValue('firstname', names.slice(0, -1).join(' '));
            this.setDataValue('lastname', names.slice(-1).join(' '));
        }
    },
    
    validate: {},       // срабатывает после всех других валидаций
    
    paranoid: true,     // не удаляет записи из базы, а добавляет им аттрибут deletedAt
    
    underscored: true,  // устанаваливает snake cased нотацию для атрибутов
    
    freezeTableName: true,
    tableName: 'my_very_custom_table_name',
    version: true,
    sequelize,          // Sequelize instance
}
```
