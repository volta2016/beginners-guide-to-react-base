# Crear custom HOOK

La lógica que tenemos aquí para almacenar algo del state localStorage y mantener sincronizado podría ser útil en otras áreas
de nuestra app afortunadamente react HOOK es vanilla js, compartiendo que la lógica sencilla, como compartir cualquier
otra lógica en JavaScript, lo que vamos hacer es hacer una función vamos a llamarla

**useLocalStorageState()**

Luego vamos a mover todas estas lineas de código y remplazamos llamando la función

Vamos a cambiar el nombre de name por:

state setState dentro de useState()

```js
const [state, setState] = React.useState(
  () => window.localStorage.getItem("name") || ""
); //obtiene
```

en cambio al obtener ítem con el string name puede hacer mas sentido para el usuario de esta función para proporcionar como un key para localStorage,
ademas puede aceptar como parámetro llamado key, esto llamado como un default value esto puede ser o tener sentido para la gente.
Para proveer ello como un defaultValue, también aceptar otros parámetros, aplicamos un defaultValue como default
params para que sea un string vacío justo en este caso que ellos no quieren proveer y lo remplazamos como un defaultValue

El default value lo podemos remplazar por el string vacío.

El parámetro name lo cambiamos por key:

## old function component:

```js
function Greeting() {
  const [name, setName] = React.useState(
    () => window.localStorage.getItem("name") || ""
  ); //obtiene

  React.useEffect(() => {
    window.localStorage.setItem("name", name); //actualiza guarda
  }, [name]);

  const handleChange = (event) => setName(event.target.value); //actualiza state

  return (
    <div>
      <form>
        <label htmlFor="name">Name: </label>
        <input value={name} onChange={handleChange} id="name" />
      </form>
      {name ? <strong>Hello {name}</strong> : "Please type your name"}
    </div>
  );
}
```

## update function component:

Remplazamos el string name y estamos seguro nosotros de actualizar estos 2 referencias de antiguo state

useLocalStorageState();

voy a necesitar obtener acceso acceso al stateActualizador o setState y el state value este mismo

Así que retornamos:

```js
function useLocalStorageState(key, defaultValue = "") {
  const [state, setState] = React.useState(
    () => window.localStorage.getItem(key) || defaultValue
  ); //obtiene

  React.useEffect(() => {
    window.localStorage.setItem(key, state); //actualiza guarda
  }, [state]);

  return [state, setState];
}
```

Podemos hacer nuestro custom HOOK y tener una similar API para useState ademas es familiar para gente que usa useState, luego llamamos a:

```js
const [name, setName] = useLocalStorageState();
```

Desde useLocalStorageState() y especificamos a name

const [name, setName] = useLocalStorageState("name");

Directamente tenemos un refactor desde el código que tenía antes en el custom función

Una buena convención para llamar a nuestros custom hook es llamarlo por "useNameCusomHook"

```js
<script type="text/babel">
      function useLocalStorageState(key, defaultValue = "") {
        const [state, setState] = React.useState(
          () => window.localStorage.getItem(key) || defaultValue
        ); //obtiene

        React.useEffect(() => {
          window.localStorage.setItem(key, state); //actualiza guarda
        }, [state]);

        return [state, setState];
      }

      function Greeting() {
        const [name, setName] = useLocalStorageState("name");

        const handleChange = (event) => setName(event.target.value); //actualiza state

        return (
          <div>
            <form>
              <label htmlFor="name">Name: </label>
              <input value={name} onChange={handleChange} id="name" />
            </form>
            {name ? <strong>Hello {name}</strong> : "Please type your name"}
          </div>
        );
      }

      function App() {
        const [count, setCount] = React.useState(0);
        return (
          <>
            <button onClick={() => setCount((c) => c + 1)}>{count}</button>
            <Greeting />
          </>
        );
      }

      ReactDOM.render(<App />, document.getElementById("root"));
    </script>
```
