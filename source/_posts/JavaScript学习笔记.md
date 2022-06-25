---
thumbnail: 'https://picsum.photos/1280/720?random=4 #111'
title: JavaScript学习笔记
date: 2021-12-06 22:43:02
tags:
- 🔥前端
- 📔笔记
- 🍕JS
---

# 函数的调用

简单点说，带括号的是函数调用，**直接执行函数**；不带括号的是绑定事件，**事件触发再执行**。

复杂点说，带括号的是把返回值赋值给事件，不带括号的是把函数体所在地址位置赋值给事件。

.then()方法是异步执行；当.then()前的方法执行完后再执行then()内部的程序，这样就避免了，数据没获取到等的问题

# Promise

Promise 对象代表了未来将要发生的事件，用来传递异步操作的消息。

## Promise 对象有以下两个特点

1. 对象的状态不受外界影响。Promise 对象代表一个异步操作，有三种状态：

   - pending: 初始状态，不是成功或失败状态。
   - fulfilled ( resolve ): 意味着操作成功完成。
   - rejected: 意味着操作失败。

   只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态。这也是 Promise 这个名字的由来，它的英语意思就是「承诺」，表示其他手段无法改变。

2. 一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise 对象的状态改变，只有两种可能：从 Pending 变为 Resolved 和从 Pending 变为 Rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果。就算改变已经发生了，你再对 Promise 对象添加回调函数，也会立即得到这个结果。这与事件（Event）完全不同，事件的特点是，如果你错过了它，再去监听，是得不到结果的。

# 解析数组对象

