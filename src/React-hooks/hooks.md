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
