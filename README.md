## What is state?

Any data that changes over time.

## How is state declared in a React component?

```jsx
import { useState } from "react"

const SomeComponent = () => {
  const [data, setData] = useState(initialValue)
  return ()
}
```

```jsx
class SomeComponent extends Component {
  state = {
    data: initialValue,
  }

  someMethod = () => {
    this.setState({
      data: newValue,
    })
  }

  render(){
    return (
      <p>Hi</p>
    )
  }
}
```

## What is returned from the `useState` hook?

```jsx
import { useState } from "react"

const SomeComponent = () => {
  const [data, setData] = useState(initialValue)

  // Same as...
  const hookTuple = useState(initialValue)
  const data = hookTuple[0]
  const setData = hookTuple[1]

  return ()
}
```

## What is the parameter for the `useState` hook?

Default value

```jsx
import { useState } from "react"

const SomeComponent = () => {
  const [someArray, setSomeArray] = useState([])

  return (
    <ul>
      {someArray.map(someElement => (
        <li>{someElement}</li>
      ))}
    </ul>
  )
}
```

## Why would you pass a function as a component prop?

* Same component, different action/behavior
* Set the state

## Describe how to change state in a parent component from a child component.

* Pass down a state modification function
* Child invokes state modification function
* Can also use the state

```jsx
<CountManager> <---- state needs to live here
  <DisplayCount />
  <IncrementCount /
</CountManager>
```

## What is lifting state?

Moving state to the nearest common ancestor

## How do you handle DOM events in React?

* Use `onClick`, `onChange`, etc.
* Get passed the event

## What is the equivalent of `.addEventListener("click", handler)` in React?

```jsx
<some-element onClick={handler} />
```

## How do you prevent native form submissions in React?

```jsx
event.preventDefault()
```

## How do you get the value of an input from its `change` event?

```jsx
event.target.value
```

## What data type does a event handler take in React?

Function

## Describe derivative state in your own words.

State that is derived from state sent to the component

```jsx
const [population, setPopulation] = useState(0)
const formattedPopulation = `Pop. ${Math.round(population)}`
```

## What's wrong with this code:

```jsx
<button onClick={setCount(count + 1)}>Increment Count</button>
```

```jsx
<button onClick={() => setCount(count + 1)}>Increment Count</button>
```

```jsx
const clickHandler = () => setCount(count + 1)

<button onClick={clickHandler}>Increment Count</button>
```

## What is wrong with this code:

```js
const name = "pikachu"

// Runs when name changes
useEffect(() => {
  if (someOtherConditionIsMet){
    const url = `https://pokeapi.co/api/v2/pokemon/${name}`
    fetch(url)
      .then(response => response.json())
      .then(pokemon => {
        setError(false)
        setPokemon(pokemon)
      }).catch(error => setError(true))
  }
}, [name])

// Runs once
useEffect(() => {
  if (someOtherConditionIsMet){
    const url = `https://pokeapi.co/api/v2/pokemon/${name}`
    fetch(url)
      .then(response => response.json())
      .then(pokemon => {
        setError(false)
        setPokemon(pokemon)
      }).catch(error => setError(true))
  }
}, [])

// Runs every time
if (someOtherConditionIsMet){
  const url = `https://pokeapi.co/api/v2/pokemon/${name}`
  fetch(url)
    .then(response => response.json())
    .then(pokemon => {
      setError(false)
      setPokemon(pokemon)
    }).catch(error => setError(true))
}
```
