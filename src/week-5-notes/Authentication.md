# Authentication and Authorization in Advanced React

## 2.21.2022

### Protected Routes/Private Route

- access the props that are nested within your component, use the prop {children}
- PrivateRoute component checks the context (UserContext) for a user first
- Use a react router dom Route component within it because remember that the Private Route is really just a Route
  - it will go to wherever we specify we want
  - you can spread out the props in an arbitrary name that will collect all the other attributes that were passed through a component into its children - ...rest or ...routeProps

```
// call the render function explicitly
// you can deconstruct your ...rest or your routeProps, and remember this will include location (from where you used useLocation in the view)
<Route {...routeProps} render={({location}) => user ? children :  <Redirect to={{pathname: '/login', state { from: location}} }/>
} />
// if there is no user, go to
>}
>
```

- we are using useLocation instead of useHistory because useHistory depends on where we came from last in order to access the history array, whereas location does not.
- useHistory replace(path, [state]) - (function) replaces the current entry on the history stack
  - for ex. you can destructure {from} from the location.state that's in the Redirect component in the Private Route
  - you can either come from the location.state(location they were at before) OR they can go to login directly - so you can do like const { from } = location.state || { from: { pathname: '/' } }
    history.replace(from.pathname)

## Route render methods

- three Route render methods:
  - <Route component>
    - Component that will render only when the location matches.
    - will create a new React element from the given component -> you will create a new component every render, which means that the existing component will unmount and a new component remount instead of an inline rendering, which means that an existing component is updated
  - <Route render>:
    - inline rendering: you can pass in the function you will call when the location matches. The render prop function has access to all the route props (match, location, history)
  - <Route children> function:
    - sometimes when you need to render whether the location matches or not, you can use the function children prop.
      - children render propr receives all the same route props, except when the route fails to match the URL then match returns null
      - this way you can dynamically adjust UI based on whether or not route matches.
- All three render methods have these three route props:
  - match
  - location
  - history
