# code-style

> * 文件名建议只使用**小写字母**，不使用大写字母；单词之间用连接符`-`或者下划线`_`
> * 为了醒目，某些说明文件的文件名，可以使用大写字母，比如`README`、`LICENSE`

主要原因：

* **可移植性**  Linux 系统是**大小写敏感**的，而 Windows 系统和 Mac 系统正好相反，**大小写不敏感**
* **易读性** 小写文件名更易读
* **易用性** 某些系统会生成一些预置的用户目录，采用首字母大写的目录名；某些常见的配置文件或说明文件，也采用大写的文件名，容易区分

**建议文件夹和文件用短线`-`**

**html和css使用双引号`""` js使用单引号`''`**

**建议每行不超过80个字符**

## Repository Name Style

* **特别简易和容易区分**的直接**小写字母**，单词组合或者缩写组合，比如jsdemos，jstutorial
* **小写字母**，单词之间直接用短线`-`连接，比如code-style
* **小写字母**，单词之间直接用下划线`_`连接，比如code_style

**建议仓库名单词小写组合，或者短线`-`**



## 命名规则

### JavaScript 命名规则

1.1 命名应具备描述性

1.2 使用驼峰式命名（小驼峰）对象、函数（方法）名和实例

```javascript
// bad
const OBJEcttsssss = {};
const this_is_my_object = {};
function c() {}

// good
const thisIsMyObject = {};
function thisIsMyFunction() {}
```

1.3 使用帕斯卡式命名（大驼峰）构造函数或类，枚举（枚举中的元素使用全大写）

```javascript
// bad
function user(options) {
  this.name = options.name;
}

const bad = new user({
  name: 'nope',
});

// good
class User {
  constructor(options) {
    this.name = options.name;
  }
}

const good = new User({
  name: 'yup',
});
```

1.4 使用下划线 `_` 开头命名私有属性

```javascript
// bad
this.__firstName__ = 'Panda';
this.firstName_ = 'Panda';

// good
this._firstName = 'Panda';
```

1.5  别保存 `this` 的引用。使用箭头函数或 Function#bind

```javascript
// bad
function foo() {
  const self = this;
  return function() {
    console.log(self);
  };
}

// bad
function foo() {
  const that = this;
  return function() {
    console.log(that);
  };
}

// good
function foo() {
  return () => {
    console.log(this);
  };
}
```

1.6 当你导出默认的函数时使用小驼峰式命名。你的文件名必须和函数名完全保持一致

```javascript
function makeStyleGuide() {
}

export default makeStyleGuide;
```

1.7 如果你的文件只输出一个类，那你的文件名必须和类名完全保持一致

```javascript
// file contents
class CheckBox {
  // ...
}
export default CheckBox;

// in some other file
// bad
import CheckBox from './checkBox';

// bad
import CheckBox from './check_box';

// good
import CheckBox from './CheckBox';
```

1.8 当你导出单例、函数库、空对象时使用帕斯卡式命名

```javascript
const AirbnbStyleGuide = {
  es6: {
  }
};

export default AirbnbStyleGuide;
```

1.9 常量用大写









## 空白缩进，逗号，分号，空格

1.1 使用 2 个空格作为缩进

```javascript
// bad
function() {
∙∙∙∙const name;
}

// bad
function() {
∙const name;
}

// good
function() {
∙∙const name;
}
```

1.2 在花括号前放一个空格

```javascript
// bad
function test(){
  console.log('test');
}

// good
function test() {
  console.log('test');
}

// bad
dog.set('attr',{
  age: '1 year',
  breed: 'Bernese Mountain Dog',
});

// good
dog.set('attr', {
  age: '1 year',
  breed: 'Bernese Mountain Dog',
});
```

1.3 在控制语句（`if`、`while` 等）的小括号前放一个空格。在函数调用及声明中，不在函数的参数列表前加空格

```javascript
// bad
if(isJedi) {
  fight ();
}

// good
if (isJedi) {
  fight();
}

// bad
function fight () {
  console.log ('Swooosh!');
}

// good
function fight() {
  console.log('Swooosh!');
}
```

1.4 使用空格把运算符隔开

```javascript
// bad
const x=y+5;

// good
const x = y + 5;
```

1.5 在文件末尾插入一个空行

1.6 在使用长方法链时进行缩进。使用前面的点 `.` 强调这是方法调用而不是新语句

