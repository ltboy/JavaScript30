# 01 - javaScript Drum Kit

## 实现效果：
打击鼓页面，用户通过点击或者键盘输入按钮对应按键播放声音，同时按钮改变状态。  
[在线地址](https://ltboy.github.io/JavaScript30/01%20-%20javaScript%20Drum%20Kit/index.html)

## 关键点
1. 键盘事件
2. 鼠标事件
3. 样式改变
4. 播放声音

## 思路
1. 声音和按钮是一一对应的，原项目使用的是`data-key`来实现对应。但是个人更喜欢采用数组，通过数组下标来进行关联。
2. 声音播放时，按钮样式改变，同时声音响起。因此他们应该属于同一状态。
3. 样式改变，采用的是class的方式，所以需要在改变时移除class。（通过`transitioned`事件）
4. 总体过程：监听键盘和按钮点击事件 >  获取对应的下标 > 执行playing

## 基础知识
### forEach

[forEach文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
基本语法
```JavaScript
array.forEach((currentValue,index,array)=>{},[this])
```

### transitionend事件
[transitionend文档](https://developer.mozilla.org/zh-CN/docs/Web/Events/transitionend)
> 注意事项：  
> 1. transitionend事件在CSS transition结束后触发
> 2. 当transition结束前移除transition,事件不会触发
> 3. 事件完成前元素为`display：none`，也不会触发
> 4. 多个属性进行transition时会触发多次

### bind
[bind文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
[apply文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
[call文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call)  
>1. 三者都可以改变this指向。
>2. bind不会执行函数，因此可以用于指定默认参数 接受多个参数
>3. applay会执行函数 接受2个参数，第一个为this执行，第二个为参数数组
>4. call会执行函数 接受多个参数第一个是this执行，后面为参数

## 难点
### 1. 获取click元素的坐标
柯里化+bind将index传递给playing函数
```javaScript
  keys.forEach((el, i) => {
    el.addEventListener('click', handlClick(i));
    el.addEventListener('transitionend', transitionend);
  })

  function handlClick(inx) {
    return playing.bind(null, inx)
  }
```
### 2. 样式变换后恢复
利用`transitionend`事件。 由于元素涉及多个属性变化会触发多次，所以加个过滤条件 确保只触发一次。
```javaScript
  function transitionend(e) {
    if (e.propertyName !== 'transform') return
    e.target.classList.remove('playing')
  }
```
