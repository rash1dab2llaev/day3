# Java Script Lecture 2

# WHAT IS SCOBE 
Область видимости определяет доступность (видимость) переменных.
JavaScript имеет 3 типа области видимости:
Область блока
Область функций
Глобальный область

# Область блока
До ES6 (2015) у JavaScript были только Global Scope и Function Scope .
ES6 представил два важных новых ключевых слова JavaScript: letи const.
Эти два ключевых слова обеспечивают область действия блока в JavaScript.
К переменным, объявленным внутри блока { }, нельзя получить доступ снаружи блока:
{
  let x = 2;
}
// x can NOT be used here
Переменные, объявленные с помощью varключевого слова, НЕ могут иметь область действия блока.
К переменным, объявленным внутри блока { }, можно получить доступ снаружи блока.
{
  var x = 2;
}
// x CAN be used here


# Область видимости Функции
В JavaScript есть область видимости функции: каждая функция создает новую область видимости.
Переменные, определенные внутри функции, недоступны (видимы) снаружи функции.
Переменные, объявленные с помощью var, let и constочень похожи при объявлении внутри функции.\
Все они имеют область действия :
function myFunction() {
  var carName = "Volvo";   // Function Scope
}
function myFunction() {
  let carName = "Volvo";   // Function Scope
}
function myFunction() {
  const carName = "Volvo";   // Function Scope
}

# Гломальный область видимости
Переменная, объявленная вне функции, становится GLOBAL .

let carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}

Глобальная переменная имеет глобальную область видимости :
Все сценарии и функции на веб-странице могут получить к ней доступ. 

# Автоматически глобальный
Если вы присвоите значение переменной, которая не была объявлена, она автоматически станет ГЛОБАЛЬНОЙ переменной.
В этом примере кода будет объявлена ​​глобальная переменная carName, даже если значение присваивается внутри функции.
myFunction();
// code here can use carName
function myFunction() {
  carName = "Volvo";
}


# HOSTING
Поднятие или hoisting — это механизм в JavaScript, в котором переменные и объявления функций, передвигаются вверх своей области видимости перед тем, как код будет выполнен.

# var

Областью видимости переменной, объявленной через var, является её настоящий контекст выполнения. Это подходит как и для замыкания функции, так и для переменных объявленных вне любой функции, то есть глобальных. Давайте посмотрим на несколько примеров, чтобы понять, что это означает.
# console.log(hoist); // Вывод: undefined
# var hoist = 'The variable has been hoisted.';

# let
Перед тем как идти дальше, стоит отметить то, что переменные объявленные через let заключены в область видимости блока, а не функции.
Вкратце, это просто говорит о том, что область видимости переменной привязана к блоку, в котором она объявлена, а не к функции в которой она объявлена.
# console.log(hoist); // Вывод: ReferenceError: hoist is not defined ...
# let hoist = 'The variable has been hoisted.';

# const

const была представлена в es6 для того, чтобы можно было сделать неизменные переменные. Да, именно это, переменные значение которых не может быть изменено или переназначено.
С const, как и с let, переменные поднимаются вверх блока кода.


# HOSTING function decloration
hoisted(); // Output: "This function has been hoisted."
function hoisted() {
  console.log('This function has been hoisted.');
};

# HOSTING function expretion
expression(); //Output: "TypeError: expression is not a function
var expression = function() {
  console.log('Will this work?');
};


# RECURSION
Частный случай подвызова – когда функция вызывает сама себя. Это как раз и называется рекурсией.
# Рассмотрим два способа её реализации.
1. Итеративный способ: цикл for:
function pow(x, n) {
  let result = 1;

  // умножаем result на x n раз в цикле
  for (let i = 0; i < n; i++) {
    result *= x;
  }

  return result;
}

alert( pow(2, 3) ); // 8
2. Рекурсивный способ: упрощение задачи и вызов функцией самой себя:
function pow(x, n) {
  if (n == 1) {
    return x;
  } else {
    return x * pow(x, n - 1);
  }
}

alert( pow(2, 3) ); // 8



# ЗАМЫКАНИЕ
амыкание — это комбинация функции и лексического окружения, в котором эта функция была определена. Другими словами, замыкание даёт вам доступ к Scope (en-US) внешней функции из внутренней функции. В JavaScript замыкания создаются каждый раз при создании функции, во время её создания.

function init() {
    var name = "Mozilla"; // name - локальная переменная, созданная в init
    function displayName() { // displayName() - внутренняя функция, замыкание
        alert (name); // displayName() использует переменную, объявленную в родительской функции
    }
    displayName();
}
init();