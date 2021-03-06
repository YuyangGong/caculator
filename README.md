# 算式计算器

[![预览图片](./src/img/demo-pic.png)](http://yuyang.date/caculator/public/index.html)


写给程序员使用的算式计算器。

[百度IFE前端学院](http://ife.baidu.com/)的一项[课程任务](http://ife.baidu.com/course/detail/id/43)。

可以直接在[这里](http://yuyang.date/caculator/public/index.html)尝试使用此计算器。

如果您只想方便的线上使用，可以跳过之前的内容，直接浏览[使用手册](#使用手册)。

## 内容索引

- [本地使用](#本地使用)
- [提交漏洞或意见](#提交漏洞或意见)
- [功能特性](#功能特性)
- [使用手册](#使用手册)
- [后续将增加的功能](#后续将增加的功能)
- [版本](#版本)
- [贡献者](#贡献者)
- [开源许可证](#开源许可证)

## 本地使用

通过以下git命令将文件包下载到本地运行:

```bash
git clone https://github.com/YuyangGong/caculator.git
```

### 文件目录

下载到本地后你将看到如下目录及文件:

```
caculator/
├── src/
│   ├── js/
│   │   ├── constants.js
│   │   ├── util.js
│   │   ├── status.js
│   │   ├── errorMessage.js
│   │   ├── core;.js
│   │   └── main.js
│   ├── less/
│   │   └── main.less
│   └── index.html
├── public/
│  ├── js/
│  │   ├── main.min.js
│  │   └── main.min.js.map
│  ├── css/
│  │   ├── main.min.css
│  │   └── main.min.css.map
│  └── index.html
├── test/
│   ├── main.test.js
│   └── mocha.opts
└── mochawesome-reports/
    ├── mochawesome.html
    └── mochawesome.js
```

```./src```目录中放置编译前的源文件，```./public```目录中放置编译后的文件，```./public/index.html```是项目的入口文件。源文件```./src/js```中```core.js```负责此算式计算器的内核，```./main.js```负责页面交互，```./constants.js```放置计算器所需常量，```./util.js```放置计算器所需方法，```./status.js```放置计算器模式状态，```./errorMessage.js```负责计算器错误码对应的错误信息。在项目编写阶段采用[TDD](http://baike.baidu.com/link?url=zhp9My3j-qwcXz3gnIb0-2wlz0EREsiZ-Bl49Jl47sFpILY13H9mKSL0dg-BEcFZ2Uwj3ku1C3qIbH73H16cN_)开发模式，引入了测试框架[mocha](http://mochajs.org/), ```./test```中放置的```./test/main.test.js```是mocha的测试文件，```./test/mocha.opts```是mocha的配置文件。为测试结果可视化，引入了[mocha](http://mochajs.org/)的插件[mochawesome](https://www.npmjs.com/package/mochawesome)，```./mochawesome-reports/mochawesome.html```展现了测试结果。


## 提交漏洞或意见

如果您对此项目有任何建议或者发现了漏洞可以在此处提个 [issue](https://github.com/YuyangGong/caculator/issues)。


## 功能特性

* 支持加减乘除幂余基本运算
* 支持左右圆括号提升优先级
* 内置基本常量
* 内置基本方法
* 支持嵌套使用方法
* 支持新建自定义方法和常量
* 支持新建变量时使用已有方法及常量
* 支持三角函数的弧度与角度切换
* 支持输入错误时自定义报错
* 输入格式错误时,报错精确到列数

如果想要了解详细，请浏览接下来的[使用手册](#使用手册)及[开发者手册](#开发者手册)。

## 使用手册

#### 常规运算
可以进行加减乘除余等基本运算，且能用左右圆括号进行提升优先级。如: (2+3-4)%2/3

#### 幂运算符^
幂运算符^，可以与其他运算符混用。

#### 内置必须的常量和强大的方法库
计算器内置必须的常量和强大的方法库，具体可见接下来的常量表和方法表

#### 方法可以嵌套使用
无论是内置的方法，还是自定义方法都可以嵌套使用，如之前提及的```pow(pow(2,3),3)```

### 内置常量表
##### e
代表 自然对数
##### π
代表 圆周率

### 内置方法表
arg 代表接受的参数数量，n代表无限制, >n代表最低为n, 最高不限制
##### abs
代表 绝对值运算，abs(-1) = 1  (arg: 1)
##### avg
代表 均值运算，avg(1,2) = 1.5  (arg: >2)
##### sin
代表 正弦运算，sin(30) = 0.5  (arg：1) 
##### cos
代表 余弦运算，cos(60) = 0.5  (arg: 1)
##### tan
代表 正切运算，tan(45) = 1  (arg: 1)
##### cot
代表 余切运算，cot(45) = 1  (arg: 1)
##### log
代表 10底对数运算，log(100) = 2  (arg: 1)
##### fac
代表 阶乘运算，fac(3) = 3\*2\*1 = 6 (arg: 1)
##### HCF
代表 最大公因数，HCF(6,4) = 2 (arg: 2)
##### pow
代表 幂运算，pow(2,3) = 8 (arg: 2)
##### sum
代表 求和运算， sum(2,3) = 5 (arg: >2)

### 创建自定义常量和方法
可以创建自己的常量和方法, 合法的常量名只能包含数字、字母、下划线，并且只能由下划线和字母开头。

在上面内置方法表中，你可能会发现一个名叫```HCF```的求最小公倍数的方法，那你可能会问，有没有相应的求最小公倍数的方法呢？答案是并没有，但是借助可以创建自定义方法，如果设置其方法名为```gcd```, 设置其方法体为```a*b/HCF(a,b)```,就可以使用```gcd```方法来直接求最小公倍数了。


## 后续将增加的功能

算术功能方面：

* [x] 允许方法与括号之间、数值与运算符之间存在不影响计算的空格
* [x] 允许幂运算符^连续使用(如: 2^3^4)和嵌套(如:(2+1)^3)
* [x] 更精准的报错系统，应该精确到错误的列数，而不仅仅是只有错误信息

UI界面方面：

* [x] 增加传统计算器界面，用户可以在传统计算器与输入栏计算器之间自由切换
* [ ] 增加自定义选项，用户可以切换不同的处理模式(如参数数量的严格模式及普通模式)
* [ ] 增加自定义方法和常量修改系统，用户可以对其自定义的常量及方法进行删、改，而不仅仅只有添加
* [ ] 移动端的配适
* [ ] 模拟输入框, 以代替原生输入框, 保证定位更精准。

代码算法方面:

* [x] 取消eval的使用，完全用栈算法代替
* [ ] 精简代码，封装重复使用代码。


## 版本

**v1.0.0** 初版本发布

**v2.0.0** 用栈重写项目，增加足量判断语句实现精确定位输入格式错误索引位置


## 贡献者

**yuyanggong**

- <https://github.com/yuyanggong>
- email: 421736079@qq.com

## 开源许可证

[MIT License](https://github.com/twbs/bootstrap/blob/master/LICENSE)
