### Object.prototype.toString 才是老大

1. typeof 操作符，对于一些常用的类型，交给它没问题

```
  typeof(123);  // "number"

  typeof(false); // "boolean"

  typeof("string"); // "string"

  typeof(undefined); // "undefined"

  typeof([]); // "object"  无能为力
```

2. instanceof 操作符; 测试构造函数的prototype属性是否出现在对象的原型链中的任何位置。(判断一个实例对象是否由某个构造函数构造而来)

```
  [] instanceof Array; // true
```

3. constructor 属性, 是每一个实例对象都拥有的属性, 并指向于创建当前对象的对象。

```
  [].constructor === Array; // true
```

4. Object.prototype.toString, 是顶层Object.prototype的toString方法, 不是实例的toString方法(Array.toString, Number.toString)

```
 实例化的对象彼此是不共享原型链时
 var iframe = document.createElement('iframe');
 document.body.appendChild(iframe);
 var iframesArray = window.frames[0].Array;

 var arr = new iframesArray(); // []

 arr instanceof Array; // false
 arr.constructor === Array; // false

 Object.prototype.toString.call(arr) // "[object Array]"  闪亮登场

 Array.isArray(arr) // true ES5 的方法，有兼容性
```

###### 一个判断实例是否是数组最佳写法
```
function isArrayFn(val) {
  if (typeof Array.isArray === "function") {
      return Array.isArray(val)
  } else {
    return Object.prototype.toString.call(val) === "[object Array]"
  }
}
```
#### 总结
使用toString()检测对象类型，是比较靠谱的
```
var toString = Object.prototype.toString;

toString.call(undefined); // "[object Undefined]"
toString.call(null); // "[object Null]"
toString.call(new Array) // "[object Array]"
toString.call(new Object) // "[object Object]"
toString.call(new String); // "[object String]"
toString.call(Math); // "[object Math]"
toString.call(new Date); // "[object Date]"
```
