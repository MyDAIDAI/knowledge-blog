---
UID: 20230516162437 
aliases: 
tags: React
source: 
cssclass: 
created: 2023-05-16
计划时间:
开始时间:
结束时间:
优先级:
---

## CPU瓶颈

主浏览器的刷新频率为60Hz，也就是每`1000ms/60Hz`（16.6ms）刷新一次，我们知道，在浏览器中，[[js线程]] 与[[GUI渲染线程]]是互斥的，不能同时执行 [[2023-05-16#💼 工作记录 WORK]]

也就是说，如果在浏览器的一个刷新周期内，只执行了[[js线程]]，而未执行[[GUI渲染线程]]，那么就会出现页面掉帧现象，造成卡顿

例如下面的🌰

```js
function App() {
  const len = 3000;
  return (
    <ul>
      {Array(len).fill(0).map((_, i) => <li>{i}</li>)}
    </ul>
  );
}

const rootEl = document.querySelector("#root");
ReactDOM.render(<App/>, rootEl);  
```

向页面视图中添加3000个`li`标签，由于页面组件数量过多，脚本时间过长，导致页面掉帧，造成卡顿 #todo/react 【使用16版本的react进行测试】

![[Pasted image 20230516180736.png]]

那如何解决呢？
