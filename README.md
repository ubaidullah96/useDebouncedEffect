# useDebouncedEffect
How to use debounced effect in react or react native

I have wrote this custom hook where in which I have added the functionality of debounce in react.

First, create a debounced effect custom hook in file useDebouncedEffect.js in your project.

```
import { useEffect } from 'react';

export const useDebouncedEffect = (effect: any, deps: any, delay: any) => {
    useEffect(() => {
        const handler = setTimeout(() => effect(), delay);
        return () => clearTimeout(handler);
    }, [...deps || [], delay]);
};
```

Then, use it inside your component (I am using it in App.js as example)

```
import { useState } from "react";
import { useDebouncedEffect } from "./useDebouncedEffect";

const App = () => {
  const [value, setValue] = useState('')

  useDebouncedEffect(() => {
    // write your code here
    console.log(value)
    
  }, [value], 1000);
  
  const handleChange = (e) => {
    setValue(e.target.value);
  }

  return (
    <button onClick={handleChange}>{value}</button>
  )
}

export default App;
```
