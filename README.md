# TechAuditBI_FE_Test

## Задание 1
Решение:
```js
const transformationFunc = (data) => {
   return data.map(item=>{
       const obj =  Object.fromEntries(item)
       return {
           label: `${obj.name}, ${obj.age} `,
           value: obj.id
       }
    })
}
const data = [
    [["id", 1], ["name", "Ivan"], ["age", 23]],
    [["id", 2], ["name", "Marina"], ["age", 30]],
    [["id", 3], ["name", "Anna"], ["age", 28]]
];
console.log(transformationFunc(data))
```