```javascript
// bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

// bad
$('#items').
  find('.selected').
    highlight().
    end().
  find('.open').
    updateCount();

// good
$('#items')
  .find('.selected')
    .highlight()
    .end()
  .find('.open')
    .updateCount();
    
// bad
const leds = stage.selectAll('.led').data(data).enter().append('svg:svg').class('led', true)
    .attr('width', (radius + margin) * 2).append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);

// good
const leds = stage.selectAll('.led')
    .data(data)
  .enter().append('svg:svg')
    .classed('led', true)
    .attr('width', (radius + margin) * 2)
  .append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);
```

1.7 在块末和新语句前插入空行

```javascript
// bad
if (foo) {
  return bar;
}
return baz;

// good
if (foo) {
  return bar;
}

return baz;

// bad
const obj = {
  foo() {
  },
  bar() {
  },
};
return obj;

// good
const obj = {
  foo() {
  },

  bar() {
  },
};

return obj;
```

1.8 行首逗号：**不需要**；增加结尾的逗号: **需要**

这会让 git diffs 更干净。另外，像 babel 这样的转译器会移除结尾多余的逗号，也就是说你不必担心老旧浏览器的尾逗号问题

```javascript
// bad
const story = [
    once
  , upon
  , aTime
];

// good
const story = [
  once,
  upon,
  aTime,
];

// bad
const hero = {
    firstName: 'Ada'
  , lastName: 'Lovelace'
  , birthYear: 1815
  , superPower: 'computers'
};

// good
const hero = {
  firstName: 'Ada',
  lastName: 'Lovelace',
  birthYear: 1815,
  superPower: 'computers',
};

// bad - git diff without trailing comma
const hero = {
     firstName: 'Florence',
-    lastName: 'Nightingale'
+    lastName: 'Nightingale',
+    inventorOf: ['coxcomb graph', 'modern nursing']
}

// good - git diff with trailing comma
const hero = {
     firstName: 'Florence',
     lastName: 'Nightingale',
+    inventorOf: ['coxcomb chart', 'modern nursing'],
}
```

1.9 **使用分号**

```javascript
// bad
(function() {
  const name = 'Skywalker'
  return name
})()

// good
(() => {
  const name = 'Skywalker';
  return name;
})();

// good (防止函数在两个 IIFE 合并时被当成一个参数)
;(() => {
  const name = 'Skywalker';
  return name;
})();
```

1.10 







## JavaScript Style

1.引用

1.1 对所有的引用使用 `const` ；避免使用 `var`；这能确保你无法对引用重新赋值，也不会导致出现 bug 或难以理解

1.2 如果你一定需要可变动的引用，使用 `let` 代替 `var`；因为 `let` 是块级作用域，而 `var` 是函数作用域

1.3 `let` 和 `const` 都是块级作用域

2.对象

2.1 使用字面值创建对象

2.2 使用对象方法的简写

```javascript
// bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

2.3 使用对象属性值的简写；这样更短更有描述性

```javascript
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
  lukeSkywalker: lukeSkywalker,
};

// good
const obj = {
  lukeSkywalker,
};
```

2.4 在对象属性声明前把简写的属性分组

3.数组

3.1 使用字面值创建数组

3.2 向数组添加元素时使用 Arrary.push 替代直接赋值

3.3 使用拓展运算符 `...` 复制数组

```javascript
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

3.4 使用 Array#from 把一个类数组对象转换成数组

4.解构

4.1 使用解构存取和使用多属性对象；因为解构能减少临时引用属性

```javascript
// bad
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;

  return `${firstName} ${lastName}`;
}

// good
function getFullName(obj) {
  const { firstName, lastName } = obj;
  return `${firstName} ${lastName}`;
}

// best
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}
```

4.2 对数组使用解构赋值

```javascript
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```

4.3 需要回传多个值时，使用对象解构，而不是数组解构；这样增加属性或者改变排序不会改变调用时的位置

```javascript
// bad
function processInput(input) {
  // then a miracle occurs
  return [left, right, top, bottom];
}

// 调用时需要考虑回调数据的顺序。
const [left, __, top] = processInput(input);

// good
function processInput(input) {
  // then a miracle occurs
  return { left, right, top, bottom };
}

// 调用时只选择需要的数据
const { left, right } = processInput(input);
```

5.字符串

5.1 字符串使用单引号 `''`

5.2 通过程序生成字符串时，使用模板字符串代替字符串连接；模板字符串更为简洁，更具可读性

