# React Forms

By their nature, forms are stateful

They need to remember information that will be submitted to the server for processing

## Steps to creating forms in React

- ***Generic Reusable Pattern Template***

    ```jsx
    import React, { useState } from 'react';

    function LoginForm() {
      const initialState = { username: '', password: '' };
      const [formState, setFormState] = useState(initialState);

      const handleChange = (event) => {
        setFormState({ ...formState, [event.target.id]: event.target.value });
      };

      const handleSubmit = (event) => {
        event.preventDefault();
        // do something with the data in the component state
        console.log(formState);
        // clear the form
        setFormState(initialState);
      };
      // Note that we need to use `htmlFor` instead of `for` in JSX
      return (
        <form onSubmit={handleSubmit}>
          <label htmlFor="username">Username:</label>
          <input
            id="username"
            type="text"
            onChange={handleChange}
            value={formState.username}
          />
          <label htmlFor="password">Password:</label>
          <input
            id="password"
            type="password"
            onChange={handleChange}
            value={formState.password}
          />
          <button type="submit">Login</button>
        </form>
      );
    }
    export default LoginForm;
    ```

1. Start with an object to hold all of the values in the form (convention to use *initialState*) and set initial values to empty strings
    - Example

        Assume we have a wireframe for a form like this:

        [https://media.git.generalassemb.ly/user/17300/files/d85aa680-11e3-11eb-85a5-b64b67088b36](https://media.git.generalassemb.ly/user/17300/files/d85aa680-11e3-11eb-85a5-b64b67088b36)

        ```jsx
        // We could have an object that represents it like this:

        const initialState = {
          issueType: '',
          subject: '',
          message: '',
        };
        const [formState, setFormState] = useState(initialState);
        ```

    ** its possible to set two "initial states" depending on what data you need to collect

2. Build out the basic form with HTML corresponding to data you want to receive
    - Example

        ```jsx
        //...
        return (
          <form>
            <label htmlFor="issueType">Type of Issue:</label>
            <select id="issueType">
              <option value="outage">Service Outage</option>
              <option value="billing">Billing</option>
              <option value="cancel">Cancel Service</option>
            </select>
            <label htmlFor="subject">Subject:</label>
            <input type="text" id="subject" />
            <label htmlFor="message">Message</label>
            <textarea id="message" cols="30" rows="10"></textarea>
            <button type="submit">Send</button>
          </form>
        );
        //...
        ```

    ** in JSX we can't use reserved keywords like *for as* an attribute in our label elements

3. Add the Form Submit Handler (convention to use *handleSubmit*)
    - Example

        ```jsx
        // Event Handler: a callback function to
        // be run when the event is observed
        const handleSubmit = (event) => {
          // we always need to stop the browser
          // from submitting the form or the page
          // will be refreshed.
          event.preventDefault();
          // do something with the data in the component state
          console.log(formState);
          // clear the form
          setFormState(initialState);
        };

        // Event Listener: tells the browser
        // which event to listen for on which
        // element and what to do when the event
        // happens
        <form onSubmit={handleSubmit}>
        ```

4. Connect the form fields to State (using handleChange)
    - this will make the form's fields become controlled and automatically update the state
    - create another event handler to update things on change of value in input fields
    - insert a value inside each
        - ***handleChange function***

            ```jsx
            const handleChange = (event) => {
              setFormState({ ...formState, [event.target.id]: event.target.value });
            };

            // spread syntax will take what was in the initial forms
            // and add new values if necessary from the form
            // e.g. username, password, valid, etc.
            ```

    - insert value and onChange attributes inside each input to ensure that the input updates the *initialState*
        - Example

            ```jsx
            <input type="text" placeholder="Username" id="username" 
            onChange={handleChange} value={formState.username}/>
            ```

### Overly Simplified Spread Syntax

takes the content of an array or an object and places it into a new one

```jsx
// a new object is created
const obj = {
  name: 'Jen',
  pet: {
    name: 'Lady'
  },
  age: 50
}
// takes whats inside old array and adds to it
const obj2 = {...obj, age: 21, city: 'Boston'}
// if the old array has a "key" of the same name, it will update that value
```