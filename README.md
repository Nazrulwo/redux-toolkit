# redux-toolkit

Install Redux toolkit: npx create-react-app my-redux-app --template redux-typescript

navigate to the project folder: cd my-redux-app

npm start


src/features/counter/counterSlice.ts:
// src/features/counter/counterSlice.ts

import { createSlice } from '@reduxjs/toolkit';

export const counterSlice = createSlice({
  name: 'counter',
  initialState: {
    value: 0,
  },
  reducers: {
    increment: (state) => {
      state.value += 1;
    },
    decrement: (state) => {
      state.value -= 1;
    },
  },
});

export const { increment, decrement } = counterSlice.actions;

export default counterSlice.reducer;


============================


// src/features/counter/Counter.tsx

import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { RootState, increment, decrement } from './counterSlice';

const Counter: React.FC = () => {
  const count = useSelector((state: RootState) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
};

export default Counter;

===============================

src/App.tsx

// src/App.tsx

import React from 'react';
import './App.css';
import Counter from './features/counter/Counter';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <Counter />
      </header>
    </div>
  );
}

export default App;



