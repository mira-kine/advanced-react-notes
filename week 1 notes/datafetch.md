# 1.25.2022

## Data Fetching

### fetch, .then, .finally

- fetch returns a promise
  - promises give us two ways to interact with data
    - .then, or async/await
      - these two can be used interchangeably, but .then is the "older brother" of async/await
- Implicit returns : when you write an arrow function, you need a return. Sometimes, you can use an implicit return where you do not see the return key word but you know that the data after => is a return. You use this when you do not have multiple lines of code within the function
- when you use .then, you are waiting for a promise to resolve

### what is JSON? .json()?

- the data is returned as an object which you can parse in order to manipulate
