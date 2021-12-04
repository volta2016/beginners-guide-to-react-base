## otras formas de llamar al children el contenido

```jsx
const rootElement = document.getElementById("root");
const element = React.createElement("div", {
  children: ["Hello World", "Good Bye World"],
  className: "container",
});
console.log(element);
ReactDOM.render(element, rootElement);
```

```jsx
const rootElement = document.getElementById("root");
const element = React.createElement(
  "div",
  {
    // children: "Hello World",
    className: "container",
  },
  "Hello World",
  "Good Bye World"
);
console.log(element);
ReactDOM.render(element, rootElement);
```
