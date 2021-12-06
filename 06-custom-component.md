# Componente re utilizable

Podemos reutilizar componentes dentro de nuestra UI

Option 1:

```js
<script type="text/babel">
  const message = <div className="message">Hello World</div>; const element = (
  <div className="container">
    {message}
    {message}
  </div>
  ); ReactDOM.render(element, document.getElementById("root"));
</script>
```

Option 2:

Pasamos nuestros mensajes por medio de props y tenemos 2 componentes con sus respectivos mensajes

```js
<script type="text/babel">
  const message = (props) => <div className="message">{props.msg}</div>; const
  element = (
  <div className="container">
    {message({ msg: "Hello world" })}
    {message({ msg: "Good Bye World" })}
  </div>
  ); ReactDOM.render(element, document.getElementById("root"));
</script>
```

**Pero esto no es ergonómico no pinta bien**

**Si tu quieres hacer un crear un react componente debe comenzar con upperCase quiere decir con su nombre el primer carácter en mayúscula, le llaman Capital**

<Message></Message>

React.createElement va pasar como primer argumento nuestro **componente**

Podemos crear un componente de react con la funcion para referenciar, así podemos crear nuestro customComponent que podemos re utilizar el código una y otra vez, podemos re escribir usando JSX

Guardamos y vemos que al compilar nuestro código en en el script React.createElement() como primer argumento tiene nuestro Message función

```js
const Message = (props) => <div className="message">{props.msg}</div>;
```

Option 3 :

```js
<script type="text/babel">
  const Message = (props) => <div className="message">{props.msg}</div>; const
  element = (
  <div className="container">
    <Message msg="Hello world" />
    <Message msg="Good Bye World" />
  </div>
  ); console.log(<div>hello world</div>); console.log(<Message>
    Hello World
  </Message>); ReactDOM.render(element, document.getElementById("root"));
</script>
```

Option 4:

O podemos pasarle props children para pasar el contenido directamente dentro del componente o como props de las 2 formas puede consumir el contenido nuestro componente.

```js
<script type="text/babel">
  const Message = (props) => (<div className="message">{props.children}</div>
  ); const element = (<div className="container">
    <Message>children</Message>
    <Message children="Good Bye World" />
  </div>
  ); console.log(<div>hello world</div>); console.log(
  <Message>Hello World</Message>); ReactDOM.render(element, document.getElementById("root"));
</script>
```

Gracias a la función de nuestro componente podemos rehusar multiples código y múltiples lugares

Este seria un custom funtion componente que acepta props object y retorna mas de un react elements
