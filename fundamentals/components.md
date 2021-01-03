# React

- anything in the return will be rendered onto the page
- functions for components need an initial capital (HelloWorld)
- new functions need to be declared in the index.js ReactDom render
- rsc extension is clutch
- class should be rewritten as className
- arrays need curly brackets around straight brackets
- vanilla javascript can be written in curly brackets (most of the time)

## How to Setup & Make Things Appear on the Screen:

1. Create a new .js file
2. Use src to make it import React

    ```jsx
    import React from 'react';

    const Movie = () => {
      return (
        <div>
          
        </div>
      );
    };

    export default Movie;
    ```

3. Import new file to App.js

    ```jsx
    import Movie from './Movie'
    ```

4. Enter page contents into return( ) section of const
5. Enter parameter (usually *props*) into const variable 
6. If an object is already declared, you can call specific values to display (won't show up if you didn't link files to import them)

    ```jsx
    <div className="movie">
        <h2>{props.title}</h2>
        <img
          src={props.image}
          alt="movie poster"
        />
        <p>
          {props.summary}
        </p>
      </div>
    ```

7. In "App.js" in the const App return function you can enter a JSX Element which will display everything inside of the linked .js file of the same name(if there are multiple things they need to be wrapped in a tag, usually a *div*)

    ```jsx
    const App = () => {
      return (
      <div>
        <Movies />
      </div>
      );
    };
    ```

8. Each specific element in the .js file needs to be called individually as an object or specific value with dot notation(they can be bunched together in a larger object)

    ```jsx
    const App = () => {
      return (
      <div>
        <Movies movie={movie}/>
      </div>
      );
    };
    ```

9. In order to iterate over something to display multiples of a large object you can use the HoF of .map( )
    - be careful of syntax and calling the correct key value pairs depending on how your pages are linked

    ```jsx
    {props.movies.map((movie) => (
          <Movie
            key={movie.id}
            title={movie.title}
            summary={movie.summary}
            image={movie.poster}
          />
          ))}
    ```

The warning of: 

"Each child in a list should have a unique "key" prop"

is because React likes unique id's

## **Components Summarized**

There are a few things we have to remember when creating components in React.

- All component files **must** import React.
- Function components must return **a single element**. Sibling elements must be contained in a single outer wrapping element.
- They always receive one argument (a **props object**).
- Components are named with an **initial cap**.
- You can surround any return value in parenthesis to break it on to multiple lines.
- To import a custom component, use the relative path to the file. All component imports must start with `./` to reference the current directory, or `../` to reference a parent directory.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7071b9f3-4fea-4e96-a686-adbc3649282c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7071b9f3-4fea-4e96-a686-adbc3649282c/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/103ecb27-b37a-4ee4-9574-258850c207d9/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/103ecb27-b37a-4ee4-9574-258850c207d9/Untitled.png)