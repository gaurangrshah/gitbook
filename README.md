---
description: >-
  Consolidating An Array of Objects to a single object, with only specified
  properties:
---

# Working With Data

```jsx
const views = [
  { id: '1', name: 'title', type: 'text', value: '' },
  { id: '2', name: 'text', type: 'text', value: '' },
  { id: '3', name: 'rate', type: 'number', value: '' },
  { id: '4', name: 'delay', type: 'number', value: '' },
  { id: '5', name: 'emoji', type: 'text', value: '' }
];
```

We'll need to use two different methods to first, return an array of objects, excluding any properties we don't specify.

First use [array.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) to map thru the array and return a new array of objects

```jsx
  const allObjects = views.map(({ name, value }) => ({ 
    [name]: value 
  }));
```

Next we can take the results from the new array of objects, which currently looks like this:

```jsx
// console.log(objects)

[
  { title: '' },
  { text: '' },
  { rate: '' },
  { delay: '' },
  { emoji: '' }
]
```

And we can now create a new object using the Object.assign\(\) method, along with the \(es6\) spread operator:

```jsx
const finalObject = Object.assign({}, ...objects)

console.log(finalObject)
```

Which now gives us the final object with our specified properties and values:

```jsx
{ title: '', text: '', rate: '', delay: '', emoji: '' }
```

Finally, we can abstract this functionality away into a function that does this for us.

```jsx
const newObject = (arrOfObjs) =>  {
  let newArrOfObjs = arrOfObjs.map(({name, value}) => ({
    [name]: value
  }))
  return Object.assign({}, ...newArrOfObjs)
}

console.log(newObject(views)) 

// => { title: '', text: '', rate: '', delay: '', emoji: '' }
```

```jsx
function newObject (arrOfObjs) {
  let newArrOfObjs = arrOfObjs.map(({name, value}) => ({
    [name]: value
  }))
  return Object.assign({}, ...newArrOfObjs)
}

console.log(newObject(views)) 

// => { title: '', text: '', rate: '', delay: '', emoji:
```



