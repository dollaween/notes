/**
 * Устанавливает значение в объекте любой вложенности.
 * Если в цепочке путей будет отсутствовать объект — создает его
 * @param {object} obj — исходный объект
 * @param {string} str — путь к объекту. Например, 'state.filters.statuses.value'
 * @param {*} value — значение, которое надо установить
 * @param {string} separator — разделитель у str
 * @returns {object}
 */
export const setValueInDepthObject = (obj, str, value, separator = '.') => {
  if (!str) return obj;
  const paths = str.split(separator);

  const recursion = (obj = {}, paths) => {
    return paths.length === 1
      // если value — объект, то сохраняем предыдущие ключи
      ? getType(value) === 'object'
        ? { ...obj, [paths[0]]: { ...obj[paths[0]], ...value } }
        : { ...obj, [paths[0]]: value }
      : { ...obj, [paths[0]]: { ...recursion(obj[paths[0]], paths.slice(1)) } };
  };

  return recursion(obj, paths);
};
