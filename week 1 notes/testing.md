# Notes on testing

## Lecture Notes 01.24.22

- Behavioral testing
  - Testing for function to be working for ex. filtering, ascending, searching, etc.
- Component testing
  - Testing for components, to make sure that things are all being displayed because that is what the user cares about
- Implementation details - SHOULD NOT BE
  - Both the development user and client user do not care about these details
  - What will a random user of my application have no idea about? for ex if you shouldn't be testing to see what state variable changed
  - For ex. testing that an h1 tag is going to show up is implementation, whereas "testing that Alchemy Compendium words show up" is component testing

### Testing terms

- Difference between getBy and findBy
  - findBy is asyncronous -> depends on API action to happen
  - getBy is not asyncronous -> before loading, does not depend on API action/fetching query to happen
- render
  - always import
  - what you call inside your test, it is the component that we want to test on
- screen
  - always import
  - after everything in the component renders into our virtual environment, you can use screen
  - what do you expect to see on the website after that specific component
- expect
  - expect is a function provided by jest

### Accessibility

- Roles are associated with accessibility

  - the order in which you should try to access your element is getByRole, LabelText, PlaceholderText, ByText, DisplayValue.
  - getByRole can be used to access something on the accessibility tree -> accessibility = necessary tools or ways in which websites can be made easier to access to the user with features like buttons, dropdowns, spaces to write text, etc.
  - accessibility tree = subset of the DOM tree that contains accessible objects for every DOM element that should be exposed to assistive technology such as screen readers

- after you decide how you want to access your element, then you can pass in an object to your getBy/findBy/queryBy function with a key in the form of a string or regex (if you use string then it'll be case sensitive) - remember, regex is a sequence of characters that form a search pattern to see if a string contains a specific search pattern or not
- using getAltByText -> the image that shows up in the header for ex. if that alt text shows up then you know that that image is being displayed. This tests to show that the image SHOULD have an alt text
- to check for loading state in your document, you can try something like expect(screen.getByText(/loading/i)).toBeInTheDocument()
- await waitForElementToBeRemoved(() => screen.getByText(/loading/i)) -> you add this line afterwards because you need to tell your test to expect a state update to end the test, and you know that loading will be removed when the API call is successful

- use getAll/findAll when there will be multiple elements rendered and you want to test for them all
- if you use something like await screen.findAllByText(pokemonName, { exact: false}) and you search for charizard, it will make it so that you will get anything that has charizard in it (includes charizard mega-x for example)
- expect(hasSameName).toBe(true) means that you're just testing that the const you created is true
- userEvent.type(searchbar, pokemonName) or userEvent.click(searchButton) tests for the accessibility functions.

- ARIA technology

  - go to dev tools, selector, click on what you want to check under the Accessibility tab. If you click on what you want to test for, you can see what role it has

- screen.debug() AFTER the await because it shows on the console what you are rendering in your testing environment
