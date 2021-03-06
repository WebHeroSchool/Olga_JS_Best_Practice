

# JavaScript BestPractice #

***

1. <a href='#first-par'>Не используйте var</a>
2. <a href='#second-par'>Избегайте глобальных переменных</a>
3. <a href='#third-par'>Инициализируйте переменные при их объявлении</a>
4. <a href='#fourth-par'>Завершите переключатели (switch) по умолчанию</a>
5. <a href='#fifth-par'>Переменные</a>
6. <a href='#sixth-par'>Инициализируйте переменные при их объявлении</a>
7. <a href='#seventh-par'>Стрелочные функции</a>
8. <a href='#eighth-par'>Используйте {} вместо new Object()</a>
9. <a href='#ninth-par'>Операторы сравнения</a>
10. <a href='#tenth-par'>Остерегайтесь автоматических преобразований типов</a>

***

## <a name='#first-par'>1. Не используйте var</a>

Объявляйте все переменные с помощью const или let. Используйте const по умолчанию, если переменная не требует переназначения. Ключевое слово var не должно использоваться.
```js
//плохо
var a = 1;
var b = 2;
```
```js
//хорошо
const a = 1;
const b = 2;
```

## <a name='#second-par'>2. Избегайте глобальных переменных</a>
Глобальных переменных стоит избегать по нескольким причинам. Во-первых, их легко переписать в различных местах кода, потому что они везде доступны. Во-вторых, они могут переписывать объект window, так как являются свойствами объекта `window`. Две эти проблемы затрудняют восприятие кода. Следовательно, стоит определять локальные переменные настолько часто, насколько это возможно, используя ключевые слова `var`, `let` или `const`.
```js
//плохо
let firstNum = 2;
let secondNum = 1;

let sum = () => {
  firstNum + secondNum;
}
```
```js
//хорошо
let sum = () => {
  let firstNum = 2;
  let secondNum = 1;
  firstNum + secondNum;
}
```
## <a name='fifth-section'>3. Инициализируйте переменные при их объявлении</a>

Хорошей практикой кодирования является инициализация переменных при их объявлении.
Это:
+ Сделает код чище
+ Предоставит единственное место для инициализации переменных
+ Позволит избежать неопределенных значений
```js
// плохо
let firstName;

firstName = Ivan;
```
```js
// хорошо
let firstName = "Ivan",
```

## <a name='#fourth-par'>4. Завершите переключатели (switch) по умолчанию</a>
Всегда завершайте операторы switch значением default. Даже если вы думаете, что в этом нет необходимости.
```js
Пример
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
    day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
    break;
  default:
    day = "Unknown";
}
```
## <a name='#fifth-par'> 5. Переменные</a>
Для именования переменных используйте существительные на английском языке(не транслит!). Имя переменной должно быть осмысленным.

Имя может состоять из:
+ Букв
+ Цифр
+ Символов $ и _ 
+ Не должно начинаться с цифры.
```js
//хорошо
var vegetables;

```
```js
//плохо
const ovoschi;
const rrfgov;
```

## <a name='#sixth-par'>6. Инициализируйте переменные при их объявлении</a>
Хорошей практикой кодирования является инициализация переменных при их объявлении. Это:

+ Сделает код чище
+ Предоставит единственное место для инициализации переменных
+ Позволит избежать неопределенных значений

```js
//плохо
let firstName;

firstName = Ivan;
```
```js
//хорошо
let firstName = "Ivan";
```

## <a name='#seventh-par'>7. Стрелочные функции</a>

Стрелочные функции придают краткость синтаксису и исправляют многие сложности, с ним связанные. Отдавайте предпочтение стрелочным функциям, а не ключевым словам, особенно для вложенных функций. Обычные объявления функций применяются только в особых случаях. В частности, в методах объектов или в конструкторах. Делается это из-за особенностей ключевого слова `this`.
```js
//плохо
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
```
```js
//хорошо
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

## <a name='#eighth-par'>8. Используйте {} вместо new Object()</a>
Используйте "" вместо new String()
Используйте 0 вместо new Number()
Используйте false вместо new Boolean()
Используйте [] вместо new Array()
Используйте /()/ вместо new RegExp()
Используйте function (){} вместо new Function()
пример
```js
const x1 = {};           // new object
const x2 = "";           // new primitive string
const x3 = 0;            // new primitive number
const x4 = false;        // new primitive boolean
const x5 = [];           // new array object
const x6 = /()/;         // new regexp object
const x7 = function(){}; // new function object
```

## <a name='#ninth-par'>9. Операторы сравнения</a>
Используйте "===" для сравнения, вместо "==". Использование данного оператора позволяет избежать нежелательного преобразования типов данных. Если нам необходимо удостовериться, что переменные действительно идентичны друг другу, стоит использовать строгое равенство. Оператор == в действительности не сравнивает объекты, а пытается привести их к одному типу. К примеру, в выражении 5 == '5', строка справа конвертируется в число, и только потом сравнивается. Тогда как "===" не делает такого преобразования. Использование сравнения с преобразованием типов может привести к непредвиденным проблемам, связанным с особенностями конвертации разных типов. Например, Объекты String имеют тип Object, а не String.
```js
// пример
0 == "";        // true
1 == "1";       // true
1 == true;      // true

0 === "";       // false
1 === "1";      // false
1 === true;     // false
```

## <a name='#tenth-par'>10. Остерегайтесь автоматических преобразований типов.

Помните, что числа могут быть случайно преобразованы в строки или NaN (Not a Number / Не число).

Переменная может содержать разные типы данных, а переменная может изменять свой тип данных:
``` js
let x = "Hello";     // по типу x является строкой
x = 5;               // изменение типа x на число
```
При выполнении математических операций JavaScript может преобразовывать числа в строки:
```js
var x = 5 + 7;       // x.valueOf() является 12,  тип x является числом
var x = 5 + "7";     // x.valueOf() является 57,  тип x является строкой
var x = "5" + 7;     // x.valueOf() является 57,  тип x является строкой
var x = 5 - 7;       // x.valueOf() является -2,  тип x является числом
var x = 5 - "7";     // x.valueOf() является -2,  тип x является числом
var x = "5" - 7;     // x.valueOf() является -2,  тип x является числом
var x = 5 - "x";     // x.valueOf() является NaN, тип x является числом
```
Вычитание строки из строки не генерирует ошибку, но возвращает NaN (Not a Number):
```js
"Hello" - "Dolly"    // возвращает NaN

```