```javascript
// bad
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// bad
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// good
function sayHi(name) {
  return `How are you, ${name}?`;
}
```

5.3 编程时使用join而不是字符串连接来构建字符串，特别是IE

```javascript
var items,
    messages,
    length, i;

messages = [{
    state: 'success',
    message: 'This one worked.'
},{
    state: 'success',
    message: 'This one worked as well.'
},{
    state: 'error',
    message: 'This one did not work.'
}];

length = messages.length;

// bad
function inbox(messages) {
  items = '<ul>';

  for (i = 0; i < length; i++) {
    items += '<li>' + messages[i].message + '</li>';
  }

  return items + '</ul>';
}

// good
function inbox(messages) {
  items = [];

  for (i = 0; i < length; i++) {
    items[i] = messages[i].message;
  }

  return '<ul><li>' + items.join('</li><li>') + '</li></ul>';
}
```



6.函数

6.1 使用函数声明代替函数表达式；因为函数声明是可命名的，所以他们在调用栈中更容易被识别。此外，函数声明会把整个函数提升（hoisted），而函数表达式只会把函数的引用变量名提升。这条规则使得箭头函数可以取代函数表达式

```javascript
// bad
const foo = function () {
};

// good
function foo() {
}
```

6.2 函数表达式

```javascript
// 立即调用的函数表达式 (IIFE)
(() => {
  console.log('Welcome to the Internet. Please follow me.');
})();
```

6.3 永远不要在一个非函数代码块（`if`、`while` 等）中声明一个函数，把那个函数赋给一个变量。浏览器允许你这么做，但它们的解析表现不一致

```javascript
// bad
if (currentUser) {
  function test() {
    console.log('Nope.');
  }
}

// good
let test;
if (currentUser) {
  test = () => {
    console.log('Yup.');
  };
}
```

6.4 永远不要把参数命名为 `arguments`。这将取代原来函数作用域内的 `arguments` 对象

```javascript
// bad
function nope(name, options, arguments) {
  // ...stuff...
}

// good
function yup(name, options, args) {
  // ...stuff...
}
```

6.5 不要使用 `arguments`。可以选择 rest 语法 `...` 替代；使用 `...` 能明确你要传入的参数。另外 rest 参数是一个真正的数组，而 `arguments` 是一个类数组

```javascript
// bad
function concatenateAll() {
  const args = Array.prototype.slice.call(arguments);
  return args.join('');
}

// good
function concatenateAll(...args) {
  return args.join('');
}
```

6.6 直接给函数的参数指定默认值，不要使用一个变化的函数参数

```javascript
// really bad
function handleThings(opts) {
  // 不！我们不应该改变函数参数。
  // 更加糟糕: 如果参数 opts 是 false 的话，它就会被设定为一个对象。
  // 但这样的写法会造成一些 Bugs。
  //（译注：例如当 opts 被赋值为空字符串，opts 仍然会被下一行代码设定为一个空对象。）
  opts = opts || {};
  // ...
}

// still bad
function handleThings(opts) {
  if (opts === void 0) {
    opts = {};
  }
  // ...
}

// good
function handleThings(opts = {}) {
  // ...
}
```

6.7 直接给函数参数赋值时需要避免副作用；因为这样的写法让人感到很困惑

 ```javascript
var b = 1;
// bad
function count(a = b++) {
console.log(a);
}
count();  // 1
count();  // 2
count(3); // 3
count();  // 3
 ```

7.箭头函数

7.1 当你必须使用函数表达式（或传递一个匿名函数）时，使用箭头函数符号；因为箭头函数创造了新的一个 `this` 执行环境，通常情况下都能满足你的需求，而且这样的写法更为简洁

```javascript
// bad
[1, 2, 3].map(function (x) {
  return x * x;
});

// good
[1, 2, 3].map((x) => {
  return x * x;
});
```

7.2 如果一个函数适合用一行写出并且只有一个参数，那就把花括号、圆括号和 `return` 都省略掉。如果不是，那就不要省略

```javascript
// good
[1, 2, 3].map(x => x * x);

// good
[1, 2, 3].reduce((total, n) => {
  return total + n;
}, 0);
```

8.构造器

8.1 总是使用 `class`。避免直接操作 `prototype`；因为 `class` 语法更为简洁更易读

