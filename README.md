# code-style

> * 文件名建议只使用**小写字母**，不使用大写字母；单词之间用连接符`-`或者下划线`_`
> * 为了醒目，某些说明文件的文件名，可以使用大写字母，比如`README`、`LICENSE`

主要原因：

* **可移植性**  Linux 系统是**大小写敏感**的，而 Windows 系统和 Mac 系统正好相反，**大小写不敏感**
* **易读性** 小写文件名更易读
* **易用性** 某些系统会生成一些预置的用户目录，采用首字母大写的目录名；某些常见的配置文件或说明文件，也采用大写的文件名，容易区分

**建议文件夹和文件用短线`-`**

**html和css使用双引号`""` js使用单引号`''`**



## Repository Name Style

* **特别简易和容易区分**的直接**小写字母**，单词组合或者缩写组合，比如jsdemos，jstutorial
* **小写字母**，单词之间直接用短线`-`连接，比如code-style
* **小写字母**，单词之间直接用下划线`_`连接，比如code_style

**建议仓库名单词小写组合，或者短线`-`**











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







## CSS Style





## HTML Style



