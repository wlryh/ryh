# 日常记录
## 2018.07.18
### aurelia configureRouter config.map 中title的国际化
思路1：刚开始的思路是想在config.map执行过后再根据后台获取到的国际化内容更新title
问题：router的title没有对应的更新方法，updateTitle不是用于Title的更新

------

思路2：利用aurelia-i18n和router的Internationalizing Titles方法进行国际化
问题：我们项目目前所有的国际化都是取得后台的资源，如果这样的话就得在前端加入aurelia-i18n，并要在前端翻译所有国际化的内容，改方法不可取

------

思路3：前两种方法没有成功之后，问了下同事，考虑在config.map之前获取后台国际化资源，之后在config.map中用变量给title赋值
问题：因为js都是异步执行，所以在config.map执行之前，后台的请求还没有返回
解决方法：异步改同步，async await使用，在config.map之前获取到了后台请求的国际化资源

### async await使用
async 用于申明一个 function 是异步的，而 await 用于等待一个异步方法执行完成

async 函数返回的是一个 Promise 对象。async 函数（包含函数语句、函数表达式、Lambda表达式）会返回一个 Promise 对象，如果在函数中 return 一个直接量，async 会把这个直接量通过 Promise.resolve() 封装成 Promise 对象

一般来说，都认为 await 是在等待一个 async 函数完成。不过按语法说明，await 等待的是一个表达式，这个表达式的计算结果是 Promise 对象或者其它值（换句话说，就是没有特殊限定）。

因为 async 函数返回一个 Promise 对象，所以 await 可以用于等待一个 async 函数的返回值——这也可以说是 await 在等 async 函数，但要清楚，它等的实际是一个返回值。注意到 await 不仅仅用于等 Promise 对象，它可以等任意表达式的结果，所以，await 后面实际是可以接普通函数调用或者直接量的

## 对象的取值方式
```
var obj = {abc:"ss",nn:90};
var v1 = obj.abc;//使用点的方式
var v2 = obj["abc"];//使用中括号的方式
```
 在实际项目中一般使用点，会方便许多，但是如果key是变量的话就不能使用点了，js会理解变量为对象的key值，造成混淆
```
var v3 = obj[key];//key是一个变量
```
## 2018.07.19
### npm install: "cb() never called"
前端项目在编译部署时报cb() never called错误，在网上搜了一些答案，有说是node和npm的版本问题，有说是npm的缓存问题
因为昨天编译还可以正常运行，所以应该不是版本出现的问题，然后想到是不是缓存问题，运维执行npm cache clean之后没有出现报错信息
### npm 缓存
npm cache 提供了三个命令，分别是npm cache add, npm cache clean, npm cache verify。

npm cache add
官方解释说这个命令主要是 npm 内部使用，但是也可以用来手动给一个指定的 package 添加缓存。(This command is primarily intended to be used internally by npm, but it can provide a way to add data to the local installation cache explicitly.)

npm cache clean
删除缓存目录下的所有数据。从 npm@5 开始，为了保证缓存数据的有效性和完整性，需要加上 --force 参数。

npm cache verify
验证缓存数据的有效性和完整性，清理垃圾数据。
