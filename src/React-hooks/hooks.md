# Hooks I've been learning about in advanced react

## useState

## useParams

## useEffect

## custom hooks

- building your own hooks let you extract component logic into reusable functions
- when you want to share logic between two js fxns, we extract it to a third function. Remember that both components and Hooks are functions.
  - so you can use custom hooks when you want to remove duplicated logic from two components
  - they do not share state, they reuse "stateful logic" -> like setting up a subscription and remembering the current value, or wanting to keep entries in a guest book of both user and message, etc.)
- remember that you can call useState and useEffect many times in one component because they will be completely independent.
- they only expose certain parts of the total context

## useMemo
