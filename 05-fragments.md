# Fragments

Recuerda que los elementos de React son expresiones de JavaScript.
Al igual que una función no puede devolver dos valores, o que las variables
no pueden almacenar dos valores, no puedes devolver dos elementos React

hacer esto es imposible:

```js
ReactDOM.render(helloElement, worldElement, document.getElementById("root"));
```

# Option 1:

**Podemos añadir un extra Child element “ ” que sea un espacio para poder separar nuestros 2 elementos creados con createElement() que la llamamos directamente de la API**

```js
<script type="text/babel">
  // const element = <div className="container">Hello world</div>; const
  helloElement = React.createElement("span", null, "Hello"); const worldElement
  = React.createElement("span", null, "World"); const element =
  React.createElement( React.Fragment, null, helloElement, " ", worldElement );
  ReactDOM.render(element, document.getElementById("root"));
</script>
```

## Option 2:

Un patrón común en React es que un componente devuelva múltiples elementos. Los Fragmentos te permiten agrupar una lista de hijos sin agregar nodos extra al DOM.

```jsx
<React.Fragment></React.Fragment>
```

```js
<script type="text/babel">
  const element = (
  <React.Fragment>
    <span>Hello</span> <span>World</span>
  </React.Fragment>
  ); ReactDOM.render(element, document.getElementById("root"));
</script>
```

Use React.Fragment cuando se requiera una estructura DOM específica

## Option 3

Especial sintaxis de React Fragments, eliminamos React.Fragment
Luego añadimos brakets abrimos y cerramos para una correcta sintaxis

```js
<></>
```
