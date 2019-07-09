#### exec 
接受一个字符串为参数，如果匹配到返回一个数组，否则返回null.

匹配时返回结果和match方法不包含g的时候一样，数组第0个元素是匹配到的文本，后面 n 个是对应的 n 个捕获的文本，
最后两个对象是index和input

同时它会在正则实例的lastindex属性指定的位置开始检索字符串，当匹配到相对应的文本后，他将会把正则实例的lastindex属性设置
为匹配文本最后一个字符的下一个位置

有没有 g 标识对单词执行 exec 方法是没有影响的，只是有 g 标识的时候可以反复调用 exec() 方法来遍历字符串中的所有匹配文本。
当 exec() 再也找不到匹配的文本时，它将返回 null，并把 lastIndex 属性重置为 0。

```javascript
var string = "2017.06.27";
var regex2 = /\b(\d+)\b/g;
console.log( regex2.exec(string) );
console.log( regex2.lastIndex);
console.log( regex2.exec(string) );
console.log( regex2.lastIndex);
console.log( regex2.exec(string) );
console.log( regex2.lastIndex);
console.log( regex2.exec(string) );
console.log( regex2.lastIndex);
// => ["2017", "2017", index: 0, input: "2017.06.27"]
// => 4
// => ["06", "06", index: 5, input: "2017.06.27"]
// => 7
// => ["27", "27", index: 8, input: "2017.06.27"]
// => 10
// => null
// => 0
```
