# Lecture 2.1.22

## Nested arrays

- for ex, within categories you have more links
- use a nested link that uses the 'url' from 'useRouteMatch'
  - you can map through with destructured items for ex:
  ```
  {movieCategories.map(({category, id}) => {
      return (
          <li key={id}>
          <Link to=`${url/${id}}>{category}</Link>
          </li>
      );
  })}
  ```
- as long as you are within a Router, you can still render a Route
- const { url, path } = useRoutematch()

  - you use url for nested links -> it'll give you whatever is in the address bar
  - use path for nested routes -> shows you how it was put together (for ex, what it matches with like /categories/:categoryId)

  ** side note **

  - remember that a .filter returns an array, .find returns an object (the first one)

## useRouteMatch()

```
const { url, path } = useRouteMatch()
```

- making dynamic links - link goes to a route, and then inside the route you plug in path.

```
<Route path={`${path}/:categoryId`}>
// :categoryId is a URL param
```

- remember, when you "useParams"hook, you are using the param of the current url you are on
- the colon tells you that it is a URL param not a fixed route. Everytime the url changes, the route auto uses it.

## useLocation()

- when you use .get('') you can set it into the URL when you do something like new urlSearchParams

## useHistory()

- history = send with new data/information
- redirect = send them somewhere
