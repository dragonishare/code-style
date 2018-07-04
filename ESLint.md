代码编辑器（或IDE）的插件会帮我们做一些静态语法检查的工作，但是如何自定义语法规则，如何集成到开发流程中，仍然需要我们花一些时间去了解



- JSLint是其中最老的工具。它根据作者的经验，定义了一套js规则，但用户无法更改或拓展这些规则，只能被迫接受，而且报错也不够友好；
- JSHint在JSLint的基础上进行了一些改进，用户可以更改规则，但仍然不能自定义新的规则，而且存在强制和分散两种模式，配置十分混乱；
- JSCS开始支持自定义规则和插件，报错定位也更加准确，但仅仅支持代码风格的检查，无法检查出一些简单的潜在bug；
- ESLint是最新出来的工具，它被设计的容易拓展、拥有丰富的可自定义规则和插件、支持ES6和JSX，另外输出也更加友好

## 文件配置

ESlint共支持6种格式的配置文件，其使用的优先级和说明如下：

1. .eslintrc.js：模块定义，export的对象即为配置对象
2. .eslintrc.yaml：yaml语法
3. .eslintrc.yml：yaml语法
4. .eslintrc.json：JSON语法
5. **.eslintrc：兼容yaml和JSON语法**
6. package.json： 在package.json的eslintConfig字段中定义





## 参考地址

* [前端代码检查](http://imweb.io/topic/59a3fd4a79c5294e26eb6001)