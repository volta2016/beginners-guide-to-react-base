# Entendiendo el React Hook Flow

Aveces podría ser útil tu código va estar corriendo cuando use reactHooks cuando haces una pequeña app que chekiada para mostrar un Child y dentro de esta caja puede hacer un Render cuando esto, el checkbox es cheked luego cuando tu das click dentro de este button va a incrementar el contador

El camino es que creamos un Child componente manteniendo un countState y luego que tienes todo un grupo de useEffect aquí tenemos un simple login aquí cuando el callback es llamado muestra la consola provee y limpia, luego creamos un react element para el render de la pagina, luego tenemos un log ante de finalizar y retornamos el elemento de react creado.
Tenemos nuestra function componente de App excepto aquí donde tenemos nuestro
useState mantenemos showChild boolean state y con useEffect tenemos un Render de elementos de react aquí para hacer Render de la UI.

1- La primera cosa que podemos ver en esta App
-> es el App: Render Start

lo primero que pasa es que react llama a:

```jsx
ReactDOM.render(<App />, document.getElementById("root"));
```

A nuestra App -> llama a nuestro function componente

2- La siguiente cosa que pasa llama a react useState inmediatamente react va llamar a la function, recupera el initialState para mostrar el child state donde el callback es llamado

console.log("%cApp: render start", "color: MediumSpringGreen");

```jsx
const [showChild, setShowChild] = React.useState(() => {
  console.log("%cApp: useState callback", "color: tomato");
  return false;
});
```

3- Luego llamamos a todo los react useEffect avisa que los log aparecen en nuestra consola. Instancia y actualmente crear este elemento

```jsx
 const element = (
          <>
            <label>
              <input
                type="checkbox"
                checked={showChild}
                onChange={(e) => setShowChild(e.target.checked)}
              />{" "}
              show child
            </label>
            <div
              style={{
                padding: 10,
                margin: 10,
                height: 30,
                width: 30,
                border: "solid",
              }}
            >
              {showChild ? <Child /> : null}
            </div>
          </>
        );

        console.log("%cApp: render end", "color: MediumSpringGreen");

        return element;
      }
```

Y obtiene el log para el console de la App cuando el Render termina

Una cosa que pasa es que react actualiza el DOM luego asincronicamente tarde esto va llamar a useEffect callbacks dentro de un tiempo de manera ordenada

No necesitamos limpiar por que no es necesario acá

```jsx
 function App() {
        console.log("%cApp: render start", "color: MediumSpringGreen");

        const [showChild, setShowChild] = React.useState(() => {
          console.log("%cApp: useState callback", "color: tomato");
          return false;
        });

        React.useEffect(() => {
          console.log("%cApp: useEffect no deps", "color: LightCoral");
          return () => {
            console.log(
              "%cApp: useEffect no deps cleanup",
              "color: LightCoral"
            );
          };
    /*….sigue el Code*/
```

Por que acá justo estamos montando el componente y no tenemos que actualiza aún

4-App: useEffect empty deps

Luego tenemos useEffect con la dependencia vacías aquí, tiene una lista de demencias vacía

```jsx
React.useEffect(() => {
  console.log("%cApp: useEffect empty deps", "color: MediumTurquoise");
  return () => {
    console.log(
      "%cApp: useEffect empty deps cleanup",
      "color: MediumTurquoise"
    );
  };
}, []);
```

5- Luego tenemos useEffect con dep y mostramos al componente Child state

```jsx
React.useEffect(() => {
  console.log("%cApp: useEffect with dep", "color: HotPink");
  return () => {
    console.log("%cApp: useEffect with dep cleanup", "color: HotPink");
  };
}, [showChild]);
```

Luego la tenemos aquí

App: useEffect with dep

Ahora vamos a ver que es lo que pasa cuando mostramos al Child recuerda que esta e sea ultima consola que estamos viendo dentro de App component cuando inicializamos nuestro componente

Tengo de nuevo:
App: render start

Esto desencadena dentro de onChange -> esto verifica el valor de nuestro checkbox input

setShowChild:

```jsx
const [showChild, setShowChild] = React.useState(() => {}
```

Va a desencadenar el el re-Render de la App el cual es como obtenemos esto:

![Car Image](image/render-consola1.png)
