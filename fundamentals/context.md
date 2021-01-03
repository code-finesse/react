- Copy and Paste Code
    - Context.js

        ```jsx
        import { createContext } from 'react'

        export const TokenContext = createContext(null)
        ```

    - App.js

        ```jsx
        import React, { useState, useEffect } from 'react'
        import './App.css';
        import axios from 'axios'
        import Page from './components/Page'

        import { TokenContext } from './TokenContext'

        function App() {
          const [job, setJob] = useState('')

          useEffect(() => {
            const url = 'http://localhost:4000/api/jobs/';
            
            fetch(url)
              .then(res => res.json())
              .then(res => setJob(res))
              
          }, [])

          return (
            <div className="App">
              <TokenContext.Provider value={job}>
                <Page />
              </TokenContext.Provider>
            </div>
          );
        }

        export default App;
        ```

    - Page.js

        ```jsx
        import React, { useContext } from 'react';
        import { TokenContext } from '../TokenContext'

        const Page = () => {
          const job = useContext(TokenContext)

          return (
            <div>
              {job?job.map((stuff) => {
                return(
                  <div>
                    {stuff.title}
                    {stuff.description}
                    {stuff.owner.id}
                  </div>
                )
              }) : null}
            </div>
          );
        };

        export default Page;
        ```

# React Context

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a7dac96-5071-45b2-8ced-92120f61b0d5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a7dac96-5071-45b2-8ced-92120f61b0d5/Untitled.png)

- props can only be seen in children components after it is passed down
- context provides a way to share values between components without having to explicitly pass a prop through every level of the tree
- prop drilling is when a prop is passed down through multiple levels of the tree to get to one specific child even if some components will never use it (this should be avoided)
- context will let us store data at the top of our application (not necessarily in App.js) and access it in any place that we want to
- when using context you need at least one Provider component with one or more Consumers
- we can create a special provider component and wrap the parts of the tree that will be communicating with it
- you can have multiple providers in a single app and multiple consumers can have one provider

Steps to set up Context 

1. CREATE PROVIDER
2. create a "UserContext.js" file
    1. import React from 'react'

    ** doesn't need to be called "UserContext" but something with Context is semantic

    ** doesn't need a return function for things on screen

3. create a variable with context

    ```jsx
    const UserContext = React.createContext()
    ```

4. export it from UserContext.js

    ```jsx
    export const UserContext = React.createContext()
    ```

5. import variable of UserContext.js file into App.js

    ```jsx
    import { UserContext } from './UserContext'
    ```

6. put UserContext.Provider into the return statement on App surrounding components you want data to be passed down to
7. give it value that it will share (like props)

    ```jsx
    <UserContext.Provider value={userInfo}>
    ```

8. wrap provider around specific component *you want to send data down to*

    ```jsx
    <UserContext.Provider value={userInfo}>
    	<ComponentA />
    </UserContext.Provider>
    // if you don't give it a value it won't have any data to share
    ```

9. import useContext into specific Component you want to use it in

    ```jsx
    import React, { useContext } from 'react'
    import { UserContext } from './UserContext'
    ```

10. now that variable can be used wherever in the component you have imported it to
- import variable as regular variable

    ```jsx
    const userInfo = useContext(UserContext)
    ```

- import variable as useState

    ```jsx
    const {userInfo, SetUser} = useContext(UserContext)
    ```

### **Summary**

Some general notes about Context:

- Typically, Provider components go at the very top of the tree.
    - React Router's `BrowserRouter` component is a Provider that communicates with all of the `Link`, `Route`, and other components. The `BrowserRouter` sits at the top of the tree.
    - This is not always the case though. For instance, you might create a `Form` component that uses Context to communicate with all of its `Input` elements.
    - *Where you put Providers is dependent upon your specific use case*
- Consumers can only communicate with *one* provider, but one component can have multiple consumers.