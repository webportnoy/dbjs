# DBJS

## Работа с массивом объектов в стиле SQL


```js
	// Создание объекта
	var db = new database();

	// Добавление данных массивом
	db.insert([
		{id: 1, name: "Nick"},
		{id: 2, name: "Poul"},
		{id: 3, name: "Aaron"},
		{id: 4, name: "Nick"},
		{id: 5, name: "Buzz"}]
		);

	// Добавление данных построчно
	db.insert({id: 6, name: "Santa"});

	// Запрос вернет массив из объектов соответсвующих условиям
	db.select('id, test, name').where("`name`!='Nick'").query();

	// Пример с группировкой
	db.select('id, count(*), name').groupby('name').query();

	// Пример с сортировкой и группировкой
	db.select('id, count(*), name').groupby('name').orderby('count(*) desc').query();

	// Аналог предыдущего примера одним вызовом
	db.query({select: 'id, count(*), name', groupby: 'name', orderby: 'count(*) desc'});

	// Получить только первую строку
	db.limit('1').query();

	// Получить две строки начиная с 3-й
	db.limit('3, 2').query();

	// Удалить все данные
	db.truncate();

	// Вернуть количество найденных запросом строк
	db.num_rows();

	// Вернуть количество колонок в результате запроса
	db.num_cols();

	// Вернуть названия колонок
	db.show_columns();

	TODO:
	update method
	delete method
```