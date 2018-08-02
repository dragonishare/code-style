代码编辑器（或IDE）的插件会帮我们做一些静态语法检查的工作，但是如何自定义语法规则，如何集成到开发流程中，仍然需要我们花一些时间去了解



- JSLint是其中最老的工具。它根据作者的经验，定义了一套js规则，但用户无法更改或拓展这些规则，只能被迫接受，而且报错也不够友好；
- JSHint在JSLint的基础上进行了一些改进，用户可以更改规则，但仍然不能自定义新的规则，而且存在强制和分散两种模式，配置十分混乱；
- JSCS开始支持自定义规则和插件，报错定位也更加准确，但仅仅支持代码风格的检查，无法检查出一些简单的潜在bug；
- ESLint是最新出来的工具，它被设计的容易拓展、拥有丰富的可自定义规则和插件、支持ES6和JSX，另外输出也更加友好

## esling是什么

ESLint 是一个**开源的 JavaScript 代码检查工具**，由 Nicholas C. Zakas 于2013年6月创建。**代码检查**是一种静态的分析，常用于寻找有问题的模式或者代码，并且不依赖于具体的编码风格。对大多数编程语言来说都会有代码检查，一般来说编译程序会内置检查工具。

JavaScript 是一个动态的弱类型语言，在开发中比较容易出错。因为没有编译程序，为了寻找 JavaScript 代码错误通常需要在执行过程中不断调试。像 ESLint 这样的可以让程序员在编码的过程中发现问题而不是在执行的过程中。
ESLint 的初衷是为了让程序员可以创建自己的检测规则。ESLint 的所有规则都被设计成可插入的。ESLint 的默认规则与其他的插件并没有什么区别，规则本身和测试可以依赖于同样的模式。为了便于人们使用，ESLint 内置了一些规则，当然，你可以在使用过程中自定义规则。

ESLint **使用 Node.js 编写**，这样既可以有一个快速的运行环境的同时也便于安装。


## 文件配置

ESlint共支持6种格式的配置文件，其使用的优先级和说明如下：

1. .eslintrc.js：模块定义，export的对象即为配置对象
2. .eslintrc.yaml：yaml语法
3. .eslintrc.yml：yaml语法
4. .eslintrc.json：JSON语法
5. **.eslintrc：兼容yaml和JSON语法**
6. package.json： 在package.json的eslintConfig字段中定义



## 配置场景
* eslint prettier项目中配置
* git commit时自动格式化 husky lint-staged

* 编辑器配置eslint prettier


prettier 开发的时候报错 提示修改
1、手动修改 默认
2、编辑器装插件修改自动 推荐

git提交时，提醒错误，
1、warn的，可以直接提交，提交的时候会通过prettier自动修改warn错误 默认
2、提醒错误，不让提交，必须修改，
  2.1 手动修改 默认
  2.2 编辑器插件自动修改 推荐




## 参考地址

* [前端代码检查](http://imweb.io/topic/59a3fd4a79c5294e26eb6001)
* [Add ESLint & Prettier to VS Code for a Create React App](https://www.youtube.com/watch?v=bfyI9yl3qfE)

