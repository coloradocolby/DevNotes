# Javascript

## Logical And

Using Logical And to your advantage

true && 'Some Age'
returns -> 'Some Age'    (note 'Some Age' is truthy)

true && false
returns -> false

false && true
returns -> false


if first value is true, then if second value is true, **second value** is returned

if first value is false, then false will be returned


## .map()

.map() returns an array, so if you are trying to return its contents from a function, set the .map() equal to a variable and return that.

```
function getOptions(options){
  if (options.length > 0){
    let arr = app.options.map((option, i) => <p key={i}>{option}</p>)
    return arr;
  } else {
    return <p>No options</p>
  }
} 
```

    
## .includes()
  figure out if expenses.description has the text variables string inside of it
  convert both to lowercase
  use .includes


## typeof

typeof startDate !== 'number'
this implies that the user did NOT specify a startDate,
therefore it should automatically be a match since the user must
not want to filter by startDate
