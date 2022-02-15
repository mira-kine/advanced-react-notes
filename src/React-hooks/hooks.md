# Hooks I've been learning about in advanced react

## useState

## useParams

## useEffect

## custom hooks

- building your own hooks let you extract component logic into reusable functions
  - it uses other react built in hooks into your own custom hook
- when you want to share logic between two js fxns, we extract it to a third function. Remember that both components and Hooks are functions.
  - so you can use custom hooks when you want to remove duplicated logic from two components
  - they do not share state, they reuse "stateful logic" -> like setting up a subscription and remembering the current value, or wanting to keep entries in a guest book of both user and message, etc.)
- remember that you can call useState and useEffect many times in one component because they will be completely independent.
- they only expose certain parts of the total context

### fun websites for custom hooks

- https://nikgraf.github.io/react-hooks/
- https://usehooks.com/
-

## useMemo

- returns a memoized value
  - **memoized** technique for improving performance of recursive algo. Rewrites the recursive algo so that answers to problem are found and are _*stored in an array*_
- useMemo will recompute the memoized value when one of the dependencies has changed, this way it will only render when necessary
- if no array provided, new value will be computed on every render

## useReducer

- an alternative to useState, where it accepts a reducer of type (state, action) => newState and returns the current state paired with a dispatch method (like Redux)
  - preferable to useState if you have complex state logic that involves multiple sub-values or you use it when the next state depends on the previous one.
  - also preferable with managing complex application states aka you can manage state that depends on the value of another state
    - more efficient for components that trigger deep updates because you pass a dispatch down instead of a call back
      - with dispatch, components don't need to rerender unless they also need the application state whereas callbacks will always rerender
- there will always be a "type" bc this hook explains how **action** types describe state changes
- takes a reducer function and the initial state

  - also updates state

    - Action: A JavaScript object with a key of `type` and an optional key of `payload`. The action `type` describes the state change you intend to make. The `payload` is any additional information you need to provide to make that state change (e.g. a new item to add to the list would be in the payload). -> for ex, the payload can be a new item you want to add to a shopping list

    - Dispatch: A function React provides that sends your actions to a reducer function. (updates state)

      - takes in an object, one of which is an action (uses key 'type:')
      - the action types will be stated before, which you can put into a switch case in order to declare what will be returned according to what type you have
      - in your return statement, what will your state look like? (checkout example below)

    - Reducer: A function you write that takes the current state and the incoming action and a returns a new state object.

- reducer function takes two parameters, state and action

### **Reducer function example:**

```
function itemsReducer(items, action) {
  switch (action.type) {
    case 'added': {
      return [
        ...items,
        {
          id: action.id,
          text: action.text,
          done: false,
        },
      ]
    }
    case 'changed': {...}
  }
  case 'deleted': {...}
}
default: {
  throw Error(`Unknown action: ${action.type}`)
}
}
}
```

### **example using dispatch in useReducer hook**

```
export default function Shopping() {
const [items, dispatch] = useReducer(itemsReducer, initialItems)

const handleAddItem = (text) => {
  dispatch({
    type:'added',
    id: items.length + `,
    text
  })
}
}
```

### React Redux

- standalone library used with any UI layer using React, angular, vanilla js, and a few others.
- predictable state container for JS apps to help write apps behave consistently
- manages and centralizes application state -> manages state through a unidirectional data flow model
