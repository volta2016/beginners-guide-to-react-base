# JSX

si aplicamos JSX dentro de nuestro documento html

```js
<script type="text/javascript">
  const rootElement = document.getElementById("root");
  <div className="container">Hello Wordl</div>; //this jsx ReactDOM.render(element,
  rootElement);
</script>
```

vemos el siguiente error en consola:

Uncaught SyntaxError: Unexpected token '<'

### para solucionar esto debemos aplicar lo siguiente:

- Cambiar el type del script por el siguiente: <script type="text/babel">

- Debemos agregar babel para que pueda compilar nuestro javacript con la extension JSX y sea intepretado
  por todo los navegadores. Que para hacer uso del debe agregar el script de la pagina llamado @babel/standalone
