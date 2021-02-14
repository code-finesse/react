```javascript
import React, { useReducer } from 'react';

// this ACTIONS variable will help with keeping code clean and not having random strings everywhere
const ACTIONS = {
    INCREMENT: 'increment',
    DECREMENT: 'decrement',
    RESET: 'reset'
}

// arguments are state (whatever the current state is) and dispatch function
// action is essentially what we call to update our current state
function reducer(state, action) {
    // switch will look for the action type and then do what you want it to depending on that action
    switch (action.type) {
        case ACTIONS.INCREMENT:
            return { count: state.count + 1 };
            break;
        case ACTIONS.DECREMENT:
            return { count: state.count - 1 };
            break;
        case ACTIONS.RESET:
            return { count: state.count = 0 };
            break;
            // default just returns current state for valid action check
        default:
            return state;
    }
}

const Reducer = () => {
	// useReducer variables "state", "dispatch", and "reducer" are always the same
	// last argument of useReducer will be objects that will chnge
	const [state, dispatch] = useReducer(reducer, { count: 0 });

	function increment() {
        // here we pass an object with a type
		dispatch({ type: ACTIONS.INCREMENT})
	}

	function decrement() {
		dispatch({ type: ACTIONS.DECREMENT})
	}

    function reset() {
        dispatch({ type: ACTIONS.RESET})
    }

	return (
		<div>
			<button onClick={decrement}>-</button>
			<span>{state.count}</span>
			<button onClick={increment}>+</button>
            <button onClick={reset}>reset</button>
		</div>
	);
};

export default Reducer;
```
