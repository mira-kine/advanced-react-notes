# Primitive DS&A 2.22.22

- .split = splits it by letter into an array
- then you can .map through it to return what you want

## Example #1

```
function standardize(sentence) {
    return sentence.split(' ').map(word => {
        return word.padStart(10, 'x')
    })
}
```
