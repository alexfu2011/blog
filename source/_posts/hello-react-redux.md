---
title: Hello React Redux
---
React和Redux非常相像，我们先来看React的一段代码：

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

React使用useState生成相关数据和方法。

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

Redux使用useReducer生成相关数据和方法。从以上代码来看Redux可以通过函数返回数据，而且可以根据不提的请求返回不同数据。这个功能得益于dispatch和reducer的巧妙结合。

## 参考
* https://blog.csdn.net/vitaviva/article/details/104508139