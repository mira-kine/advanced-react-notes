# Lecture 1.26.2022 - Mock Service Worker (MSW)

## HTTP Requests Review

- client side goes to site, makes api request --> http request --> serverside runs a code --> response --> back to client side as [{data:results}]
- what happens if API data base is down?

## Mock Service Worker Purpose

- you create a mock API database that mocks the data base you will actually be using
  - this way if the database is down, your test can still work
- mock service worker interrupts the http request, so that the response is sent back from the mock service worker rather than the API

## How to set up MSW

1. import {rest} from 'msw' and {setupServer} from 'msw/node - rest is for REST API -> what we are using to communicate with API for now
2. set up a const server = setupServer()
3. use rest.httpsVerb for ex rest.get()
4. first argument for your verb is api end point (for ex. api's url)
5. second argument is a call back function () with **three arguments: req, res, ctx** - **req(request)** - to get request data - **res(response)** - mimic api response -> this is a function. It is what we will call. we will give it ctx - **ctx (context)** - mimic the json sent from the response -> uses the same .json() method that our call uses in the api response (not the mock one) - **IN THIS ORDER** variable name does not matter, but order does
6. return your response that takes your mock json object as argument
   - for ex res(ctx.json(mockResponse))
     -when you console log your fetch call, the object you receive is what you want to mimic in your .json() in your msw. You can also use postman or look in the network tab to get your data - for ex: const mockResponse = [{id: 1, pokemon: pikachu}]
7. put a **beforeAll(() => {})** and **afterAll(() => {})** before the actual test
   - beforeAll(() => server.listen()) runs before all tests
   - afterAll(() => server.close()) runs after all tests
8. if you want to check that your function is running, put a console.log in your actual api call back function

### MSW code example

```
const server = setupServer(rest.get(`api url`, (req, res, ctx) => {
    return res(ctx.json(mockResponse))
}))

beforeAll(() => server.listen())
afterAll(() => server.close())
```

### Cool things Vonta teaches

- if you press p you can choose what test you want to run in the terminal
