# Use a lazy initializer with useState

```js
function Greetings() {
  const [name, setName] = React.useState(
    window.localStorage.getItem("name" || "")
  ); //obtiene

  console.log("rendered");

  React.useEffect(() => {
    window.localStorage.setItem("name", name); //guarda actualiza
  });

  const handleChange = (event) => setName(event.target.value);

  return (
    <div>
      <form>
        <label htmlFor="name">name:</label>
        <input value={name} onChange={handleChange} id="name" type="text" />
      </form>
      {name ? <strong>Hello {name}</strong> : <p>Please type your name</p>}
    </div>
  );
}
```

Tenemos un inicial render por la consola
nosotros obtenemos un render en a cada rato cuando escribimos en el input.
No necesitamos tener que leer dentro de localStorage a cada rato por un re-render

Eso es realmente costoso por que esta leyendo dentro del localStorage puede ser mas rápido, pero donde nosotros parseamos un JSON grande luego esto podría ser un problema(costoso) -> combate eso con useState tiene una una lazy característica de inicialización. Tu puedes proveer una función como inicial value y la función puede ser llamada para recuperar el valor inicial y la función puede ser llamada cuando realmente sea necesaria usarla para recuperar el valor inicial

```js
const [name, setName] = React.useState(() => {
  console.log("hello");
  return window.localStorage.getItem("name" || "");
}); //obtiene
```

Creamos un arrow función y retornamos el inicialValue podemos hacerla de múltiple linea y que retorne un valor

```js
 <script type="text/babel">
      function Greetings() {
        const [name, setName] = React.useState(() => {
          console.log("hello");
          return window.localStorage.getItem("name" || "");
        }); //obtiene

        console.log("rendered");

        React.useEffect(() => {
          () => window.localStorage.setItem("name", name); //guarda actualiza
        });

        const handleChange = (event) => setName(event.target.value);

        return (
          <div>
            <form>
              <label htmlFor="name">name:</label>
              <input
                value={name}
                onChange={handleChange}
                id="name"
                type="text"
              />
            </form>
            {name ? (
              <strong>Hello {name}</strong>
            ) : (
              <p>Please type your name</p>
            )}
          </div>
        );
      }

      ReactDOM.render(<Greetings />, document.getElementById("root"));
    </script>
```
