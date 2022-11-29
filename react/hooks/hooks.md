<h1 align="center">React hooks 🪝</h1>

Before using the hooks the [caveats of hooks](https://reactjs.org/docs/hooks-rules.html) must be known.

There are various hooks used in React. Here the most commonly used hooks are described

1. [useState](https://reactjs.org/docs/hooks-reference.html#usestate)

   Returns a stateful value (a value that is linked to the render of a component) and a function to change said stateful value

   example:

   ```js
   const [statefulValue, setStatefulValue] = useState(initial value) // initial value can be of any type
   ```

2. [useEffect](https://reactjs.org/docs/hooks-reference.html#useEffect)

   Accepts a function to run based on the changes to the passed dependencies array

   example:

   ```js
   useEffect(()=> {
       console.log('hello') // hello gets printed out whenever change is detected in the dependencies
   }, [statefulValue1, statefulValue2, ...]);
   ```

3. [useContext](https://reactjs.org/docs/hooks-reference.html#usecontext)

   Api provided by react itself to enable sharing of state without having to [prop drill](https://medium.com/analytics-vidhya/props-drilling-in-react-js-934120a4906b)

   It accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context. The current context value is determined by the value prop of the nearest `<MyContext.Provider>` above the calling component in the tree.

   basic usage:

   ```js
   const value = useContext(MyContext);
   ```

   example (with provider):

   ```js
   const themes = {
     light: {
       foreground: "#000000",
       background: "#eeeeee",
     },
     dark: {
       foreground: "#ffffff",
       background: "#222222",
     },
   };

   const ThemeContext = React.createContext(themes.light);

   function App() {
     return (
       <ThemeContext.Provider value={themes.dark}>
         <Toolbar />
       </ThemeContext.Provider>
     );
   }

   function Toolbar(props) {
     return (
       <div>
         <ThemedButton />
       </div>
     );
   }

   function ThemedButton() {
     const theme = useContext(ThemeContext); // consuming the theme context
     return (
       <button
         style={{ background: theme.background, color: theme.foreground }}
       >
         I am styled by theme context!
       </button>
     );
   }
   ```

4. [useCallback](https://reactjs.org/docs/hooks-reference.html#usecallback)
5. [useMemo](https://reactjs.org/docs/hooks-reference.html#usecallback)
6. [useRef](https://reactjs.org/docs/hooks-reference.html#usecallback)

## React 18 concurrency hooks

The concurrency hooks enable developers to make priorities to state updates. For example: developers can prioritize
the changes in form to show immediate feedback to users and the side effect of form data can be pended. Therefore a form
that renders 10000 elements on each change can be made more responsive by rendering the user changes in the form immediately and passes a deffered value (`useDefferedValue`) to show the changes in 10000 elements.

1. [useDefferedValue](https://reactjs.org/docs/hooks-reference.html#usedeferredvalue)
   Accepts a value and returns a new copy of the value that will defer to more urgent updates. It marks the value
   it takes as a less priority state update and lets other state updates to run before it.

example:

```js
const deferredValue = useDeferredValue(value);
```

2. [useTransition](https://reactjs.org/docs/hooks-reference.html#usetransition)
   Returns a stateful value for the pending state of the transition, and a function to start it.

```js
const [isPending, startTransition] = useTransition();
```

```js
startTransition(()=> {...}) // allows to mark the callback passed as a transition
```

`isPending` can be useful to show a fallback UI or a pending state
