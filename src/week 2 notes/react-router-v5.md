# React Router v5

## 1.31.2022

### Routers

- a router component will only render a component that matches the route or it will render null
- the importance of switches -> switch components render the first component that matches the URL path (for ex, after a <Route path="/" />, every other thing that comes after will also match /)

For example:

```
// you exact path the / because that is more universal so you don't want it to render every time a slash exists
<Switch>
    <Route exact path="/">
        <Home/>
    </Route>
    <Route path="/teams/:teamid">
    // :teamid is just a variable with a colon
        <TeamDetail />
    </Route>
</Switch>
```

- question mark (?) means that a query comes afterwards
- when to use a query parameter vs useParams
- what comes after the = is the value that you are searching

### useParams()

- if you console log your params, you can see what params you have access to
- initializer functions so that you can get items from local storage after the initial API call so that you don't have to keep making API calls
- useParams directs you to a new route from the current URL rather than directing the app to a new page/tab
- used for urlparams

### useLocation()

- key is auto generated, path name is what is on your route
- if you check in the prototypes in the console, you can see what functions you have access to

```
const location = useLocation();
const search = location.search (you could also destructure this before and do const { search } = useLocation();)
// use URLSearchParams to grab the keys on our query parameters. The keys were generated from useLocation hook
const searchConference = new URLSearchParams(search);
        --> if you console.log searchConference, you'll get an URLSearchParams object
// grab the specific key you want using the get() method
const conference = searchedConference.get('conference')
```

- key is what is on the left side of the equal sign
- once you have this value (for ex: conference), you can do whatever you want with it for ex use it in your API call
- used for query params, after the questionmark

### useHistory()

- programmatic navigation
  - when you need to wait for some code to run/validation before you redirect for ex a form submission
