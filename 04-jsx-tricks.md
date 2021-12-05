# JSX de manera efectiva con React

Puedes poner valores de Javascirpt dentro de expresiones estan seran evaluadas y resultado es usado en
la actual posición o nuestra UI.

```JS
<script type="text/babel">
  const rootElement = document.getElementById("root");
  const myChidlren = "Hello";
  const worldChild = "world";
  const myClassName = "container";
  const element = <div className={myClassName}>{chidlren}</div>; //this jsx
  ReactDOM.render(element, rootElement);
</script>
```

## Babel

Babel administra compilar bajo javascript que el browser puede ejecutar ciertas tareas usando API de react, entonces
puede interpretar nuestro código jsx y las expresiones ya que luego esto sera compilado.

**Una importante cosa que recordar es que children es una especial props que podría proporcionar como props aquí**

```js
const element = <div className={myClassName} children={chidlren} />;
```

Si pasamos children como props igual vamos a obtener el contenido del hijo dentro del div:

```js
<script type="text/babel">
  const rootElement = document.getElementById("root"); const chidlren = "Hello
  world"; const myClassName = "container"; const element ={" "}
  <div className={myClassName} children={chidlren}></div>; //this jsx ReactDOM.render(element,
  rootElement);
</script>
```

**podemos pasar con un spread nuestras props**

```js
const element = <div {...props} />;
```

Vamos a pasar a children y className como parte de las props:

```js
<script type="text/babel">
  const rootElement = document.getElementById("root"); const children = "Hello
  world"; const className = "container"; const props = {(children, className)};
  const element =
  <div id="app-root" {...props} className="not-container" />; ReactDOM.render(element,
  rootElement);
</script>
```
