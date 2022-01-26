## Lecture 1.26.2022 - Mock Service Worker (MSW)

### HTTP Requests

- client side goes to site, makes api request --> http request --> serverside runs a code --> response --> back to client side as [{data:results}]
- what happens if API data base is down?

### Mock Service Worker

- so you create a mock API database that mocks the data base you will actually be using
- this way if the database is down, your test can still work
- mock service worker interrupts the http request, so that the response is sent back from the mock service worker rather than the API

### how to set up MSW

- import {rest} from 'msw' and {setupServer} from 'msw/node
- rest is for REST API -> what we are using to communicate with API for now
- req(request) - to get request data
- res(response) - mimic api response
- ctx (context) - mimic the json sent from the response
  - IN THIS ORDER. variable name does not matter, but order does

```
// 'rest' is the api endpoint that we want to hit
// use your HTTP verbs so for ex .get
// in the argument of the verb, we get the api
// first argument is api endpoint (like a url), then a call back function
// the call back function auto gets passed 3 arguments: req, res, and ctx
const server = setupServer(rest.get(`api url`, () => {
    return
}))
```
