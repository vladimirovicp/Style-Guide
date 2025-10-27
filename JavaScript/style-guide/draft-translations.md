
* **Избегайте избыточных приведений к логическому типу.**

  eslint: [`no-extra-boolean-cast`](http://eslint.org/docs/rules/no-extra-boolean-cast)

  ```js
  const result = true
  if (!!result) {   // ✗ не рекомендуется
    // ...
  }

  const result = true
  if (result) {     // ✓ допустимо
    // ...
  }
  ```

* **Не используйте лишние круглые скобки вокруг функциональных выражений.**

  eslint: [`no-extra-parens`](http://eslint.org/docs/rules/no-extra-parens)

  ```js
  const myFunc = (function () { })   // ✗ не рекомендуется
  const myFunc = function () { }     // ✓ допустимо
  ```

* **Используйте `break`, чтобы избежать «проваливания» (`fallthrough`) в `switch`-кейсах.**

  eslint: [`no-fallthrough`](http://eslint.org/docs/rules/no-fallthrough)

  ```js
  switch (filter) {
    case 1:
      doSomething()    // ✗ не рекомендуется
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      break           // ✓ допустимо
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      // fallthrough  // ✓ допустимо
    case 2:
      doSomethingElse()
  }
  ```

* **Не используйте числа с плавающей точкой без нуля перед точкой.**

  eslint: [`no-floating-decimal`](http://eslint.org/docs/rules/no-floating-decimal)

  ```js
  const discount = .5      // ✗ не рекомендуется
  const discount = 0.5     // ✓ допустимо
  ```

* **Избегайте повторного присваивания функциональным объявлениям.**

  eslint: [`no-func-assign`](http://eslint.org/docs/rules/no-func-assign)

  ```js
  function myFunc () { }
  myFunc = myOtherFunc    // ✗ не рекомендуется
  ```

* **Не переназначайте глобальные переменные, доступные только для чтения.**

  eslint: [`no-global-assign`](http://eslint.org/docs/rules/no-global-assign)

  ```js
  window = {}     // ✗ не рекомендуется
  ```

* **Не используйте неявный вызов `eval()`.**

  eslint: [`no-implied-eval`](http://eslint.org/docs/rules/no-implied-eval)

  ```js
  setTimeout("alert('Hello world')")                   // ✗ не рекомендуется
  setTimeout(function () { alert('Hello world') })     // ✓ допустимо
  ```

* **Не объявляйте функции внутри вложенных блоков.**

  eslint: [`no-inner-declarations`](http://eslint.org/docs/rules/no-inner-declarations)

  ```js
  if (authenticated) {
    function setAuthUser () {}    // ✗ не рекомендуется
  }
  ```

* **Не используйте недопустимые строки регулярных выражений в конструкторе `RegExp`.**

  eslint: [`no-invalid-regexp`](http://eslint.org/docs/rules/no-invalid-regexp)

  ```js
  RegExp('[a-z')    // ✗ не рекомендуется
  RegExp('[a-z]')   // ✓ допустимо
  ```

* **Не используйте нестандартные («нерегулярные») пробельные символы.**

  eslint: [`no-irregular-whitespace`](http://eslint.org/docs/rules/no-irregular-whitespace)

  ```js
  function myFunc () /*<NBSP>*/{}   // ✗ не рекомендуется
  ```

* **Не используйте `__iterator__`.**

  eslint: [`no-iterator`](http://eslint.org/docs/rules/no-iterator)

  ```js
  Foo.prototype.__iterator__ = function () {}   // ✗ не рекомендуется
  ```

* **Метки (`label`) не должны совпадать по имени с переменными в текущей области видимости.**

  eslint: [`no-label-var`](http://eslint.org/docs/rules/no-label-var)

  ```js
  var score = 100
  function game () {
    score: while (true) {      // ✗ не рекомендуется
      score -= 10
      if (score > 0) continue score
      break
    }
  }
  ```

* **Не используйте метки (`label`).**

  eslint: [`no-labels`](http://eslint.org/docs/rules/no-labels)

  ```js
  label:
    while (true) {
      break label     // ✗ не рекомендуется
    }
  ```

* **Не используйте ненужные вложенные блоки.**

  eslint: [`no-lone-blocks`](http://eslint.org/docs/rules/no-lone-blocks)

  ```js
  function myFunc () {
    {                   // ✗ не рекомендуется
      myOtherFunc()
    }
  }

  function myFunc () {
    myOtherFunc()       // ✓ допустимо
  }
  ```

* **Избегайте смешивания пробелов и табуляции для отступов.**

  eslint: [`no-mixed-spaces-and-tabs`](http://eslint.org/docs/rules/no-mixed-spaces-and-tabs)

* **Не используйте несколько пробелов подряд, за исключением отступов.**

  eslint: [`no-multi-spaces`](http://eslint.org/docs/rules/no-multi-spaces)

  ```js
  const id =    1234    // ✗ не рекомендуется
  const id = 1234       // ✓ допустимо
  ```

* **Не используйте многострочные строки.**

  eslint: [`no-multi-str`](http://eslint.org/docs/rules/no-multi-str)

  ```js
  const message = 'Hello \
                   world'     // ✗ не рекомендуется
  ```

* **Не используйте `new`, если не присваиваете созданный объект переменной.**

  eslint: [`no-new`](http://eslint.org/docs/rules/no-new)

  ```js
  new Character()                     // ✗ не рекомендуется
  const character = new Character()   // ✓ допустимо
  ```

* **Не используйте конструктор `Function`.**

  eslint: [`no-new-func`](http://eslint.org/docs/rules/no-new-func)

  ```js
  var sum = new Function('a', 'b', 'return a + b')    // ✗ не рекомендуется
  ```

* **Не используйте конструктор `Object`.**

  eslint: [`no-new-object`](http://eslint.org/docs/rules/no-new-object)

  ```js
  let config = new Object()   // ✗ не рекомендуется
  ```

* **Не используйте `new require`.**

  eslint: [`no-new-require`](http://eslint.org/docs/rules/no-new-require)

  ```js
  const myModule = new require('my-module')    // ✗ не рекомендуется
  ```

* **Не используйте конструктор `Symbol`.**

  eslint: [`no-new-symbol`](http://eslint.org/docs/rules/no-new-symbol)

  ```js
  const foo = new Symbol('foo')   // ✗ не рекомендуется
  ```

* **Не используйте экземпляры обёрток примитивных типов.**

  eslint: [`no-new-wrappers`](http://eslint.org/docs/rules/no-new-wrappers)

  ```js
  const message = new String('hello')   // ✗ не рекомендуется
  ```

* **Не вызывайте свойства глобальных объектов как функции.**

  eslint: [`no-obj-calls`](http://eslint.org/docs/rules/no-obj-calls)

  ```js
  const math = Math()   // ✗ не рекомендуется
  ```

* **Не используйте восьмеричные литералы.**

  eslint: [`no-octal`](http://eslint.org/docs/rules/no-octal)

  ```js
  const octal = 042         // ✗ не рекомендуется
  const decimal = 34        // ✓ допустимо
  const octalString = '042' // ✓ допустимо
  ```

* **Не используйте восьмеричные escape-последовательности в строковых литералах.**

  eslint: [`no-octal-escape`](http://eslint.org/docs/rules/no-octal-escape)

  ```js
  const copyright = 'Copyright \251'  // ✗ не рекомендуется
  ```

* **Избегайте конкатенации строк при работе с `__dirname` и `__filename`.**

  eslint: [`no-path-concat`](http://eslint.org/docs/rules/no-path-concat)

  ```js
  const pathToFile = __dirname + '/app.js'            // ✗ не рекомендуется
  const pathToFile = path.join(__dirname, 'app.js')   // ✓ допустимо
  ```

* **Избегайте использования `__proto__`.** Используйте вместо этого `getPrototypeOf`.

  eslint: [`no-proto`](http://eslint.org/docs/rules/no-proto)

  ```js
  const foo = obj.__proto__               // ✗ не рекомендуется
  const foo = Object.getPrototypeOf(obj)  // ✓ допустимо
  ```

* **Не переобъявляйте переменные.**

  eslint: [`no-redeclare`](http://eslint.org/docs/rules/no-redeclare)

  ```js
  let name = 'John'
  let name = 'Jane'     // ✗ не рекомендуется

  let name = 'John'
  name = 'Jane'         // ✓ допустимо
  ```

* **Избегайте нескольких пробелов подряд в литералах регулярных выражений.**

  eslint: [`no-regex-spaces`](http://eslint.org/docs/rules/no-regex-spaces)

  ```js
  const regexp = /test   value/   // ✗ не рекомендуется

  const regexp = /test {3}value/  // ✓ допустимо
  const regexp = /test value/     // ✓ допустимо
  ```

* **Присваивания в операторах `return` должны быть заключены в скобки.**

  eslint: [`no-return-assign`](http://eslint.org/docs/rules/no-return-assign)

  ```js
  function sum (a, b) {
    return result = a + b     // ✗ не рекомендуется
  }

  function sum (a, b) {
    return (result = a + b)   // ✓ допустимо
  }
  ```

* **Избегайте присваивания переменной самого себя**

  eslint: [`no-self-assign`](http://eslint.org/docs/rules/no-self-assign)

  ```js
  name = name   // ✗ не рекомендуется
  ```

* **Избегайте сравнения переменной с самой собой.**

  eslint: [`no-self-compare`](http://eslint.org/docs/rules/no-self-compare)

  ```js
  if (score === score) {}   // ✗ не рекомендуется
  ```

* **Избегайте использования оператора запятой.**

  eslint: [`no-sequences`](http://eslint.org/docs/rules/no-sequences)

  ```js
  if (doSomething(), !!test) {}   // ✗ не рекомендуется
  ```

* **Зарезервированные имена не должны быть затенены.**

  eslint: [`no-shadow-restricted-names`](http://eslint.org/docs/rules/no-shadow-restricted-names)

  ```js
  let undefined = 'value'     // ✗ не рекомендуется
  ```

* **Разреженные массивы (с «дырами») запрещены.**

  eslint: [`no-sparse-arrays`](http://eslint.org/docs/rules/no-sparse-arrays)

  ```js
  let fruits = ['apple',, 'orange']       // ✗ не рекомендуется
  ```

* **Не используйте символы табуляции**

  eslint: [`no-tabs`](http://eslint.org/docs/rules/no-tabs)

* **Обычные строки не должны содержать шаблонные литералы (`${}`).**

  eslint: [`no-template-curly-in-string`](http://eslint.org/docs/rules/no-template-curly-in-string)

  ```js
  const message = 'Hello ${name}'   // ✗ не рекомендуется
  const message = `Hello ${name}`   // ✓ допустимо
  ```

* **`super()` должен быть вызван до использования `this`.**

  eslint: [`no-this-before-super`](http://eslint.org/docs/rules/no-this-before-super)

  ```js
  class Dog extends Animal {
    constructor () {
      this.legs = 4     // ✗ не рекомендуется
      super()
    }
  }
  ```

* **Используйте `throw` только с объектами `Error`.**

  eslint: [`no-throw-literal`](http://eslint.org/docs/rules/no-throw-literal)

  ```js
  throw 'error'               // ✗ не рекомендуется
  throw new Error('error')    // ✓ допустимо
  ```

* **Пробелы в конце строк недопустимы.**

  eslint: [`no-trailing-spaces`](http://eslint.org/docs/rules/no-trailing-spaces)

* **Инициализация переменных значением `undefined` запрещена.**

  eslint: [`no-undef-init`](http://eslint.org/docs/rules/no-undef-init)

  ```js
  let name = undefined    // ✗ не рекомендуется

  let name
  name = 'value'          // ✓ допустимо
  ```

* **Условия циклов не должны оставаться неизменными.**

  eslint: [`no-unmodified-loop-condition`](http://eslint.org/docs/rules/no-unmodified-loop-condition)

  ```js
  for (let i = 0; i < items.length; j++) {...}    // ✗ не рекомендуется
  for (let i = 0; i < items.length; i++) {...}    // ✓ допустимо
  ```

* **Не используйте тернарные операторы, если есть более простая альтернатива.**

  eslint: [`no-unneeded-ternary`](http://eslint.org/docs/rules/no-unneeded-ternary)

  ```js
  let score = val ? val : 0     // ✗ не рекомендуется
  let score = val || 0          // ✓ допустимо
  ```

* **Недостижимый код после операторов `return`, `throw`, `continue` и `break` запрещён.**

  eslint: [`no-unreachable`](http://eslint.org/docs/rules/no-unreachable)

  ```js
  function doSomething () {
    return true
    console.log('never called')     // ✗ не рекомендуется
  }
  ```

* **Операторы управления потоком (`return`, `throw`, `break`, `continue`) запрещены в блоках `finally`.**

  eslint: [`no-unsafe-finally`](http://eslint.org/docs/rules/no-unsafe-finally)

  ```js
  try {
    // ...
  } catch (e) {
    // ...
  } finally {
    return 42     // ✗ не рекомендуется
  }
  ```

* **Левый операнд реляционных операторов не должен быть отрицанием.**

  eslint: [`no-unsafe-negation`](http://eslint.org/docs/rules/no-unsafe-negation)

  ```js
  if (!key in obj) {}       // ✗ не рекомендуется
  if (!(key in obj)) {}     // ✓ допустимо
  ```

* **Избегайте ненужного использования `.call()` и `.apply()`.**

  eslint: [`no-useless-call`](http://eslint.org/docs/rules/no-useless-call)

  ```js
  sum.call(null, 1, 2, 3)   // ✗ не рекомендуется
  ```

* **Избегайте ненужного использования вычисляемых ключей в объектах.**

  eslint: [`no-useless-computed-key`](http://eslint.org/docs/rules/no-useless-computed-key)

  ```js
  const user = { ['name']: 'John Doe' }   // ✗ не рекомендуется
  const user = { name: 'John Doe' }       // ✓ допустимо
  ```

* **Не используйте бесполезные конструкторы.**

  eslint: [`no-useless-constructor`](http://eslint.org/docs/rules/no-useless-constructor)

  ```js
  class Car {
    constructor () {      // ✗ не рекомендуется
    }
  }
  ```

* **Не используйте избыточные escape-последовательности.**

  eslint: [`no-useless-escape`](http://eslint.org/docs/rules/no-useless-escape)

  ```js
  let message = 'Hell\o'  // ✗ не рекомендуется
  ```

* **Переименование импортов, экспортов и деструктуризаций в то же самое имя запрещено.**

  eslint: [`no-useless-rename`](http://eslint.org/docs/rules/no-useless-rename)

  ```js
  import { config as config } from './config'     // ✗ не рекомендуется
  import { config } from './config'               // ✓ допустимо
  ```

* **Не ставьте пробелы перед свойствами объектов.**

  eslint: [`no-whitespace-before-property`](http://eslint.org/docs/rules/no-whitespace-before-property)

  ```js
  user .name      // ✗ не рекомендуется
  user.name       // ✓ допустимо
  ```

* **Не используйте оператор `with`.**

  eslint: [`no-with`](http://eslint.org/docs/rules/no-with)

  ```js
  with (val) {...}    // ✗ не рекомендуется
  ```

* **Соблюдайте согласованность переносов строк между свойствами объектов.**

  eslint: [`object-property-newline`](http://eslint.org/docs/rules/object-property-newline)

  ```js
  const user = {
    name: 'Jane Doe', age: 30,
    username: 'jdoe86'            // ✗ не рекомендуется
  }

  const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' }    // ✓ допустимо

  const user = {
    name: 'Jane Doe',
    age: 30,
    username: 'jdoe86'
  }                                                                 // ✓ допустимо
  ```

* **Не добавляйте пустые строки в начале и конце блоков кода.**

  eslint: [`padded-blocks`](http://eslint.org/docs/rules/padded-blocks)

  ```js
  if (user) {
                              // ✗ не рекомендуется
    const name = getName()

  }

  if (user) {
    const name = getName()    // ✓ допустимо
  }
  ```

* **Не ставьте пробел между оператором расширения (`...`) и выражением.**

  eslint: [`rest-spread-spacing`](http://eslint.org/docs/rules/rest-spread-spacing)

  ```js
  fn(... args)    // ✗ не рекомендуется
  fn(...args)     // ✓ допустимо
  ```

* **После точки с запятой должен быть пробел, а перед ней — нет.**

  eslint: [`semi-spacing`](http://eslint.org/docs/rules/semi-spacing)

  ```js
  for (let i = 0 ;i < items.length ;i++) {...}    // ✗ не рекомендуется
  for (let i = 0; i < items.length; i++) {...}    // ✓ допустимо
  ```

* **Перед открывающей фигурной скобкой блока должен быть пробел.**

  eslint: [`space-before-blocks`](http://eslint.org/docs/rules/space-before-blocks)

  ```js
  if (admin){...}     // ✗ не рекомендуется
  if (admin) {...}    // ✓ допустимо
  ```

* **Не ставьте пробелы внутри круглых скобок.**

  eslint: [`space-in-parens`](http://eslint.org/docs/rules/space-in-parens)

  ```js
  getName( name )     // ✗ не рекомендуется
  getName(name)       // ✓ допустимо
  ```

* **После унарных операторов должен быть пробел.**

  eslint: [`space-unary-ops`](http://eslint.org/docs/rules/space-unary-ops)

  ```js
  typeof!admin        // ✗ не рекомендуется
  typeof !admin       // ✓ допустимо
  ```

* **Используйте пробелы внутри комментариев.**

  eslint: [`spaced-comment`](http://eslint.org/docs/rules/spaced-comment)

  ```js
  //comment           // ✗ не рекомендуется
  // comment          // ✓ допустимо

  /*comment*/         // ✗ не рекомендуется
  /* comment */       // ✓ допустимо
  ```

* **Не ставьте пробелы внутри шаблонных литералов (`${}`).**

  eslint: [`template-curly-spacing`](http://eslint.org/docs/rules/template-curly-spacing)

  ```js
  const message = `Hello, ${ name }`    // ✗ не рекомендуется
  const message = `Hello, ${name}`      // ✓ допустимо
  ```

* **Используйте `isNaN()` для проверки на `NaN`.**

  eslint: [`use-isnan`](http://eslint.org/docs/rules/use-isnan)

  ```js
  if (price === NaN) { }      // ✗ не рекомендуется
  if (isNaN(price)) { }       // ✓ допустимо
  ```

* **Результат `typeof` должен сравниваться только с корректными строками.**

  eslint: [`valid-typeof`](http://eslint.org/docs/rules/valid-typeof)

  ```js
  typeof name === 'undefimed'     // ✗ не рекомендуется
  typeof name === 'undefined'     // ✓ допустимо
  ```

* **Немедленно вызываемые функциональные выражения (IIFE) должны быть обёрнуты в скобки.**

  eslint: [`wrap-iife`](http://eslint.org/docs/rules/wrap-iife)

  ```js
  const getName = function () { }()     // ✗ не рекомендуется

  const getName = (function () { }())   // ✓ допустимо
  const getName = (function () { })()   // ✓ допустимо
  ```

* **В выражениях `yield*` звёздочка должна быть окружена пробелами с обеих сторон.**

  eslint: [`yield-star-spacing`](http://eslint.org/docs/rules/yield-star-spacing)

  ```js
  yield* increment()    // ✗ не рекомендуется
  yield * increment()   // ✓ допустимо
  ```

* **Избегайте условий в стиле Йоды (Yoda conditions).**

  eslint: [`yoda`](http://eslint.org/docs/rules/yoda)

  ```js
  if (42 === age) { }    // ✗ не рекомендуется
  if (age === 42) { }    // ✓ допустимо
  ```

## Точка с запятой

* **Точки с запятой не используются.** (см.: [1](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding), [2](https://web.archive.org/web/20201206065632/http://inimino.org/~inimino/blog/javascript_semicolons), [3](https://www.youtube.com/watch?v=gsfbh17Ax9I))

  eslint: [`semi`](http://eslint.org/docs/rules/semi)

  ```js
  window.alert('hi')   // ✓ допустимо
  window.alert('hi');  // ✗ не рекомендуется
  ```

* **Никогда не начинайте строку с `(`, `[`, `` ` ``, или нескольких других маловероятных символов.**

  Это единственная потенциальная проблема при опускании точек с запятой, и `standard` защищает вас от неё.

  (Полный список: `[`, `(`, `` ` ``, `+`, `*`, `/`, `-`, `,`, `.`, но большинство из них в реальном коде никогда не появятся в начале строки.)

  eslint: [`no-unexpected-multiline`](http://eslint.org/docs/rules/no-unexpected-multiline)

  ```js
  // ✓ допустимо
  ;(function () {
    window.alert('ok')
  }())

  // ✗ не рекомендуется
  (function () {
    window.alert('ok')
  }())
  ```

  ```js
  // ✓ допустимо
  ;[1, 2, 3].forEach(bar)

  // ✗ не рекомендуется
  [1, 2, 3].forEach(bar)
  ```

  ```js
  // ✓ допустимо
  ;`hello`.indexOf('o')

  // ✗ не рекомендуется
  `hello`.indexOf('o')
  ```