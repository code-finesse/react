## React State

- React is *reactive* not proactive
    - React uses **declarative style** of programming (describing a picture), whereas imperative programming (a set of instructions for painting a picture) is what we were doing before
    - React allows us to design views for each state and it handles efficiently updating and rendering views when our data changes
    - Certain variables will have a specific state which will tell the page how to behave
- Class-based vs. Function Components with Hooks
    - Data can be designated as a state with one of two syntaxes: ES6 class syntax and function components with hooks
    - These notes and instructions will focus on hooks, but there is a LOT of legacy code using classes
    - we use useState hooks because it will update the page for us
        - simply calling a variable and updating it won't change what is displayed on the page

## How to Add State to a Component

1. same setup but with  { useState } in import line
    - this syntax is called destructuring
    - useState contains two elements (the first is the actual state data and the second is a method that allows us to change the data
2. set up values in the function above the return statement

```jsx
function App() {
  const [showing, setShowing] = useState(true);
  return (
```

3. there are various ways to display when the showing state variable evaluates to true

- Use a logical &:

    ```jsx
    return (
      <main>
        {showing && <p>Can you see me now?</p>}
        <button onClick={() => setShowing(!showing)}>Toggle State</button>
      </main>
    );
    ```

- Use a ternay:

    ```jsx
    return <main>{showing ? <p>Can you see me now?</p> : null}</main>;
    ```

- Set an inline style:

    ```jsx
    return (
      <main>
        <p style={{ showing ? display: 'none' : ''}}>Can you see me now?</p>
      </main>
    )
    ```

*inline styles must be passed as javascript objects (not html/css eg. display: 'none'; backgroundColor: 'green')

** if first value is false everything will return as false

## Passing Down State as Props

1. whatever is in the parameters will be used as props

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3bca0c38-1f9b-436f-bb2e-8a1121937ca9/Screen_Shot_2020-10-16_at_12.08.25_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3bca0c38-1f9b-436f-bb2e-8a1121937ca9/Screen_Shot_2020-10-16_at_12.08.25_PM.png)

2. React will take the two values and turn them into objects THEN it will use values from component set to display on screen

3. Use component to display what pieces of the function you want

4. You can pass down functions as props (if applicable)

## Destructuring

- destructuring let's us name parts of an array object so that we don't have to use dot notation
    - destructuring - creates a copy of the variable. Not mutating the original obj

    ```jsx
    const [data, setData] = useState(initialState);
    ```

    - When destructuring, in the example above, 'data' will be the new key in the state, 'setData' will be the method used to update the value inside of 'data', and the useState() function will be destructuring the state while assigning 'data' it's initial value. We can call 'data' and 'setData' whatever we want, but best practice is to follow the structure of a semantic variable name, and then continuing to be semantic by using set[VariableName] as the method to change the value.
    - We should always change state with the related method. For example, to change the value inside of 'data':

        ```jsx
        //always use:
        setData(newDataValue);
        //never use:
        data = newDataValue;
        ```

## Setting Event Listeners in React:

- To set event listeners you use an "onClick" attribute directly in a component/tag. Like using "addEventListener" in vanilla JS, it passes a click event into a callback function. Therefore, it must be set like

```jsx
function myAlert(){
	alert('This is an alert!')
}

<button onClick={myAlert} />
//OR
<button onClick={() => myAlert()} />
//the second approach above would be for when you
//want to pass parameters into the function inside of
//your callback

//if the onClick attribute is set as a function call
//issues will arise as it will call the function when trying
//to assign. for example:

<button onClick={myAlert()} /> //This won't work!
```

## CSS Modules

[https://create-react-app.dev/docs/adding-a-css-modules-stylesheet/](https://create-react-app.dev/docs/adding-a-css-modules-stylesheet/)

[https://create-react-app.dev/docs/adding-a-css-modules-stylesheet/](https://create-react-app.dev/docs/adding-a-css-modules-stylesheet/)