```javascript
// bad
function Queue(contents = []) {
  this._queue = [...contents];
}
Queue.prototype.pop = function() {
  const value = this._queue[0];
  this._queue.splice(0, 1);
  return value;
}


// good
class Queue {
  constructor(contents = []) {
    this._queue = [...contents];
  }
  pop() {
    const value = this._queue[0];
    this._queue.splice(0, 1);
    return value;
  }
}

```

8.2 使用 `extends` 继承；因为 `extends` 是一个内建的原型继承方法并且不会破坏 `instanceof`

9.模块

9.1 总是使用模组 (`import`/`export`) 而不是其他非标准模块系统。你可以编译为你喜欢的模块系统；

```javascript
// bad
const AirbnbStyleGuide = require('./AirbnbStyleGuide');
module.exports = AirbnbStyleGuide.es6;

// ok
import AirbnbStyleGuide from './AirbnbStyleGuide';
export default AirbnbStyleGuide.es6;

// best
import { es6 } from './AirbnbStyleGuide';
export default es6;
```

9.2 不要使用通配符 import；这样能确保你只有一个默认 export

```javascript
// bad
import * as AirbnbStyleGuide from './AirbnbStyleGuide';

// good
import AirbnbStyleGuide from './AirbnbStyleGuide';
```

9.3 不要从 import 中直接 export；虽然一行代码简洁明了，但让 import 和 export 各司其职让事情能保持一致

```javascript
// bad
// filename es6.js
export { es6 as default } from './airbnbStyleGuide';

// good
// filename es6.js
import { es6 } from './AirbnbStyleGuide';
export default es6;
```

10.不要使用 iterators。使用高阶函数例如 `map()` 和 `reduce()` 替代 `for-of`

```javascript
const numbers = [1, 2, 3, 4, 5];

// bad
let sum = 0;
for (let num of numbers) {
  sum += num;
}

sum === 15;

// good
let sum = 0;
numbers.forEach((num) => sum += num);
sum === 15;

// best (use the functional force)
const sum = numbers.reduce((total, num) => total + num, 0);
sum === 15;
```

11.属性

11.1 使用 `.` 来访问对象的属性

```javascript
const luke = {
  jedi: true,
  age: 28,
};

// bad
const isJedi = luke['jedi'];

// good
const isJedi = luke.jedi;
```

11.2 当通过变量访问属性时使用中括号 `[]`

```javascript
const luke = {
  jedi: true,
  age: 28,
};

function getProp(prop) {
  return luke[prop];
}

const isJedi = getProp('jedi');
```

12.变量

12.1 一直使用 `const` 来声明变量；使用 `const` 声明每一个变量；这样增加新变量将变的更加容易，而且你永远不用再担心调换错 `;` 跟 `,`

```javascript
// bad
const items = getItems(),
    goSportsTeam = true,
    dragonball = 'z';

// bad
// (compare to above, and try to spot the mistake)
const items = getItems(),
    goSportsTeam = true;
    dragonball = 'z';

// good
const items = getItems();
const goSportsTeam = true;
const dragonball = 'z';
```

12.2 将所有的 `const` 和 `let` 分组；当你需要把已赋值变量赋值给未赋值变量时非常有用

```javascript
// bad
let i, len, dragonball,
    items = getItems(),
    goSportsTeam = true;

// bad
let i;
const items = getItems();
let dragonball;
const goSportsTeam = true;
let len;

// good
const goSportsTeam = true;
const items = getItems();
let dragonball;
let i;
let length;
```

12.3 在你需要的地方给变量赋值，但请把它们放在一个合理的位置；因为`let` 和 `const` 是块级作用域而不是函数作用域

```javascript
// bad - unnecessary function call
function(hasName) {
  const name = getName();

  if (!hasName) {
    return false;
  }

  this.setFirstName(name);

  return true;
}

// good
function(hasName) {
  if (!hasName) {
    return false;
  }

  const name = getName();
  this.setFirstName(name);

  return true;
}
```

13.提升Hoisting

 13.1 `var` 声明会被提升至该作用域的顶部，但它们赋值不会提升。`let` 和 `const` 声明不会被提示

