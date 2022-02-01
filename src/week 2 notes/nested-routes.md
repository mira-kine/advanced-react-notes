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
