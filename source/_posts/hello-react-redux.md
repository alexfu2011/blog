---
title: Hello React Redux
---
React和Redux非常相像，React可以使用useState和useReducer解决数据和动作的绑定。Redux使用createStore。

useState使用起来比较简单，代码如下：

```js
import React, { useState } from "react";

const ComponentUseState = () => {
  const [num, setNum] = useState(0);

  return (
    <div>
      <h2>Using useState</h2>
      Number: {num}
      <button onClick={() => setNum(num + 1)}>+</button>
      <button onClick={() => setNum(num - 1)}>-</button>
    </div>
  );
};

export default ComponentUseState;
```

以上代码使用useState生成相关数据和方法。useReducer使用起来复杂一些，代码如下：

```js
import React, { useReducer } from 'react'

const initialState = {num: 0};

const reducer = (state, action) => {
  switch(action.type) {
    case 'decrement':
      return {...state, num: state.num - 1}
    case 'increment':
      return {...state, num: state.num + 1}
    default:
      return state;
  }
}

const ComponentUseReducer = () => {
  const [state, dispatch] = useReducer(reducer, initialState)

  const { num } = state
  return (
    <div>
      <h2>Using useReducer</h2>
      Number: {num}
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
    </div>
  );
};
```

以上代码使用useReducer生成相关数据和方法。从以上代码来看，可以通过函数返回数据，而且可以根据不同的请求返回不同数据。这个功能得益于dispatch和reducer的巧妙结合。

```js
import React from "react";
import { createStore } from "redux";
import { Provider, useSelector, useDispatch } from "react-redux";

const initialState = { num: 0 };

const reducer = (state, action) => {
  switch (action.type) {
    case "decrement":
      return { ...state, num: state.num - 1 };
    case "increment":
      return { ...state, num: state.num + 1 };
    default:
    
      return state;
  }
};

const store = createStore(reducer, initialState);

const ComponentUseReactRedux = () => {
  return (
    <div>
      <h2>ComponentUseReactRedux</h2>
      <Provider store={store}>
        <ChildComponentUseReactRedux />
      </Provider>
    </div>
  )
}

const ChildComponentUseReactRedux = () => {
  const num = useSelector(state => state.num);
  const dispatch = useDispatch();
  return (
    <div>
      <h3>Using useSelector, useDispatch</h3>
      Number: {num}
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </div>
  );
};

export default ComponentUseReactRedux;
```
Redux使用createStore，创建一个store对象，它是Redux的核心，通过Provider传递给其他组件，再通过useSelector获取数据和通过useDispatch发送数据。

## 参考
* https://blog.csdn.net/vitaviva/article/details/104508139