```javascript
// 由于变量提升的原因，
// 在引用变量后再声明变量是可以运行的。
// 注：变量的赋值 `true` 不会被提升。
function example() {
  console.log(declaredButNotAssigned); // => undefined
  var declaredButNotAssigned = true;
}

// 编译器会把函数声明提升到作用域的顶层，
// 这意味着我们的例子可以改写成这样：
function example() {
  let declaredButNotAssigned;
  console.log(declaredButNotAssigned); // => undefined
  declaredButNotAssigned = true;
}

// 使用 const 和 let
function example() {
  console.log(declaredButNotAssigned); // => throws a ReferenceError
  console.log(typeof declaredButNotAssigned); // => throws a ReferenceError
  const declaredButNotAssigned = true;
}
```

13.2 匿名函数表达式的变量名会被提升，但函数内容并不会

```javascript
function example() {
  console.log(anonymous); // => undefined

  anonymous(); // => TypeError anonymous is not a function

  var anonymous = function() {
    console.log('anonymous function expression');
  };
}
```

13.3 命名的函数表达式的变量名会被提升，但函数名和函数函数内容并不会

```javascript
function example() {
  console.log(named); // => undefined

  named(); // => TypeError named is not a function

  superPower(); // => ReferenceError superPower is not defined

  var named = function superPower() {
    console.log('Flying');
  };
}

// the same is true when the function name
// is the same as the variable name.
function example() {
  console.log(named); // => undefined

  named(); // => TypeError named is not a function

  var named = function named() {
    console.log('named');
  }
}
```

13.4 函数声明的名称和函数体都会被提升

```
function example() {
  console.log(superPower);
  superPower(); // => Flying

  function superPower() {
    console.log('Flying');
  }
}
```

14.比较运算符 & 等号

14.1 优先使用 `===` 和 `!==` 而不是 `==` 和 `!=`

14.2 条件表达式例如 `if` 语句通过抽象方法 `ToBoolean` 强制计算它们的表达式并且总是遵守下面的规则：

- **对象** 被计算为 **true**
- **Undefined** 被计算为 **false**
- **Null** 被计算为 **false**
- **布尔值** 被计算为 **布尔的值**
- **数字** 如果是 **+0、-0、或 NaN** 被计算为 **false**, 否则为 **true**
- **字符串** 如果是空字符串 `''` 被计算为 **false**，否则为 **true**

14.3 使用简写

```javascript
// bad
if (name !== '') {
  // ...stuff...
}

// good
if (name) {
  // ...stuff...
}

// bad
if (collection.length > 0) {
  // ...stuff...
}

// good
if (collection.length) {
  // ...stuff...
}

```

15.代码块

15.1 使用大括号包裹所有的多行代码块

```javascript
// bad
if (test)
  return false;

// good
if (test) return false;

// good
if (test) {
  return false;
}

// bad
function() { return false; }

// good
function() {
  return false;
}
```

15.2 如果通过 `if` 和 `else` 使用多行代码块，把 `else` 放在 `if` 代码块关闭括号的同一行

```javascript
// bad
if (test) {
  thing1();
  thing2();
}
else {
  thing3();
}

// good
if (test) {
  thing1();
  thing2();
} else {
  thing3();
}
```

16.注释

16.1 使用 `/** ... */` 作为多行注释。包含描述、指定所有参数和返回值的类型和值

```javascript
// bad
// make() returns a new element
// based on the passed in tag name
//
// @param {String} tag
// @return {Element} element
function make(tag) {

  // ...stuff...

  return element;
}

// good
/**
 * make() returns a new element
 * based on the passed in tag name
 *
 * @param {String} tag
 * @return {Element} element
 */
function make(tag) {

  // ...stuff...

  return element;
}
```

16.2 使用 `//` 作为单行注释。在评论对象上面另起一行使用单行注释。在注释前插入空行

```javascript
// bad
const active = true;  // is current tab

// good
// is current tab
const active = true;

// bad
function getType() {
  console.log('fetching type...');
  // set the default type to 'no type'
  const type = this._type || 'no type';

  return type;
}

// good
function getType() {
  console.log('fetching type...');

  // set the default type to 'no type'
  const type = this._type || 'no type';

  return type;
}
```

16.3 给注释增加 `FIXME` 或 `TODO` 的前缀可以帮助其他开发者快速了解这是一个需要复查的问题，或是给需要实现的功能提供一个解决方式。这将有别于常见的注释，因为它们是可操作的。使用 `FIXME -- need to figure this out` 或者 `TODO -- need to implement`

* 使用 `// FIXME`: 标注问题

  ```javascript
  class Calculator {
    constructor() {
      // FIXME: shouldn't use a global here
      total = 0;
    }
  }
  ```

  

