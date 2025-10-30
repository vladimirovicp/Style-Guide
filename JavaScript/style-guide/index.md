# JavaScript Standard Style


## Правила

* **Используйте 2 пробела** для отступа.

  eslint: [`indent`](http://eslint.org/docs/rules/indent)

  ```js
  function hello (name) {
    console.log('hi', name)
  }
  ```

* **Используйте одинарные кавычки для строк**за исключением случаев, когда нужно экранировать символы.

  eslint: [`quotes`](http://eslint.org/docs/rules/quotes)

  ```js
  console.log('hello there')    // ✓ ok
  console.log("hello there")    // ✗ avoid
  console.log(`hello there`)    // ✗ avoid

  $("<div class='box'>")        // ✓ ok
  console.log(`hello ${name}`)  // ✓ ok
  ```

* **Никаких неиспользуемых переменных.**

  eslint: [`no-unused-vars`](http://eslint.org/docs/rules/no-unused-vars)

  ```js
  function myFunction () {
    var result = something()   // ✗ avoid
  }
  ```

* **Добавьте пробел после ключевых слов.**

  eslint: [`keyword-spacing`](http://eslint.org/docs/rules/keyword-spacing)

  ```js
  if (condition) { ... }   // ✓ ok
  if(condition) { ... }    // ✗ avoid
  ```

* **Добавьте пробел перед скобками в объявлении функции.**

  eslint: [`space-before-function-paren`](http://eslint.org/docs/rules/space-before-function-paren)

  ```js
  function name (arg) { ... }   // ✓ ok
  function name(arg) { ... }    // ✗ avoid

  run(function () { ... })      // ✓ ok
  run(function() { ... })       // ✗ avoid
  ```

* **Всегда используйте** `===` вместо `==`.<br>
  Исключение: `obj == null` можно использовать для проверки `null || undefined`.

  eslint: [`eqeqeq`](http://eslint.org/docs/rules/eqeqeq)

  ```js
  if (name === 'John')   // ✓ ok
  if (name == 'John')    // ✗ avoid
  ```

  ```js
  if (name !== 'John')   // ✓ ok
  if (name != 'John')    // ✗ avoid
  ```

* **Инфиксные операторы** олжны быть разделены пробелами.

  eslint: [`space-infix-ops`](http://eslint.org/docs/rules/space-infix-ops)

  ```js
  // ✓ ok
  var x = 2
  var message = 'hello, ' + name + '!'
  ```

  ```js
  // ✗ avoid
  var x=2
  var message = 'hello, '+name+'!'
  ```

* **После запятых должен быть пробел**.

  eslint: [`comma-spacing`](http://eslint.org/docs/rules/comma-spacing)

  ```js
  // ✓ ok
  var list = [1, 2, 3, 4]
  function greet (name, options) { ... }
  ```

  ```js
  // ✗ avoid
  var list = [1,2,3,4]
  function greet (name,options) { ... }
  ```

* **Указывайте операторы else** в той же строке, что и их фигурные скобки.

  eslint: [`brace-style`](http://eslint.org/docs/rules/brace-style)

  ```js
  // ✓ ok
  if (condition) {
    // ...
  } else {
    // ...
  }
  ```

  ```js
  // ✗ avoid
  if (condition) {
    // ...
  }
  else {
    // ...
  }
  ```

* **Для многострочных операторов if** используйте фигурные скобки..

  eslint: [`curly`](http://eslint.org/docs/rules/curly)

  ```js
  // ✓ ok
  if (options.quiet !== true) console.log('done')
  ```

  ```js
  // ✓ ok
  if (options.quiet !== true) {
    console.log('done')
  }
  ```

  ```js
  // ✗ avoid
  if (options.quiet !== true)
    console.log('done')
  ```

* **Всегда обрабатывайте** `err` параметр функции.

  eslint: [`handle-callback-err`](http://eslint.org/docs/rules/handle-callback-err)
  ```js
  // ✓ ok
  run(function (err) {
    if (err) throw err
    window.alert('done')
  })
  ```

  ```js
  // ✗ avoid
  run(function (err) {
    window.alert('done')
  })
  ```

* **Объявите глобальные переменные браузера** с помощью `/* global */` комментария.<br>
  Исключения: `window`, `document`, и `navigator`.<br>
  Предотвращает случайное использование глобальных переменных браузера с неудачными именами, таких как `open`, `length`,
  `event`, и `name`.

  ```js
  /* global alert, prompt */

  alert('hi')
  prompt('ok?')
  ```

  Явное указание на функцию или свойство в `window` тоже допустимо, хотя такой код не 
  будет работать в Worker, где используется `self` вместо `window`.

  eslint: [`no-undef`](http://eslint.org/docs/rules/no-undef)

  ```js
  window.alert('hi')   // ✓ ok
  ```

* **Несколько пустых строк не допускаются.**

  eslint: [`no-multiple-empty-lines`](http://eslint.org/docs/rules/no-multiple-empty-lines)

  ```js
  // ✓ ok
  var value = 'hello world'
  console.log(value)
  ```

  ```js
  // ✗ avoid
  var value = 'hello world'
  // blank line
  // blank line
  console.log(value)
  ```

* **Для тернарного оператора** в многострочном формате разместите `?` и `:` на отдельных строках.

  eslint: [`operator-linebreak`](http://eslint.org/docs/rules/operator-linebreak)

  ```js
  // ✓ ok
  var location = env.development ? 'localhost' : 'www.api.com'

  // ✓ ok
  var location = env.development
    ? 'localhost'
    : 'www.api.com'

  // ✗ avoid
  var location = env.development ?
    'localhost' :
    'www.api.com'
  ```

* **Для объявлений переменных** запишите каждое объявление в отдельной строке.

  eslint: [`one-var`](http://eslint.org/docs/rules/one-var)

  ```js
  // ✓ ok
  var silent = true
  var verbose = true

  // ✗ avoid
  var silent = true, verbose = true

  // ✗ avoid
  var silent = true,
      verbose = true
  ```

* **Заключите условные присваивания** в дополнительные скобки. Так будет понятно, что выражение намеренно является присваиванием (`=`), а не опечаткой в сравнении (`===`).

  eslint: [`no-cond-assign`](http://eslint.org/docs/rules/no-cond-assign)

  ```js
  // ✓ ok
  while ((m = text.match(expr))) {
    // ...
  }

  // ✗ avoid
  while (m = text.match(expr)) {
    // ...
  }
  ```

* **Добавляйте пробелы внутри однострочных блоков.**

  eslint: [`block-spacing`](http://eslint.org/docs/rules/block-spacing)

  ```js
    function foo () {return true}    // ✗ avoid
    function foo () { return true }  // ✓ ok
  ```

* **При именовании переменных и функций используйте стиль camelcase.**

  eslint: [`camelcase`](http://eslint.org/docs/rules/camelcase)

  ```js
    function my_function () { }    // ✗ avoid
    function myFunction () { }     // ✓ ok

    var my_var = 'hello'           // ✗ avoid
    var myVar = 'hello'            // ✓ ok
  ```

* **Запятые в конце предложения не допускаются.**

  eslint: [`comma-dangle`](http://eslint.org/docs/rules/comma-dangle)

  ```js
    var obj = {
      message: 'hello',   // ✗ avoid
    }
  ```

* **Запятые должны стоять в конце текущей строки.**

  eslint: [`comma-style`](http://eslint.org/docs/rules/comma-style)

  ```js
    var obj = {
      foo: 'foo'
      ,bar: 'bar'   // ✗ avoid
    }

    var obj = {
      foo: 'foo',
      bar: 'bar'   // ✓ ok
    }
  ```

* **Точка должна находиться на одной линии со свойством.**

  eslint: [`dot-location`](http://eslint.org/docs/rules/dot-location)

  ```js
    console.
      log('hello')  // ✗ avoid

    console
      .log('hello') // ✓ ok
  ```

* **Файлы должны заканчиваться переводом строки.**

  eslint: [`eol-last`](http://eslint.org/docs/rules/eol-last)

* **Между идентификаторами функций и их вызовами не должно быть пробелов.**

  eslint: [`func-call-spacing`](http://eslint.org/docs/rules/func-call-spacing)

  ```js
  console.log ('hello') // ✗ avoid
  console.log('hello')  // ✓ ok
  ```

* **Добавьте пробел между двоеточием и значением в парах «ключ-значение»**

  eslint: [`key-spacing`](http://eslint.org/docs/rules/key-spacing)

  ```js
  var obj = { 'key' : 'value' }    // ✗ avoid
  var obj = { 'key' :'value' }     // ✗ avoid
  var obj = { 'key':'value' }      // ✗ avoid
  var obj = { 'key': 'value' }     // ✓ ok
  ```

* **Имена конструкторов должны начинаться с заглавной буквы.**

  eslint: [`new-cap`](http://eslint.org/docs/rules/new-cap)

  ```js
  function animal () {}
  var dog = new animal()    // ✗ avoid

  function Animal () {}
  var dog = new Animal()    // ✓ ok
  ```

* **Конструктор без аргументов должен вызываться с использованием круглых скобок.**

  eslint: [`new-parens`](http://eslint.org/docs/rules/new-parens)

  ```js
  function Animal () {}
  var dog = new Animal    // ✗ avoid
  var dog = new Animal()  // ✓ ok
  ```

* **Если задан сеттер, объект должен содержать геттер.**

  eslint: [`accessor-pairs`](http://eslint.org/docs/rules/accessor-pairs)

  ```js
  var person = {
    set name (value) {    // ✗ avoid
      this._name = value
    }
  }

  var person = {
    set name (value) {
      this._name = value
    },
    get name () {         // ✓ ok
      return this._name
    }
  }
  ```

* **Конструкторы производных классов должны вызывать `super`.**

  eslint: [`constructor-super`](http://eslint.org/docs/rules/constructor-super)

  ```js
  class Dog {
    constructor () {
      super()             // ✗ avoid
      this.legs = 4
    }
  }

  class Dog extends Animal {
    constructor () {      // ✗ avoid
      this.legs = 4
    }
  }

  class Dog extends Animal {
    constructor () {
      super()             // ✓ ok
      this.legs = 4
    }
  }
  ```

* **Используйте литералы массивов вместо конструкторов массивов.**

  eslint: [`no-array-constructor`](http://eslint.org/docs/rules/no-array-constructor)

  ```js
  var nums = new Array(1, 2, 3)   // ✗ avoid
  var nums = [1, 2, 3]            // ✓ ok
  ```

* **Не используйте `arguments.callee` и `arguments.caller`.**

  eslint: [`no-caller`](http://eslint.org/docs/rules/no-caller)

  ```js
  function foo (n) {
    if (n <= 0) return

    arguments.callee(n - 1)   // ✗ avoid
  }

  function foo (n) {
    if (n <= 0) return

    foo(n - 1)                // ✓ ok
  }
  ```

* **Не изменяйте переменные в объявлениях классов.**

  eslint: [`no-class-assign`](http://eslint.org/docs/rules/no-class-assign)

  ```js
  class Dog {}
  Dog = 'Fido'    // ✗ avoid
  ```

* **Не изменяйте переменные, объявленные с помощью `const`.**

  eslint: [`no-const-assign`](http://eslint.org/docs/rules/no-const-assign)

  ```js
  const score = 100
  score = 125       // ✗ avoid
  ```

* **Избегайте использования константных выражений в условиях (кроме циклов).**

  eslint: [`no-constant-condition`](http://eslint.org/docs/rules/no-constant-condition)

  ```js
  if (false) {    // ✗ avoid
    // ...
  }

  if (x === 0) {  // ✓ ok
    // ...
  }

  while (true) {  // ✓ ok
    // ...
  }
  ```

* **В регулярных выражениях нет управляющих символов.**

  eslint: [`no-control-regex`](http://eslint.org/docs/rules/no-control-regex)

  ```js
  var pattern = /\x1f/    // ✗ avoid
  var pattern = /\x20/    // ✓ ok
  ```

* **Никаких `debugger` заявлений.**

  eslint: [`no-debugger`](http://eslint.org/docs/rules/no-debugger)

  ```js
  function sum (a, b) {
    debugger      // ✗ avoid
    return a + b
  }
  ```

* **Оператор `delete` для переменных не используется.**

  eslint: [`no-delete-var`](http://eslint.org/docs/rules/no-delete-var)

  ```js
  var name
  delete name     // ✗ avoid
  ```

* **В определениях функций не должно быть повторяющихся аргументов.**

  eslint: [`no-dupe-args`](http://eslint.org/docs/rules/no-dupe-args)

  ```js
  function sum (a, b, a) {  // ✗ avoid
    // ...
  }

  function sum (a, b, c) {  // ✓ ok
    // ...
  }
  ```

* **В членах класса не должно быть повторяющихся имён.**

  eslint: [`no-dupe-class-members`](http://eslint.org/docs/rules/no-dupe-class-members)

  ```js
  class Dog {
    bark () {}
    bark () {}    // ✗ avoid
  }
  ```

* **В объектных литералах не должно быть повторяющихся ключей.**

  eslint: [`no-dupe-keys`](http://eslint.org/docs/rules/no-dupe-keys)

  ```js
  var user = {
    name: 'Jane Doe',
    name: 'John Doe'    // ✗ avoid
  }
  ```

* **В операторах `case` не должно быть повторяющихся меток `switch`.**

  eslint: [`no-duplicate-case`](http://eslint.org/docs/rules/no-duplicate-case)

  ```js
  switch (id) {
    case 1:
      // ...
    case 1:     // ✗ avoid
  }
  ```

* **Используйте один оператор импорта на модуль.**

  eslint: [`no-duplicate-imports`](http://eslint.org/docs/rules/no-duplicate-imports)

  ```js
  import { myFunc1 } from 'module'
  import { myFunc2 } from 'module'          // ✗ avoid

  import { myFunc1, myFunc2 } from 'module' // ✓ ok
  ```

* **Запрещены пустые символьные классы в регулярных выражениях.**

  eslint: [`no-empty-character-class`](http://eslint.org/docs/rules/no-empty-character-class)

  ```js
  const myRegex = /^abc[]/      // ✗ avoid
  const myRegex = /^abc[a-z]/   // ✓ ok
  ```

* **Запрещены пустые шаблоны деструктуризации.**

  eslint: [`no-empty-pattern`](http://eslint.org/docs/rules/no-empty-pattern)

  ```js
  const { a: {} } = foo         // ✗ avoid
  const { a: { b } } = foo      // ✓ ok
  ```

* **Запрещено использование `eval()`.**

  eslint: [`no-eval`](http://eslint.org/docs/rules/no-eval)

  ```js
  eval( "var result = user." + propName ) // ✗ avoid
  var result = user[propName]             // ✓ ok
  ```

* **Запрещено повторное присваивание исключений в блоках `catch`.**

  eslint: [`no-ex-assign`](http://eslint.org/docs/rules/no-ex-assign)

  ```js
  try {
    // ...
  } catch (e) {
    e = 'new value'             // ✗ avoid
  }

  try {
    // ...
  } catch (e) {
    const newVal = 'new value'  // ✓ ok
  }
  ```

* **Никаких расширяемых собственных объектов.**

  eslint: [`no-extend-native`](http://eslint.org/docs/rules/no-extend-native)

  ```js
  Object.prototype.age = 21     // ✗ avoid
  ```

* **Избегайте ненужной привязки функций.**

  eslint: [`no-extra-bind`](http://eslint.org/docs/rules/no-extra-bind)

  ```js
  const name = function () {
    getName()
  }.bind(user)    // ✗ avoid

  const name = function () {
    this.getName()
  }.bind(user)    // ✓ ok
  ```

* **Избегайте избыточных приведений к логическому типу.**

  eslint: [`no-extra-boolean-cast`](http://eslint.org/docs/rules/no-extra-boolean-cast)

  ```js
  const result = true
  if (!!result) {   // ✗ avoid
    // ...
  }

  const result = true
  if (result) {     // ✓ ok
    // ...
  }
  ```

* **Не используйте лишние круглые скобки вокруг функциональных выражений.**

  eslint: [`no-extra-parens`](http://eslint.org/docs/rules/no-extra-parens)

  ```js
  const myFunc = (function () { })   // ✗ avoid
  const myFunc = function () { }     // ✓ ok
  ```

* **Используйте `break` чтобы избежать «проваливания» (fallthrough) в `switch`.**

  eslint: [`no-fallthrough`](http://eslint.org/docs/rules/no-fallthrough)

  ```js
  switch (filter) {
    case 1:
      doSomething()    // ✗ avoid
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      break           // ✓ ok
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      // fallthrough  // ✓ ok
    case 2:
      doSomethingElse()
  }
  ```

* **Не используйте числа с плавающей точкой без нуля перед точкой.**

  eslint: [`no-floating-decimal`](http://eslint.org/docs/rules/no-floating-decimal)

  ```js
  const discount = .5      // ✗ avoid
  const discount = 0.5     // ✓ ok
  ```

* **Избегайте повторного присваивания функциональным объявлениям.**

  eslint: [`no-func-assign`](http://eslint.org/docs/rules/no-func-assign)

  ```js
  function myFunc () { }
  myFunc = myOtherFunc    // ✗ avoid
  ```

* **Не переназначайте глобальные переменные, доступные только для чтения.**

  eslint: [`no-global-assign`](http://eslint.org/docs/rules/no-global-assign)

  ```js
  window = {}     // ✗ avoid
  ```

* **Не используйте неявный вызов `eval()`.**

  eslint: [`no-implied-eval`](http://eslint.org/docs/rules/no-implied-eval)

  ```js
  setTimeout("alert('Hello world')")                   // ✗ avoid
  setTimeout(function () { alert('Hello world') })     // ✓ ok
  ```

* **Не объявляйте функции внутри вложенных блоков.**

  eslint: [`no-inner-declarations`](http://eslint.org/docs/rules/no-inner-declarations)

  ```js
  if (authenticated) {
    function setAuthUser () {}    // ✗ avoid
  }
  ```

* **Не используйте недопустимые строки регулярных выражений в конструкторе  `RegExp`.**

  eslint: [`no-invalid-regexp`](http://eslint.org/docs/rules/no-invalid-regexp)

  ```js
  RegExp('[a-z')    // ✗ avoid
  RegExp('[a-z]')   // ✓ ok
  ```

* **Не используйте нестандартные («нерегулярные») пробельные символы.**

  eslint: [`no-irregular-whitespace`](http://eslint.org/docs/rules/no-irregular-whitespace)

  ```js
  function myFunc () /*<NBSP>*/{}   // ✗ avoid
  ```

* **Не используйте `__iterator__`.**

  eslint: [`no-iterator`](http://eslint.org/docs/rules/no-iterator)

  ```js
  Foo.prototype.__iterator__ = function () {}   // ✗ avoid
  ```

* **Метки (label) не должны совпадать по имени с переменными в текущей области видимости.**

  eslint: [`no-label-var`](http://eslint.org/docs/rules/no-label-var)

  ```js
  var score = 100
  function game () {
    score: while (true) {      // ✗ avoid
      score -= 10
      if (score > 0) continue score
      break
    }
  }
  ```

* **Не используйте метки (label).**

  eslint: [`no-labels`](http://eslint.org/docs/rules/no-labels)

  ```js
  label:
    while (true) {
      break label     // ✗ avoid
    }
  ```

* **Не используйте ненужные вложенные блоки.**

  eslint: [`no-lone-blocks`](http://eslint.org/docs/rules/no-lone-blocks)

  ```js
  function myFunc () {
    {                   // ✗ avoid
      myOtherFunc()
    }
  }

  function myFunc () {
    myOtherFunc()       // ✓ ok
  }
  ```

* **Избегайте смешивания пробелов и табуляции для отступов.**

  eslint: [`no-mixed-spaces-and-tabs`](http://eslint.org/docs/rules/no-mixed-spaces-and-tabs)

* **Не используйте несколько пробелов подряд, за исключением отступов.**

  eslint: [`no-multi-spaces`](http://eslint.org/docs/rules/no-multi-spaces)

  ```js
  const id =    1234    // ✗ avoid
  const id = 1234       // ✓ ok
  ```

* **Не используйте многострочные строки.**

  eslint: [`no-multi-str`](http://eslint.org/docs/rules/no-multi-str)

  ```js
  const message = 'Hello \
                   world'     // ✗ avoid
  ```

* **Не используйте `new` если не присваиваете созданный объект переменной.**

  eslint: [`no-new`](http://eslint.org/docs/rules/no-new)

  ```js
  new Character()                     // ✗ avoid
  const character = new Character()   // ✓ ok
  ```

* **Не используйте конструктор `Function`.**

  eslint: [`no-new-func`](http://eslint.org/docs/rules/no-new-func)

  ```js
  var sum = new Function('a', 'b', 'return a + b')    // ✗ avoid
  ```

* **Не используйте конструктор `Object`.**

  eslint: [`no-new-object`](http://eslint.org/docs/rules/no-new-object)

  ```js
  let config = new Object()   // ✗ avoid
  ```

* **Не используйте `new require`.**

  eslint: [`no-new-require`](http://eslint.org/docs/rules/no-new-require)

  ```js
  const myModule = new require('my-module')    // ✗ avoid
  ```

* **Не используйте конструктор `Symbol`.**

  eslint: [`no-new-symbol`](http://eslint.org/docs/rules/no-new-symbol)

  ```js
  const foo = new Symbol('foo')   // ✗ avoid
  ```

* **Не используйте экземпляры обёрток примитивных типов.**

  eslint: [`no-new-wrappers`](http://eslint.org/docs/rules/no-new-wrappers)

  ```js
  const message = new String('hello')   // ✗ avoid
  ```

* **Не вызывайте свойства глобальных объектов как функции.**

  eslint: [`no-obj-calls`](http://eslint.org/docs/rules/no-obj-calls)

  ```js
  const math = Math()   // ✗ avoid
  ```

* **Не используйте восьмеричные литералы.**

  eslint: [`no-octal`](http://eslint.org/docs/rules/no-octal)

  ```js
  const octal = 042         // ✗ avoid
  const decimal = 34        // ✓ ok
  const octalString = '042' // ✓ ok
  ```

* **Не используйте восьмеричные escape-последовательности в строковых литералах.**

  eslint: [`no-octal-escape`](http://eslint.org/docs/rules/no-octal-escape)

  ```js
  const copyright = 'Copyright \251'  // ✗ avoid
  ```

* **Избегайте конкатенации строк при работе с `__dirname` и `__filename`.**

  eslint: [`no-path-concat`](http://eslint.org/docs/rules/no-path-concat)

  ```js
  const pathToFile = __dirname + '/app.js'            // ✗ avoid
  const pathToFile = path.join(__dirname, 'app.js')   // ✓ ok
  ```

* **Избегайте использования `__proto__`.** Используйте вместо этого `getPrototypeOf`.

  eslint: [`no-proto`](http://eslint.org/docs/rules/no-proto)

  ```js
  const foo = obj.__proto__               // ✗ avoid
  const foo = Object.getPrototypeOf(obj)  // ✓ ok
  ```

* **Не переобъявляйте переменные.**

  eslint: [`no-redeclare`](http://eslint.org/docs/rules/no-redeclare)

  ```js
  let name = 'John'
  let name = 'Jane'     // ✗ avoid

  let name = 'John'
  name = 'Jane'         // ✓ ok
  ```

* **Избегайте нескольких пробелов подряд в литералах регулярных выражений.**

  eslint: [`no-regex-spaces`](http://eslint.org/docs/rules/no-regex-spaces)

  ```js
  const regexp = /test   value/   // ✗ avoid

  const regexp = /test {3}value/  // ✓ ok
  const regexp = /test value/     // ✓ ok
  ```

* **Присваивания в операторах return должны быть заключены в скобки.**

  eslint: [`no-return-assign`](http://eslint.org/docs/rules/no-return-assign)

  ```js
  function sum (a, b) {
    return result = a + b     // ✗ avoid
  }

  function sum (a, b) {
    return (result = a + b)   // ✓ ok
  }
  ```

* **Избегайте присваивания переменной самого себя**

  eslint: [`no-self-assign`](http://eslint.org/docs/rules/no-self-assign)

  ```js
  name = name   // ✗ avoid
  ```

* **Избегайте сравнения переменной с самой собой.**

  eslint: [`no-self-compare`](http://eslint.org/docs/rules/no-self-compare)

  ```js
  if (score === score) {}   // ✗ avoid
  ```

* **Избегайте использования оператора запятой.**

  eslint: [`no-sequences`](http://eslint.org/docs/rules/no-sequences)

  ```js
  if (doSomething(), !!test) {}   // ✗ avoid
  ```

* **Зарезервированные имена не должны быть затенены.**

  eslint: [`no-shadow-restricted-names`](http://eslint.org/docs/rules/no-shadow-restricted-names)

  ```js
  let undefined = 'value'     // ✗ avoid
  ```

* **Разреженные массивы (с «дырами») запрещены.**

  eslint: [`no-sparse-arrays`](http://eslint.org/docs/rules/no-sparse-arrays)

  ```js
  let fruits = ['apple',, 'orange']       // ✗ avoid
  ```

* **Не используйте символы табуляции**

  eslint: [`no-tabs`](http://eslint.org/docs/rules/no-tabs)

* **Обычные строки не должны содержать шаблонные литералы (${}).**

  eslint: [`no-template-curly-in-string`](http://eslint.org/docs/rules/no-template-curly-in-string)

  ```js
  const message = 'Hello ${name}'   // ✗ avoid
  const message = `Hello ${name}`   // ✓ ok
  ```

* **`super()` должен быть вызван до использования `this`.**

  eslint: [`no-this-before-super`](http://eslint.org/docs/rules/no-this-before-super)

  ```js
  class Dog extends Animal {
    constructor () {
      this.legs = 4     // ✗ avoid
      super()
    }
  }
  ```

* **Используйте `throw` только с объектами `Error`.**

  eslint: [`no-throw-literal`](http://eslint.org/docs/rules/no-throw-literal)

  ```js
  throw 'error'               // ✗ avoid
  throw new Error('error')    // ✓ ok
  ```

* **Пробелы в конце строк недопустимы.**

  eslint: [`no-trailing-spaces`](http://eslint.org/docs/rules/no-trailing-spaces)

* **Инициализация переменных значением `undefined` запрещена.**

  eslint: [`no-undef-init`](http://eslint.org/docs/rules/no-undef-init)

  ```js
  let name = undefined    // ✗ avoid

  let name
  name = 'value'          // ✓ ok
  ```

* **Условия циклов не должны оставаться неизменными.**

  eslint: [`no-unmodified-loop-condition`](http://eslint.org/docs/rules/no-unmodified-loop-condition)

  ```js
  for (let i = 0; i < items.length; j++) {...}    // ✗ avoid
  for (let i = 0; i < items.length; i++) {...}    // ✓ ok
  ```

* **Не используйте тернарные операторы, если есть более простая альтернатива.**

  eslint: [`no-unneeded-ternary`](http://eslint.org/docs/rules/no-unneeded-ternary)

  ```js
  let score = val ? val : 0     // ✗ avoid
  let score = val || 0          // ✓ ok
  ```

* **Недостижимый код после операторов `return`, `throw`, `continue`, и `break` statements.**

  eslint: [`no-unreachable`](http://eslint.org/docs/rules/no-unreachable)

  ```js
  function doSomething () {
    return true
    console.log('never called')     // ✗ avoid
  }
  ```

* **Операторы управления потоком (return, throw, break, continue) запрещены в блоках `finally`.**

  eslint: [`no-unsafe-finally`](http://eslint.org/docs/rules/no-unsafe-finally)

  ```js
  try {
    // ...
  } catch (e) {
    // ...
  } finally {
    return 42     // ✗ avoid
  }
  ```

* **Левый операнд реляционных операторов не должен быть отрицанием.**

  eslint: [`no-unsafe-negation`](http://eslint.org/docs/rules/no-unsafe-negation)

  ```js
  if (!key in obj) {}       // ✗ avoid
  if (!(key in obj)) {}     // ✓ ok
  ```

* **Избегайте ненужного использования `.call()` и `.apply()`.**

  eslint: [`no-useless-call`](http://eslint.org/docs/rules/no-useless-call)

  ```js
  sum.call(null, 1, 2, 3)   // ✗ avoid
  ```

* **Избегайте ненужного использования вычисляемых ключей в объектах.**

  eslint: [`no-useless-computed-key`](http://eslint.org/docs/rules/no-useless-computed-key)

  ```js
  const user = { ['name']: 'John Doe' }   // ✗ avoid
  const user = { name: 'John Doe' }       // ✓ ok
  ```

* **Не используйте бесполезные конструкторы.**

  eslint: [`no-useless-constructor`](http://eslint.org/docs/rules/no-useless-constructor)

  ```js
  class Car {
    constructor () {      // ✗ avoid
    }
  }
  ```

* **Не используйте избыточные escape-последовательности.**

  eslint: [`no-useless-escape`](http://eslint.org/docs/rules/no-useless-escape)

  ```js
  let message = 'Hell\o'  // ✗ avoid
  ```

* **Переименование импортов, экспортов и деструктуризаций в то же самое имя запрещено.**

  eslint: [`no-useless-rename`](http://eslint.org/docs/rules/no-useless-rename)

  ```js
  import { config as config } from './config'     // ✗ avoid
  import { config } from './config'               // ✓ ok
  ```

* **Не ставьте пробелы перед свойствами объектов.**

  eslint: [`no-whitespace-before-property`](http://eslint.org/docs/rules/no-whitespace-before-property)

  ```js
  user .name      // ✗ avoid
  user.name       // ✓ ok
  ```

* **Не используйте оператор `with`.**

  eslint: [`no-with`](http://eslint.org/docs/rules/no-with)

  ```js
  with (val) {...}    // ✗ avoid
  ```

* **Соблюдайте согласованность переносов строк между свойствами объектов.**

  eslint: [`object-property-newline`](http://eslint.org/docs/rules/object-property-newline)

  ```js
  const user = {
    name: 'Jane Doe', age: 30,
    username: 'jdoe86'            // ✗ avoid
  }

  const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' }    // ✓ ok

  const user = {
    name: 'Jane Doe',
    age: 30,
    username: 'jdoe86'
  }                                                                 // ✓ ok
  ```

* **Не добавляйте пустые строки в начале и конце блоков кода.**

  eslint: [`padded-blocks`](http://eslint.org/docs/rules/padded-blocks)

  ```js
  if (user) {
                              // ✗ avoid
    const name = getName()

  }

  if (user) {
    const name = getName()    // ✓ ok
  }
  ```

* **Не ставьте пробел между оператором расширения (...) и выражением.**

  eslint: [`rest-spread-spacing`](http://eslint.org/docs/rules/rest-spread-spacing)

  ```js
  fn(... args)    // ✗ avoid
  fn(...args)     // ✓ ok
  ```

* **После точки с запятой должен быть пробел, а перед ней — нет.**

  eslint: [`semi-spacing`](http://eslint.org/docs/rules/semi-spacing)

  ```js
  for (let i = 0 ;i < items.length ;i++) {...}    // ✗ avoid
  for (let i = 0; i < items.length; i++) {...}    // ✓ ok
  ```

* **Перед открывающей фигурной скобкой блока должен быть пробел.**

  eslint: [`space-before-blocks`](http://eslint.org/docs/rules/space-before-blocks)

  ```js
  if (admin){...}     // ✗ avoid
  if (admin) {...}    // ✓ ok
  ```

* **Не ставьте пробелы внутри круглых скобок.**

  eslint: [`space-in-parens`](http://eslint.org/docs/rules/space-in-parens)

  ```js
  getName( name )     // ✗ avoid
  getName(name)       // ✓ ok
  ```

* **После унарных операторов должен быть пробел.**

  eslint: [`space-unary-ops`](http://eslint.org/docs/rules/space-unary-ops)

  ```js
  typeof!admin        // ✗ avoid
  typeof !admin        // ✓ ok
  ```

* **Используйте пробелы внутри комментариев.**

  eslint: [`spaced-comment`](http://eslint.org/docs/rules/spaced-comment)

  ```js
  //comment           // ✗ avoid
  // comment          // ✓ ok

  /*comment*/         // ✗ avoid
  /* comment */       // ✓ ok
  ```

* **Не ставьте пробелы внутри шаблонных литералов (${}).**

  eslint: [`template-curly-spacing`](http://eslint.org/docs/rules/template-curly-spacing)

  ```js
  const message = `Hello, ${ name }`    // ✗ avoid
  const message = `Hello, ${name}`      // ✓ ok
  ```

* **Используйте `isNaN()` для проверки на `NaN`.**

  eslint: [`use-isnan`](http://eslint.org/docs/rules/use-isnan)

  ```js
  if (price === NaN) { }      // ✗ avoid
  if (isNaN(price)) { }       // ✓ ok
  ```

* **Результат `typeof` должен сравниваться только с корректными строками.**

  eslint: [`valid-typeof`](http://eslint.org/docs/rules/valid-typeof)

  ```js
  typeof name === 'undefimed'     // ✗ avoid
  typeof name === 'undefined'     // ✓ ok
  ```

* **Немедленно вызываемые функциональные выражения (IIFEs) должны быть обёрнуты в скобки.**

  eslint: [`wrap-iife`](http://eslint.org/docs/rules/wrap-iife)

  ```js
  const getName = function () { }()     // ✗ avoid

  const getName = (function () { }())   // ✓ ok
  const getName = (function () { })()   // ✓ ok
  ```

* **В выражениях `yield*` звёздочка `*` должна быть окружена пробелами с обеих сторон.**

  eslint: [`yield-star-spacing`](http://eslint.org/docs/rules/yield-star-spacing)

  ```js
  yield* increment()    // ✗ avoid
  yield * increment()   // ✓ ok
  ```

* **Избегайте условий в стиле Йоды (Yoda conditions).**

  eslint: [`yoda`](http://eslint.org/docs/rules/yoda)

  ```js
  if (42 === age) { }    // ✗ avoid
  if (age === 42) { }    // ✓ ok
  ```

## Точка с запятой

* Точки с запятой не используются. (см.: [1](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding), [2](https://web.archive.org/web/20201206065632/http://inimino.org/~inimino/blog/javascript_semicolons), [3](https://www.youtube.com/watch?v=gsfbh17Ax9I))

  eslint: [`semi`](http://eslint.org/docs/rules/semi)

  ```js
  window.alert('hi')   // ✓ ok
  window.alert('hi');  // ✗ avoid
  ```

* Никогда не начинайте строку с `(`, `[`, `` ` ``, или нескольких других маловероятных символов.

  (Полный список: `[`, `(`, `` ` ``, `+`, `*`, `/`, `-`, `,`, `.`, но большинство из них в реальном коде никогда не появятся в начале строки.)

  eslint: [`no-unexpected-multiline`](http://eslint.org/docs/rules/no-unexpected-multiline)

  ```js
  // ✓ ok
  ;(function () {
    window.alert('ok')
  }())

  // ✗ avoid
  (function () {
    window.alert('ok')
  }())
  ```

  ```js
  // ✓ ok
  ;[1, 2, 3].forEach(bar)

  // ✗ avoid
  [1, 2, 3].forEach(bar)
  ```

  ```js
  // ✓ ok
  ;`hello`.indexOf('o')

  // ✗ avoid
  `hello`.indexOf('o')
  ```

  Примечание: если вы часто пишете подобный код, возможно, вы пытаетесь быть слишком «умным».

  Краткие и хитроумные сокращения не рекомендуются — по возможности следует отдавать предпочтение ясным и читаемым выражениям.

  Вместо этого:

  ```js
  ;[1, 2, 3].forEach(bar)
  ```

  Настоятельно рекомендуется писать так:

  ```js
  var nums = [1, 2, 3]
  nums.forEach(bar)
  ```