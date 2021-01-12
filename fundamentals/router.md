# React Router

- React Router's ***BrowserRouter, Link, Route*** and ***Redirect*** components help to add navigation to a React application
- Allows us to build single-page applications
    - helps us to avoid new page rendering or forwards to other pages, pages slowing down, and displaying components when and how we want to
- Link is like an anchor tag without reloading the page
- React and React Router loads all of the components at once and uses link as a destination

## Steps to set up React Router

Link = sets the url to wherever we want it to go

Route = renders a specified component based on where you are

Redirect = 

1. Install react-router-dom as a dependency in package.json

    ```bash
    npm install react-router-dom
    ```

2. Import dependencies into index.js (or wherever ReactDOM.render is located)
    - this modifies the "root" and lets us see changes to the App, which is now a child component of Router, through React Router (I think)

    ```jsx
    import { BrowserRouter as Router } from "react-router-dom"

    ReactDOM.render(
      <Router>
        <App />
      </Router>,
      document.getElementById("root")
    );

    // you need to wrap the App component in the Router tags
    ```

3. Import Route and Link to top of App.js

    ```jsx
    import { Route, Link } from 'react-router-dom'
    ```

4. Use link and route tags

    ```jsx
    <nav>
    // (wherever we are, we want to go to this landing page)
      <Link to='/wherever'>
        <img
        src="image or logo or whatever"
        alt="semantics save lives"
      />
      <h1>Bitcoin prices</h1>
    </nav>
    <main>
      <Route path='/wherever' exact component={Home}/>
    </main>
    // Route and link should point to same place
    ```

5. Input ***to=*** for where you want to go into first **Link** tag
6. Input ***path=*** for the same place and input ***component={ }*** with component with the same path name into **Route** tag
    - Route path tells the screen to render a certain component when you are in a certain place
    - Exact keyword is optional and will only render the component if the user is in the exact same location as the path that is set
7. OPTIONAL: If you want the page to render something on load use render keyword
    - render means when the path is the same as the url do this function (must use routerProps but not 100% sure of that)

    ```jsx
    // it is optional to use routerProps (render can have any function inside)
    <Route path='/Price/:currency' render={(routerProps) => {
    // when you load the price with the value :currency, display the following things
    // (currency is a variable and only exists because thats 
    // what we called it as in that component)
    return(
      <Price
        price={price}
        setPrice={setPrice}
        match={routerProps.match}
      />
    )
    ```

    ** need to figure out how to explain match easier than below

    - match

![image](https://user-images.githubusercontent.com/71715721/104231914-9a090800-541d-11eb-87af-326722970a75.png)