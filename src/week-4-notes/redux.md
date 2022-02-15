# Redux lecture, 2.15.22

## redux steps

1. create the Redux Store and provide to react
2. create a slice of state
3. add slice Reducer to our store
4. use our dispatch and selector in our component

### Create Redux Store and provide to react

```
<!-- this store will have all the global application state we want -->
export const store = configureStore({
    // then we want an object with a key of reducer on it
    reducer: {},
})
<!-- provide it to react by using a Provider component that takes a prop named store -->
```

### Create a slice of state

```
<!-- Redux makes it so that it seems mutable but it is not. It uses Immer library which detects changes to a "draft state" and produces a brand new immutable state based off those changes. in other words, the slice const itself is not mutable BUT it describes what mutation to the state may happen where it is used -->

export const counterSlice = createSlice({
    name: 'counter',
    initialState: initialCount,
    <!-- initial Count is declared before the function -->
    reducers: {
        increment: (state) => {
            state.count += 1;
        },
        decrement: (state) => {
            state.count -= 1;
        },
    },
})
<!-- define as action -->
export const { increment, decrement } = counterSlice.actions;
<!-- export reducer function from slice -->
export default counterSlice.reducer
```

- side note, += or -= means increment or decrement and then set the new value equal to whatever for ex state.count += 1 means increment by 1 and then set that equal

### Add slice reducer to our store

- make sure your provider wraps the component you need

```
<!-- import _____ reducer from where your slice is. You can name it what you want but convention would be to call it ____Reducer fr ex. counterReducer-->

export const store = configureStore({
    reducer: {
        <!-- name the piece of state and give it the reducer to use -->
        counter: counterReducer
    }
})
```

### Use dispatch and selector in our component

- useSelector hook will grab all the state in our store and set it to a const

```
const count = useSelector((state) => state.counter.count)
const dispatch = useDispatch()

```

- then you will dispatch either increment() or decrement() because those are th eonly ones available in your slice
