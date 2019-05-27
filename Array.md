# 数组相关方法总结

### forEach 和 map

相同点：
        1.第一个参数：callback
                都为数组中的每个元素执行所提供的函数，提供的函数*callback*都接受三个参数，包含*currentValue*，*index*，*array*;
        2.第二个参数: thisArg(可选) 
                执行 callback 函数时使用的this 值。
        3. 都不会改变原数组

不同点：
        1. 返回值不同 forEach返回值为undfined 而 map返回一个新数组

        2. forEach 没有办法中止或者跳出 forEach() 循环，除了抛出一个异常 不可链式调用 而map可以
