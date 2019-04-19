## JavaScript built-in types (es6)
JavaScript has 7 built-in types, `string` `number` `boolean` `null` `undefined` `symbol` `object`

## All possible return values from `typeof` operator
There are 7 possible return values from `typeof` operator, same count as js built-in types count.
`string` `number` `boolean` `functon` `undefined` `symbol` `object`

`typeof` operator never returns type `null` for null value but instead it returns `object`, this is a bug of javascript and won't be fixed.
`typeof` operator returns `function` if followed by a function even `Function` is not an built-in type of JavaScript. function is `object` type.

## The falsy value of javascript
except type `object` and `symbol`, here is all the falsy value of the rest 5 js built-in types
``` javascript 
"" (string)
0, -0, NaN (number)
null (null)
undefined (undefined)
false (boolean)
```
