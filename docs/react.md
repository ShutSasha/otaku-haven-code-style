# React 🌋

[Return to Table of Contents](../README.md)

## Basic conventions

#### Import
> Instead of
```javascript
import * as React from 'react';
```
> Use
```javascript
import React, { useState, Component } from 'react';
```

#### Typed component state for non trivial values
> On the rare occasions where you need to initialize a hook with a null-ish value, you can make use of a generic and pass a union to correctly type your hook. See this instance:
```javascript
interface User = {
  email: string;
  id: string;
}

// the generic is the < >
// the union is the User | null
// together, TypeScript knows, "Ah, user can be User or null".
const [user, setUser] = useState<User | null>(null);
```

#### Extending Component Props
> We recommend using the option with `interface`
> Sometimes you want to take component props declared for one component and extend them to use them on another component. But you might want to modify one or two. Well, remember how we looked at the two ways to type component props, types or interfaces? Depending on which you used determines how you extend the component props. Let’s first look at the way using `type`:
```javascript
type ButtonProps = {
  /** the background color of the button */
  color: string;
  /** the text to show inside the button */
  text: string;
}

type ContainerProps = ButtonProps & {
  /** the height of the container (value used with 'px') */
  height: number;
}

const Container: React.FC<ContainerProps> = ({ color, height, width, text }) => {
  return <div style={{ backgroundColor: color, height: `${height}px` }}>{text}</div>
}
```

> If you declared your props using an `interface`, then we can use the keyword extends to essentially `extend` that interface but make a modification or two:
```javascript
interface ButtonProps {
  /** the background color of the button */
  color: string;
  /** the text to show inside the button */
  text: string;
}

interface ContainerProps extends ButtonProps {
  /** the height of the container (value used with 'px') */
  height: number;
}

const Container: FC<ContainerProps> = ({ color, height, width, text }) => {
  return <div style={{ backgroundColor: color, height: `${height}px` }}>{text}</div>
}
```


## **Working with hooks**

### Try to always move complex mount logic into a dedicated function ✅

> Instead of

```javascript
useEffect(() => {
  getUserData()
    .then()
    .catch()
    // ...another complex logic
}, []);
```

> Just do

```javascript
useEffect(() => {
  // a function with all the mount operations inside
  initializeData();
}, []);
```
#### `NOTE!`
Do not use useEffect quite frequently, since it might significantly slow down the performance of your app as well as lead to some unexpected issues with while re-rendering.
Ideally there should be only one useEffect(() => {}, []) - which is **didMount**

### Try to use useMemo in case you have expensive calculations ✅

```javascript
// runs only once while component`s initialization
const memoizedValue = useMemo(() => expensiveOperation(), []);

// runs every time X or Y get changed 
const memoizedValue = useMemo(() => expensiveOperation(X, Y), [X, Y]);
```

## Communication with your server

None

## **Hacks and tricks**

#### In case you have mapped values and a function that should be passed into each child - use closure and avoid in-line functions. ✅

> Instead of

```javascript
const getSomeValue = (id) => { // some operations }

map(({ id }) => <ChildComponent onGetValue={() => getSomeValue(id)} />)  
```

> Use

```javascript
const getSomeValue = (id) = () => { // some operations }

map(({ id }) => <ChildComponent onGetValue={getSomeValue(id)} />)  
```
