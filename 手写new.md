#### 用js写一个new

##### 过程分析：

* **因为 new 的结果是一个新对象，所以在模拟实现的时候，我们也要建立一个新对象，假设这个对象叫 obj，因为 obj 会具有 People 构造函数里的属性，想想经典继
承的例子，我们可以使用 People.apply(obj, arguments)来给 obj 添加新的属性。**
* **原型与原型链，我们知道实例的 __proto__ 属性会指向构造函数的 prototype，也正是因为建立起这样的关系，实例可以访问原型上的属性**

##### 构造函数的实现

* 构造函数无返回值
```javascript
function People(name,age){
  this.name=name;
  this.age=age;
  this.address="北京市"
}
People.prototype.sayName=function(){
  console.log('my name :'+this.name)
}

function _new(){
  var obj=new Object();
  Constructor=[].shift.call(arguments);
  obj._proto_=Constructor.prototype;
  Constructor.apply(obj,arguments);
  return obj;
}
var people1=_new(People,'tony',28);
```

* 构造函数有返回值且为对象
```javascript
function People(name,age){
  this.name=name;
  this.address="北京市"
  return {
    age:age
  }
}

function _new(){
  var obj=new Object();
  Constructor=[].shift.call(arguments);
  obj._proto_=Constructor.prototype;
  var ret=Constructor.apply(obj,arguments);
  return ret;
}
var people1=_new(People,'tony',28);
```

* 构造函数有返回值且不为对象

**此情况和无返回值情况相同直接返回obj**

> 综述上述情况，可得出最终结果：

```javascript
function _new(){
  var obj=new Object();
  Constructor=[].shift.call(arguments);
  obj._proto_=Constructor.prototype;
  var ret=Constructor.apply(obj,arguments);
  return instance of ret=='object'?ret:obj
}
```



