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
## Задание 2
Решение:
```js
import React, { Component } from "react";

class Data extends Component {
  state = {
    name: this.props.initialName || "Anonymous",
    clicks: 0,
  };

  componentDidMount() {
    console.log("Setting up observers");
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevProps.count !== this.props.count) {
      console.log(`Count has changed to: ${this.props.count}`);
    }

    if (prevState.clicks !== this.state.clicks) {
      console.log(`Clicks have been updated: ${this.state.clicks}`);
    }
  }

  componentWillUnmount() {
    console.log("Clear observers");
  }

  handleClick = () => {
    this.setState((prevState) => ({ clicks: prevState.clicks + 1 }));
  };

  render() {
    const { name, clicks } = this.state;
    const { count } = this.props;

    return (
      <div>
        <div>Name: {name}</div>
        <div>Count: {count}</div>
        <div>Clicks: {clicks}</div>
        <button onClick={this.handleClick}>Increment Clicks</button>
      </div>
    );
  }
}

export default Data;
```
## Задание 3
Решение:
```js
import React from "react";
import { useSelector } from "react-redux";
import { RootState, LayoutItem } from "./types"; 

interface SliceInfoProps {
  sliceId: number;
}

const SliceInfo = ({ sliceId }: SliceInfoProps) => {
  const customChartName = useSelector((state: RootState) => {
    const layout = state.dashboardLayout.present;

    const matchingItem = Object.values(layout).find(
      (item: LayoutItem) => item.meta.chartId === sliceId
    );

    return matchingItem?.meta.sliceNameOverride || matchingItem?.meta.sliceName || "Unnamed Chart";
  });

  return (
    <div>
      <h1>{customChartName}</h1>
    </div>
  );
};

export default SliceInfo;


```
## Задание 4

```sql
SELECT 
    product_category, 
    SUM(quantity) AS quantity_sum,
    CASE 
        WHEN SUM(quantity) < 50 THEN 'Low Sales'
        WHEN SUM(quantity) BETWEEN 50 AND 100 THEN 'Medium Sales'
        ELSE 'High Sales'
    END AS sales_level
FROM sales
GROUP BY product_category
ORDER BY product_category;

```

## project_Hierarchy
Ссылка
https://codesandbox.io/p/sandbox/vzmj2t
