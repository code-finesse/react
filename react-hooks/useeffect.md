- # React useEffect()

- useEffect can be used to update data on the page and change what is displayed  like a hook
- it updates and can be simple like changing parts of components or be complex like fetching data from APIs and updating the contents of the page

## Steps to set up useEffect()

1. Import useEffect next to useState

    ```jsx
    import React, { useState, useEffect } from 'react';
    ```

2. Add useEffect function in page function (below App( ) function, but above page return statement)

    ```jsx
    useEffect(() => {
        effect
        return () => {
            cleanup
        }
        }, [input])

    // this useEffect will fire when the page is loaded or the state is updated 
    // because there is no second argument
        useEffect(() => {
        console.log('hello world')
        console.log('I am going to fire vevery time the page is loaded or state is updated')
        })

    // this useEffect only fires upon page load/component being mounted
    // because there is an empty array as the second argument
        useEffect(() => {
        console.log('I fire upon page load')
    // empty array as the second argument means we only want it to fire once
        }, [])

    useEffect(() => {
        console.log('hello from flavor town')
        // value in the array means that its going to update when that specific piece is being updated
        }, [flavor])

    ```

3. Set up use effect as needed

    (usually invokes a function or changes a state)

- Steps to fetch API data with useEffect( )

# Steps to fetch API data with useEffect( )

1. Set up useEffect( ) on the page
2. Prepare a variable with an initial state that we will update with fetched url

    ```jsx
    // setting useState to empty parens is the easiest (but NOT the only) way 
    // for it to be updated in the future
    const [variable, setVariable] = useState()

    // using a ternary is the easiest (but NOT the only) way 
    // for it to be updated from nothing
    ```

3. Set up a fetch request inside a function

    ```jsx
    function updatePage = {
        fetch(url)
            .then(res => res.json())
            .then(res => {
    // catch JSON data in the setVariable 
    // so that it will update the page
            setVariable(res)
            }
    }
    ```

4. Set up a useEffect function with fetch request function inside

    ```jsx
    // useEffect to fetch API on page load
    useEffect(() => {
        updatePage()
        }, [])
    ```

5. Create logic to make page update with fetch request function (onClick, etc.)

    ```jsx
    return (
        <button onClick={updatePage}>Give Me Something New</button>
    );
    ```

6. If your initial value does not have a way to display in the component (like being left undefined in step 1) best practice is to have a placeholder

    ```jsx
    {variable ? {setVariable} : null}
    {/* this logic reads if variable exists then you should display the variable,
    but if it doesnt yet this should be null */}
    // if something is undefined it is falseyand does not exist
    ```

7. If all is done correctly the page should update through the logic that was set up

- Component Life Cycle

## Component Life Cycle

React components have a few lifestyle methods that we can use to add functionality to our components

They are invoked at points in the "life cycle" depending on what happens and when

Usually happens when something is being mounted or unmounted on the DOM (page is loaded, state is changed, effect happens, etc.)

[https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

There are three types of component lifecycle methods:

**the useEffect() hook gets called inside of the functional component**

**Mounting:** called when a component is created and inserted into the DOM.

```jsx
{/* This only gets fired when this component is mounted */} 
useEffect(() => { 
    console.log('I only get logged when this component mounts') 
}, [])
```

**Updating:** usually triggered by changes in props or state.

```jsx
{/* This will run upon component mounting and every change in state */} 
useEffect(() => { 
    console.log('I get logged on mount and every time I hear state change') 
})
```

**Unmounting:** called when a component is being removed from the DOM.

```jsx
useEffect(() => {
{/* This return will fire when the component gets unmounted*/} 
    return () => { 
        console.log('I get logged when this component unmounts') 
    } 
})
```

### Extra Things

- ternary is basically an if statement in one line for React
- css classes must be added in component .js file (not in component recall of App.js)
- has been blocked by CORS policy error means you need *www.* in web address