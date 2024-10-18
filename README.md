# js-tasks
2) Напишите функцию для поверхностного сравнения двух объектов. Поверхностное сравнение объектов - это процесс сравнения ключей объекта и их значений, без учета уровня вложенности. То есть значение с типом object, никогда не будет равен точно такому же значению с типом object, т.к. ссылки на эти значения будут отличаться.
Пример работы функции сравнения:

shallowEquals({ a: 1, b: "2" }, { a: 1, b: "2" }); // true
shallowEquals({ a: 0 }, { a: undefined }); // false
shallowEquals({ a: {} }, { a: {} }); // false
shallowEquals({ a: [] }, { a: [] }); // false
shallowEquals({ a: () => {} }, { a: () => {} }); // false
 

3) Напишите функцию, которая будет устанавливать значение в объекте, по переданному пути. Сигнатура функции должна быть следующей function ([“user”, “name”], “Sam”, obj). После вызова функции, для поля obj.user.name должно быть установлено значение “Sam”.

4) Реализуйте, на выбор, один из методов массива: map, sort, filter. Пример работы:

[].myMap((item, index, arr) => {});
[].myFilter((item, index, arr) => {});
[].mySort((a, b) => {});
[].mySort();
5) Реализуйте функцию pipe. Она должна принимать неопределенное количество функций-обработчиков и возвращать функцию, которая будет прогонять принимаемый параметр через все обработчики, а на выходе вернет результат работы. Функции-обработчики должны вызываться справа налево.

const fillUser = pipe (
  (user) => ({ ...user, lastName: "Pass" }),
  (user) => ({ ...user, age: 29 }),
  (user) => ({ ...user, city: "Boston" }),
);
6) Напишите функцию для поиска значения в n-арном дереве. Если искомое значение отсутствует, необходимо вернуть значение -1. Найдите 11, 1 и 25 узел из дерева.

const tree = {
  node: 1,
  children: [
    {
      node: 2,
      children: [
        {
          node: 3,
          children: [
            {
              node: 4,
              children: [
                {
                  node: 5,
                  children: [],
                },
                {
                  node: 6,
                  children: [],
                },
                {
                  node: 7,
                  children: [],
                },
                {
                  node: 8,
                  children: [],
                },
              ],
            },
            {
              node: 9,
              children: [],
            },
          ],
        },
      ],
    },
    {
      node: 10,
      children: [
        {
          node: 11,
          children: [
            {
              node: 12,
              children: [],
            },
          ],
        },
        {
          node: 13,
          children: [],
        },
        {
          node: 14,
          children: [],
        },
      ],
    },
  ],
};
7) Напишите упрощенную версию для нативного типа данных Set, MySet. Ваша реализация должна предоставлять методы add, has, delete, clear и свойство size. При создании MySet принимает только массив, если передать другое значение, то необходимо выдавать ошибку, что переданное значение не поддерживается. Способы реализации методов произвольные. Пример работы MySet

const mySet = new MySet([ 0, 1, 2, 3]);

console.log(mySet); // { 0, 1, 2, 3, size: 4 }
console.log(mySet.size); // 4
console.log(mySet.has(6)); // false

mySet.add(4);
console.log(mySet); // { 0, 1, 2, 3, 4, size: 5 }

mySet.delete(2);
console.log(mySet); // { 0, 1, 2: 3, 3: 4, size: 4 }

mySet.clear();
console.log(mySet); // { size: 0 }
8) Напишите две функции для преобразования приведенного массива в указанный объект и для преобразования полученного объекта в исходный массив. Интерфейс объекта в массиве следующий: { name: string, value: number }.

[
  { name: "width", value: 100 },
  { name: "height", value: 50 },
]

{ width: 100, height: 50 }
9) Написать функцию asyncTimeout. Функция должна принимать значения timeout, по завершении которого возвращает зарезолвленный промис. Пример работы:

setTimeout(() => console.log(3), 2000);

console.log(1);

asyncTimeout(1000).then(() => console.log(2));
10) Напишите функцию promiseStack, которая принимает массив функций возвращающих промис и вызывает их в порядке очереди, пока первый промис не завершился второй не начинается. Результатом выполнения данного кода должно быть следующее:
через 4 секунды в консоль выведется “1”
еще через 2 секунды “2”
еще через 1 секунду “3”
еще через 3 секунды “4”

promiseStack([
  () => asyncTimeout(4000).then(() => console.log(1)),
  () => asyncTimeout(2000).then(() => console.log(2)),
  () => asyncTimeout(1000).then(() => console.log(3)),
  () => asyncTimeout(3000).then(() => console.log(4)),
]);
11) Обновите функцию promiseStack, таким образом, чтобы она принимала второй необязательный аргумент отвечающий за количество параллельно обрабатываемых промисов.Результатом выполнения данного кода должно быть следующее:
через 4 секунды в консоль выведется одновременно две “1”
еще через 2 секунды одновременно две “2”
еще через 1 секунду одновременно две “3”
еще через 3 секунды “4”

promiseStack([
  () => asyncTimeout(4000).then(() => console.log(1)),
  () => asyncTimeout(4000).then(() => console.log(1)),
  () => asyncTimeout(2000).then(() => console.log(2)),
  () => asyncTimeout(2000).then(() => console.log(2)),
  () => asyncTimeout(1000).then(() => console.log(3)),
  () => asyncTimeout(1000).then(() => console.log(3)),
  () => asyncTimeout(3000).then(() => console.log(4)),
], 2);


2) Напишите функцию для получения имени и фамилии из формы

<!DOCTYPE html>
<html>
  <head>
    <meta charset=utf-8 />
    <title>Return first and last name from a form - w3resource</title>
  </head>
  <body>
    <form id="form1" onsubmit="getFormvalue()">
      First name: <input type="text" name="fname" value="David"><br>
      Last name: <input type="text" name="lname" value="Beckham"><br>
      <input type="submit" value="Submit">
    </form>
  </body>
</html>
3) Напишите функцию JavaScript для добавления строк в таблицу.

<!DOCTYPE html>
<html>
  <head><meta charset=utf-8 />
    <title>Insert row in a table - w3resource</title>
  </head>
  <body>
    <table id="sampleTable" border="1">
      <tr>
        <td>Row1 cell1</td>
        <td>Row1 cell2</td>
      </tr>
      <tr>
        <td>Row2 cell1</td>
        <td>Row2 cell2</td>
      </tr>
    </table>
    <br>
    <input type="button" onclick="insert_Row()" value="Insert row"> 
  </body>
</html>
4) Напишите программу на JavaScript для вычисления объема сферы. 
