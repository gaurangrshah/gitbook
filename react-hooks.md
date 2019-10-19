---
description: 'useState():: Update Object State Value'
---

# React Hooks:

```jsx
  const [values, setValues] = useState(initialState);
  const updateValue = e => {
    let [name, value] = e.target;
    console.log(setValues({ ...values, [name]: value }));
  };
```