![img](https://gitee.com/feng-lekai/blog-image/raw/master/img/293534a7971c4647934ae4bddbe7f39b.jpg)

通过.map()方法返回新数组，**es6中只有一个形参可以不用括号，** `item => Object.values(item)`map内的方法使用Object.values(item)，返回所有object对象中value的值。

![img](https://gitee.com/feng-lekai/blog-image/raw/master/img/7341c336b25f4d409b21a41f92ef9f21.jpg)

# bind()

方法会创建一个新的函数，称为绑定函数,fun方法在this环境下调用

该方法可传入两个参数，第一个参数作为this，第二个及以后的参数则作为函数的参数调用

# window.location.href的用法

javascript中的location.href有很多种用法，主要如下。

self.location.href="/url" 当前页面打开URL页面
location.href="/url" 当前页面打开URL页面
windows.location.href="/url" 当前页面打开URL页面，前面三个用法相同。
this.location.href="/url" 当前页面打开URL页面
parent.location.href="/url" 在父页面打开新页面
top.location.href="/url" 在顶层页面打开新页面

如果页面中自定义了frame，那么可将parent self top换为自定义frame的名称,效果是在frame窗口打开url地址

此外，window.location.href=window.location.href;和window.location.Reload()和都是刷新当前页面。区别在于是否有提交数据。当有提交数据时，window.location.Reload()会提示是否提交，window.location.href=window.location.href;则是向指定的url提交数据

你可以这么写： location.replace(location.href);

## 一些通用方法

`window.open(url)`

`top.location.href="/url"`

### 文件下载

```js
      // 文件链接直接下载
      const a = document.createElement("a");
      const url = "url";
      const fileName = "filename.xlsx";
      a.herf = url;
      a.download = fileName;
      a.click();
      
      // 后端blob流文件下载
      fetch(url).then((response) =>
        response.blob().then((blob) => {
          const a = document.createElement("a");
          const url = window.URL.createObjectURL(blob);
          const fileName = "filename.xlsx";
          a.herf = url;
          a.download = fileName;
          a.click();
          window.URL.revokeObjectURL(url);
        })
      );
```

# 返回并刷新页面：

location.replace(document.referrer);

document.referrer //前一个页面的URL

不要用 history.go(-1)，或 history.back();来返回并刷新页面，这两种方法不会刷新页面。

# 时间格式化

```js
const value = new Date();
const getDate = value.getFullYear() + '-' + (value.getMonth() + 1) + '-' + value.getDate() + ' ' + value.getHours() + ':' + value.getMinutes() + ':' + value.getSeconds();
```

# 字符串转换数字，判断是否是数字

```js
     // 数字加字母等非数字转换
     const s = '234string';
     parseInt(s);　//234
     parseFloat(s);  //234.0
     
     isNaN() // 判断是否是数字，是返回true，否则返回false
```

# 遍历对象

```js
// 创建一个对象并指定其原型，bar 为原型上的属性
const obj = Object.create({
 bar: 'bar'
})
 
// foo 为对象自身的属性
obj.foo = 'foo'
 
for (let key in obj) {
 console.log(obj[key]) // foo, bar
}
```

for of是ES6新增的循环方法

①：for of无法循环遍历对象

②：遍历输出结果不同

③：for in 会遍历自定义属性，for of不会

# 数组中删除某个元素

```js
//删除起始下标为1，长度为1的一个值(len设置1，如果为0，则数组不变) 
const arr = ['a','b','c','d']; 
arr.splice(1,1); 
console.log(arr); 
//['a','c','d']; 
  
  
//删除起始下标为1，长度为2的一个值(len设置2) 
const arr2 = ['a','b','c','d'] 
arr2.splice(1,2); 
console.log(arr2); 
//['a','d']
```

**split() 方法用于把一个字符串分割成字符串数组。**

**在判断中 == '' 会判断 0，''和undefinded**

# 深拷贝和浅拷贝

## JSON转换

```js
const targetObj = JSON.parse(JSON.stringify(copyObj))
let arr4 = JSON.parse(JSON.stringify(arr))
```

缺点：

1. 如果对象里有函数,函数无法被拷贝下来
2. 无法拷贝copyObj对象原型链上的属性和方法
3. 当数据的层次很深，会栈溢出

## 普通递归函数

```js
function deepCopy( source ) {
if (!isObject(source)) return source; //如果不是对象的话直接返回
    let target = Array.isArray( source ) ? [] : {} //数组兼容
    for ( let k in source ) {
    	if (source.hasOwnProperty(k)) {
    		if ( typeof source[ k ] === 'object' ) {
            	target[ k ] = deepCopy( source[ k ] )
        	} else {
            	target[ k ] = source[ k ]
        	}
    	}
    }
    return target
}

function isObject(obj) {
    return typeof obj === 'object' && obj !== null
}
```

缺点：

1. 无法保持引用
2. 当数据的层次很深，会栈溢出

## 防栈溢出函数

```js
function cloneLoop(x) {
    const root = {};

    // 栈
    const loopList = [
        {
            parent: root,
            key: undefined,
            data: x,
        }
    ];

    while(loopList.length) {
        // 深度优先
        const node = loopList.pop();
        const parent = node.parent;
        const key = node.key;
        const data = node.data;

        // 初始化赋值目标，key为undefined则拷贝到父元素，否则拷贝到子元素
        let res = parent;
        if (typeof key !== 'undefined') {
            res = parent[key] = {};
        }

        for(let k in data) {
            if (data.hasOwnProperty(k)) {
                if (typeof data[k] === 'object') {
                    // 下一次循环
                    loopList.push({
                        parent: res,
                        key: k,
                        data: data[k],
                    });
                } else {
                    res[k] = data[k];
                }
            }
        }
    }

    return root;
}
```

优点：

1. 不会栈溢出
2. 支持很多层级的数据

```js
 function copyObject(orig) {
    var copy = Object.create(Object.getPrototypeOf(orig));
    copyOwnPropertiesFrom(copy, orig);
    return copy;
  }


  function copyOwnPropertiesFrom(target, source) {
    Object
    .getOwnPropertyNames(source)
    .forEach(function (propKey) {
      var desc = Object.getOwnPropertyDescriptor(source, propKey);
      Object.defineProperty(target, propKey, desc);
    });
    return target;
  }

  var obj = {
    name: 'Jack',
    age: '32',
    job: 'developer'
  };

  var obj2 = copyObject(obj);
  console.log(obj2);
  obj.age = 39;
  obj.name = 'Tom';
  console.log(obj);
  console.log(obj2);
```

# 一些数据数据处理的方法

```js
// string转number
parseInt(string); // 整型
parseFloat(string); // 浮点型
// 浮点数处理
let num = '1.2345'
Math.floor(num * 100) / 100; //向上取整
Math.ceil(num * 100) / 100; // 向下取整
Math.round(num * 100) / 100; // 四舍五入
NumberObject.toFixed(num) //这里的num是指0~20的数字，用于保留小数后num位，如果不足会补0
```

# 使用filter做批量勾选删除

```js
let new_arr = attendeeList.filter(
  (attendee) => selectedRowKeys.filter((key) => key === attendee.id).length === 0
)
```

# 数组上移下移操作

```js
up(index) {
            if(index === 0) {
              return
            }
            //在上一项插入该项
            this.list.splice(index - 1, 0, (this.list[index]))
            //删除后一项
            this.list.splice(index + 1, 1)

            this.save();
        },
        down(index) {
            if (index === (this.list.length-1)) {
              return
            }
            // 在下一项插入该项
            this.list.splice(index + 2, 0, (this.list[index]))
            // 删除前一项
            this.list.splice(index, 1)

            this.save();
        },
```

| 字母 |                             含义                             |                             示例                             |
| ---- | :----------------------------------------------------------: | :----------------------------------------------------------: |
| y    |       年份。一般用 yy 表示两位年份，yyyy 表示 4 位年份       |   使用 yy 表示的年扮，如 11；使用 yyyy 表示的年份，如 2011   |
| M    | 月份。一般用 MM 表示月份，如果使用 MMM，则会根据语言环境显示不同语言的月份 | 使用 MM 表示的月份，如 05；使用 MMM 表示月份，在 Locale.CHINA语言环境下，如“十月”；在 Locale.US语言环境下，如 Oct |
| d    |               月份中的天数。一般用 dd 表示天数               |                  使用 dd 表示的天数，如 10                   |
| D    |       年份中的天数。表示当天是当年的第几天， 用 D 表示       |              使用 D 表示的年份中的天数，如 295               |
| E    | 星期几。用 E 表示，会根据语言环境的不同， 显示不同语言的星期几 | 使用 E 表示星期几，在 Locale.CHINA 语言环境下，如“星期四”；在 Locale.US 语言环境下，如 Thu |
| H    |         一天中的小时数（0~23)。一般用 HH 表示小时数          |                 使用 HH 表示的小时数，如 18                  |
| h    |        一天中的小时数（1~12)。一般使用 hh 表示小时数         | 使用 hh 表示的小时数，如 10 (注意 10 有可能是 10 点，也可能是 22 点） |
| m    |                分钟数。一般使用 mm 表示分钟数                |                 使用 mm 表示的分钟数，如 29                  |
| s    |                  秒数。一般使用 ss 表示秒数                  |                  使用 ss 表示的秒数，如 38                   |
| S    |               毫秒数。一般使用 SSS 表示毫秒数                |                使用 SSS 表示的毫秒数，如 156                 |

`YYYY-MM-dd HH:mm:ss`

# 前端模糊查询

```js
//字符串方法indexOf
var len = list.length;
var arr = [];
for(var i=0;i<len;i++){
    //如果字符串中不包含目标字符会返回-1
    if(list[i].indexOf(keyWord)>=0){
        arr.push(list[i]);
    }
}
return arr;

//正则表达式
var len = list.length;
var arr = [];
var reg = new RegExp(keyWord);
for(var i=0;i<len;i++){
    //如果字符串中不包含目标字符会返回-1
    if(list[i].match(reg)){
        arr.push(list[i]);
    }
}
return arr;
```

```js
/**
* @param {Object} lists 所有数据
* @param {Object} keyWord 查询的关键词
*/
selectMatchItem(lists, keyWord) {
    let resArr = [];
    lists.filter(item => {
        for(let i in item){
            if (item[i].includes(keyWord)) {
                resArr.push(item);
            }
        }
    })
    return resArr;
},
// 函数执行 在 “staff” 对象中查找 包含 “coot” 的数据。
this.selectMatchItem(staff,'coot')
```

