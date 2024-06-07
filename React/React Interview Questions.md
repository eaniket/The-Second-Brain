1. React allows server-side rendering, makes use of virtual DOM rather than real DOM as real DOM manipulation is expensive.
2. React is a library. It provides tools for component reusablity, unlike strictness of framework for a fixed structure.
3. Don't use keys in list in react -> Why?
4. Class component vs functional component
5. Controlled Component vs Uncontrolled Component
6. **Props are read-only. They cannot be manipulated or changed inside a component.**
7. Create your own ErrorBoundary Component
8. Rules for using a hook
   -  React Hooks must be called only at the top level. It is not allowed to call them inside the nested functions, loops, or conditions. 
   - It is allowed to call the Hooks only from the React Function Components.
9. **useRefs**: Refs are used for
   - Managing focus, media playback, or text selection. 
   - Integrating with DOM libraries by third-party. 
   - Triggering the imperative animations.
10.  How to prevent re-renders in React?
	1. using shouldComponentUpdate in static class Components
	2. using React.memo and React.PureComponent for functional components
11. Ways to optimise React app:
	1. using useMemo()
	2. using React.PureComponent in class based components
	3. mainitaining state colocation: moving state as close as possible to the required component
	4. lazy loading
12. Pass data b/w:
	1. **Parent -> Child: use props**
	   ```JS
	   //Parent Component:
	   import ChildComponent from './Child';
	   const ParentComponent = (props) => {
		   let [count, setCount] = useState(0);
		   let increement = () => setCount(++count);
		   return(
			   <div>
				   <button onClick={increement}>Increement Button</button>
				   <ChildComponent counterValue={count}/>
		   );
	   }

	   //Child Component
	   const ChildComponent = (props) => {
		   return (
			   <div>
				   <p> Value of counter: {props.count} </p>
				</div>
		   );
	   };
```
	2. **Child->Parent: use emit events(callbacks)**
	   ```JS
	   //Parent Component:
	   import ChildComponent from './Child';
	   const ParentComponent = (props) => {
		   let [count, setCount] = useState(0);
		   let callback = valueFromChild => setCount(valueFromChild);
		   return(
			   <div>
				   <p>Value from Counter:{count}</p>
				   <ChildComponent callbackFunc = {callback} counterValue={count}/>
		   );
	   }

	   //Child Component
	   const ChildComponent = (props) => {
		   let childCounterValue = props.counterValue
		   return (
			   <div>
				   <button onClick={()=>{props.callbackFunc(++childCounterValue)}}>Increement Button</button>
				</div>
		   );
	   };
```
13. Implement HOC: Example - Commonly used for cross-cutting concerns like logging, context, subscriptions, and more
    ```JS
    // withLogging.js
import React, { useEffect } from 'react';

function withLogging(WrappedComponent) {
  return function WithLogging(props) {
    useEffect(() => {
      console.log(`${WrappedComponent.name} mounted`);

      return () => {
        console.log(`${WrappedComponent.name} unmounted`);
      };
    }, []);

    return <WrappedComponent {...props} />;
  };
}

export default withLogging;

// MyComponent.js
import React from 'react';

function MyComponent() {
  return <div>My Component</div>;
}

export default MyComponent;

// App.js
import React from 'react';
import withLogging from './withLogging';
import MyComponent from './MyComponent';

const MyComponentWithLogging = withLogging(MyComponent);

function App() {
  return (
    <div>
      <MyComponentWithLogging />
    </div>
  );
}

export default App;
```
14. React lifecycles phases and methods\
15. Does React Hook work with static typing?
16. How does the performance of using Hooks will differ in comparison with the classes?
17. Conditional rendering in react.
18. Switching component.
19. How to re-render the view when the browser is resized?
    ```JS
    // useWindowSize hook
	import { useState, useEffect } from 'react';

	const useWindowSize = () => {
	  const [windowSize, setWindowSize] = useState({
	    width: window.innerWidth,
	    height: window.innerHeight
	  });
	
	  useEffect(() => {
	    const handleResize = () => {
	      setWindowSize({
	        width: window.innerWidth,
	        height: window.innerHeight
	      });
	    };
	
	    window.addEventListener('resize', handleResize);
	
	    // Clean up the event listener on component unmount
	    return () => {
	      window.removeEventListener('resize', handleResize);
	    };
	  }, []);

	  return windowSize;
	};

	export default useWindowSize;

	//Main Component
	import React from 'react';
	import useWindowSize from './useWindowSize';
	
	const ResizableComponent = () => {
	  const { width, height } = useWindowSize();
	
	  return (
	    <div>
	      <h1>Window Size</h1>
	      <p>Width: {width}px</p>
	      <p>Height: {height}px</p>
	      {/* Your component rendering logic */}
	    </div>
	  );
	};
	
	export default ResizableComponent;
```

20. How to pass data between sibling components using React router?
	 Using history.push and match.params, read about implementation.
21. **Flux** will keep data uni-directional in react.
22. Webpack