* 使用 `// TODO`: 标注问题的解决方式

  ```javascript
  class Calculator {
    constructor() {
      // TODO: total should be configurable by an options param
      this.total = 0;
    }
  }
  ```

17.类型转换

17.1 字符串

```javascript
//  => this.reviewScore = 9;

// bad
const totalScore = this.reviewScore + '';

// good
const totalScore = String(this.reviewScore);
```

17.2 对数字使用 `parseInt` 转换，并带上类型转换的基数

```javascript
const inputValue = '4';

// bad
const val = new Number(inputValue);

// bad
const val = +inputValue;

// bad
const val = inputValue >> 0;

// bad
const val = parseInt(inputValue);

// good
const val = Number(inputValue);

// good
const val = parseInt(inputValue, 10);
```

17.3 如果因为某些原因 parseInt 成为你所做的事的瓶颈而需要使用位操作解决性能问题时，留个注释说清楚原因和你的目的

```javascript
// good
/**
 * 使用 parseInt 导致我的程序变慢，
 * 改成使用位操作转换数字快多了。
 */
const val = inputValue >> 0;
```

17.4 布尔

```javascript
const age = 0;

// bad
const hasAge = new Boolean(age);

// good
const hasAge = Boolean(age);

// good
const hasAge = !!age;
```

18 存取器

18.1 属性的存取函数不是必须的；如果你需要存取函数时使用 `getVal()` 和 `setVal('hello')`

```javascript
// bad
dragon.age();

// good
dragon.getAge();

// bad
dragon.age(25);

// good
dragon.setAge(25);
```

18.2 如果属性是布尔值，使用 `isVal()` 或 `hasVal()`

```javascript
// bad
if (!dragon.age()) {
  return false;
}

// good
if (!dragon.hasAge()) {
  return false;
}
```

18.3 创建 `get()` 和 `set()` 函数是可以的，但要保持一致

```javascript
class Jedi {
  constructor(options = {}) {
    const lightsaber = options.lightsaber || 'blue';
    this.set('lightsaber', lightsaber);
  }

  set(key, val) {
    this[key] = val;
  }

  get(key) {
    return this[key];
  }
}
```

19.jQuery

19.1 使用 `$` 作为存储 jQuery 对象的变量名前缀

```javascript
// bad
const sidebar = $('.sidebar');

// good
const $sidebar = $('.sidebar');
```

19.2 缓存 jQuery 查询

```javascript
// bad
function setSidebar() {
  $('.sidebar').hide();

  // ...stuff...

  $('.sidebar').css({
    'background-color': 'pink'
  });
}

// good
function setSidebar() {
  const $sidebar = $('.sidebar');
  $sidebar.hide();

  // ...stuff...

  $sidebar.css({
    'background-color': 'pink'
  });
}
```

19.3 对有作用域的 jQuery 对象查询使用 `find`

```javascript
// bad
$('ul', '.sidebar').hide();

// bad
$('.sidebar').find('ul').hide();

// good
$('.sidebar ul').hide();

// good
$('.sidebar > ul').hide();

// good
$sidebar.find('ul').hide();
```



















## React Style

基础规范

1. 统一全部采用 ES6
2. 组件文件名称和类名采用大驼峰命名
3. 函数名（方法名）小驼峰命名

 命名规范

- 组件名称：大驼峰
- 属性名称：小驼峰
- 事件处理函数：`handleSomething`
- 自定义事件属性名称：`onSomething={this.handleSomething}`
- key: 不能使用数组 index ，构造或使用唯一的 id
- 组件方法名称：避免使用下划线开头的命名

jsx书写规范

```
//自闭合
// bad
<Foo className="stuff"></Foo>

// good
<Foo className="stuff" />

//属性对齐
// bad
<Foo superLongParam="bar"
     anotherSuperLongParam="baz" />

// good
<Foo
    superLongParam="bar"
    anotherSuperLongParam="baz"
/>

// if props fit in one line then keep it on the same line
<Foo bar="bar" />

//返回
// bad
render() {
  return <MyComponent className="long body" foo="bar">
           <MyChild />
         </MyComponent>;
}

// good
render() {
  return (
    <MyComponent className="long body" foo="bar">
      <MyChild />
    </MyComponent>
  );
}

// good, when single line
render() {
  const body = <div>hello</div>;
  return <MyComponent>{body}</MyComponent>;
}
```









## CSS Style





## HTML Style



