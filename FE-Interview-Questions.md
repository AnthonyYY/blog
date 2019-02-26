
> Question: output for following two calling.

``` javascript
const foo = ({save = true, ignored} = {}) => {
  console.log(arguments[0]);
}
foo({save: false});
foo({});
foo();
```

> Answer:

``` shell
{save: false}
{}
undefined
```

