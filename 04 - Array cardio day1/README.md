# 03 css variables
## 效果
[demo地址](https://ltboy.github.io/JavaScript30/04%20-%20Array%20cardio%20day1/index.html)

## 知识点

### [map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

> var new_array = arr.map(function callback(currentValue[, index[, array]]) {
 // Return element for new_array }[, 
thisArg])  
> 返回新数组  

> callback
生成新数组元素的函数，使用三个参数：  
> - currentValue
callback 数组中正在处理的当前元素。
> - index可选
callback 数组中正在处理的当前元素的索引。
> - array可选
callback  map 方法被调用的数组。  

> thisArg可选
执行 callback 函数时使用的this 值。

### [filter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
> var new_array = arr.filter(callback(element[, index[, array]])[, thisArg])  
> 返回过滤后的新数组 **不改变原数组**

> callback
用来测试数组的每个元素的函数。调用时使用参数 (element, index, array)。
返回true表示保留该元素（通过测试），false则不保留。它接受三个参数：  
> - element
当前在数组中处理的元素。  
> - index可选
正在处理元素在数组中的索引。  
> - array可选
调用了filter的数组。  

> thisArg可选
可选。执行 callback 时的用于 this 的值。


### [sort](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
>  `arr.sort([compareFunction])`  *返回排序后的数组 会改变原数组*  

> 1. 如果 compareFunction(a, b) 小于 0 ，那么 a 会被排列到 b 之前；  
> 2. 如果 compareFunction(a, b) 等于 0 ， a 和 b 的相对位置不变。备注： ECMAScript 标准并不保证这一行为，而且也不是所有浏览器都会遵守（例如 Mozilla 在 2003 年之前的版本）；  
> 3. 如果 compareFunction(a, b) 大于 0 ， b 会被排列到 a 之前。  
> 4. compareFunction(a, b) 必须总是对相同的输入返回相同的比较结果，否则排序的结果将是不确定的。

### [reduce](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

> arr.reduce(callback[, initialValue])   *返回值是累计结果*

> callback 参数  
> - accumulator
累加器累加回调的返回值; 它是上一次调用回调时返回的累积值，或initialValue（见于下方）。  
> - currentValue
数组中正在处理的元素。   
> - currentIndex可选
数组中正在处理的当前元素的索引。 如果提供了initialValue，则索引号为0，否则索引为1。   
> - array可选
调用reduce()的数组   

> initialValue 累计值
