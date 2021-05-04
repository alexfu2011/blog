---
title: Hello Redux-thunk
---
接上文，如果想让dispatch传递一个函数的话，通常是一个异步函数，就需要使用redux-thunk。

```js
const updateData = value => dispatch => {
  dispatch({
    type: 'UPDATE_DATA',
    value,
  });
};
```

这个功能确实扩展了dispatch，我一开始看到这个函数的时候有点疑惑，不过当你掌握了Javascript，就可以当它像下面这段代码执行。

```js
function sleep (time) {
  return new Promise((resolve) => setTimeout(resolve, time));
}

let put = function(value) {
    if (typeof value === "function") {
        value(put, arguments);
    } else {
        console.log(value);
    }
};

let asyncFunc = value => async put => {
  await sleep(3000);
  put(value);
};

put(asyncFunc("hello"));
```