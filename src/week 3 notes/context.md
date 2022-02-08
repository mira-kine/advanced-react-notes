# Lecture 02.07.2022

## Passing data deeply with context

### "Lifting state up" -> "Prop drilling"

- when there are more than one levels that props need to go through to get state from main, it's called prop drilling
- its inefficient because everytime a main state is updated, the whole tree will get rendered regardless of whether it's actually using the prop or not
- An alternative to passing props is **context**

### Context

- Context lets a parent- no matter distance- provide some data to the entire tree inside of it. Goes directly to the components that need it
- There can be more than one context passed down
- createContext() creates a new context, match the name with the context you are creating for ex.
  - itll have Provider and Consumer (we don't use Consumer as much)
  - Provider value's will hold the state that you want to be passing down to whatever components you will eventually wrap it around

## **Steps to create context:**

1. create context
2. create provider -> often times when context isn't working, there is an issue with the provider
3. return the Provider component with a prop name value.
   - the value prop is the value of the context aka the state that you want to share with this context
   - within value, you are creating a new object (that has a key and a value, object short notationed as {{ entries, setEntries }} for example)

```
const EntryContext = createContext()
const EntryProvider = ({ children }) => {
    const [entries, setEntries] = useState([])
    return <EntryContext.Provider value={{ entries, setEntries }}>{children}</EntryContext.Provider>
}
```

- ^ after we create the provider component, that is what we use to wrap the other components we will be giving context to.

4. create a custom hook -> optional, but it is the recommended way because you give a way to access the context values without exposing the actual context. As long as you have the word "use" you can call what comes afterwards whatever you want
5. call useContext with the context we want to use (so in this case, EntryContext)
6. export provider and the custom hook
7. Then you can wrap whatever components you need to provide context down to using the EntryProvider provider component you created
8. as a beginner, you can wrap your whole app at the root level with your UserProvider. This <App /> is usually found in index.jsx

```
const useEntries = () => {
    const context = useContext(EntryContext)

    if(context === undefined) {
        throw new Error('useEntries must be defined within an EntryContext Provider)
        // here, context is an object that has entries: [] and setEntries f(). This means that both will be accessible throughout whatever components you wrap the provider with
    }
    return context
}
export { EntryProvider, useEntries }
}
```