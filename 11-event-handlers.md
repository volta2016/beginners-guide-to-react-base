# Event Handlers con react

Nosotros podemos hacer una actualización de nuestro state y un re-render de nuestra app

Tenemos una función lista aquí llamada setState la cual puede actualizar la variable de nuestro state y luego hacer un render de nuestra app, llamando a React.render() en nuestro root de nuevo este no es e típico re-render en nuestra App o el manejo de state en una React App pero esto puede trabajar por nuestro propósito aprendiendo como el evento trabaja en react

```js
function setState(newState) {
  Object.assign(state, newState);
  renderApp();
}
```

Tenemos un button , tenemos el onClick event, que podemos llamar -> esto nos va proporcionar una función y la puedo hacer en linea con un Arrow función nosotros podemos decirle setState

Estamos llamando a function que tenemos aquí

```js
function App() {
  return (
    <div>
      <p>there have been {state.eventCount} events.</p>
      <p>
        <button onClick={() => setState({ eventCount: state.eventCount + 1 })}>
          Click Me
        </button>
      </p>
      <p>You tiped: {state.username}</p>
      <p>
        <input />
      </p>
    </div>
  );
}

function setState(newState) {
  Object.assign(state, newState);
  renderApp();
}
function renderApp() {
  ReactDOM.render(<App />, document.getElementById("root"));
}

renderApp();
```

Con el newState y un objeto -> actualizamos el currentState + 1

También podemos hacer que por medio de un onFocus pueda incrementar

```js
<button
  onFocus={() => setState({ eventCount: state.eventCount + 1 })}
>
```

OnMouseOver={} -> para que cuando pase por encima también cambie

Tenemos un serie de eventos que podemos documentarnos en siguiente link:

[event react js](https://reactjs.org/docs/events.html#supported-events)

De esta forma separamos al lógica y actualizamos nuestro state

```js
<script type="text/babel">
      const state = { eventCount: 0, username: "" };

      function App() {
        function handleClick() {
          setState({ eventCount: state.eventCount + 1 });
        }

        return (
          <div>
            <p>there have been {state.eventCount} events.</p>
            <p>
              <button onClick={handleClick}>Click Me</button>
            </p>
            <p>You tiped: {state.username}</p>
            <p>
              <input />
            </p>
          </div>
        );
      }

      function setState(newState) {
        Object.assign(state, newState);
        renderApp();
      }

      function renderApp() {
        ReactDOM.render(<App />, document.getElementById("root"));
      }

      renderApp();
    </script>
```

Ahora miremos este input queremos que esto cuando tapiemos obtenga la actualización cuando entre algún nuevo username

Cuando lleno el input con un valué se actualiza al aplicar Tab gracias al onBlur

```js
<input onBlur={(event) => setState({ username: event.target.value })} />
```

Con elemento onChange se va actualizar mientras escribo o detecte un cambio en el input

```js
<input onChange={(event) => setState({ username: event.target.value })} />
```

Ahora separamos el code nuestro evento

```js
<script type="text/babel">
      const state = { eventCount: 0, username: "" };

      function App() {
        function handleClick() {
          setState({ eventCount: state.eventCount + 1 });
        }


        return (
          <div>
            <p>there have been {state.eventCount} events.</p>
            <p>
              <button onClick={handleClick}>Click Me</button>
            </p>
            <p>You tiped: {state.username}</p>
            <p>
              <input
                onChange={(event) => setState({ username: event.target.value })}
              />
            </p>
          </div>
        );
      }

      function setState(newState) {
        Object.assign(state, newState);
        renderApp();
      }

      function renderApp() {
        ReactDOM.render(<App />, document.getElementById("root"));
      }

      renderApp();
    </script>
```

Si pasamos esto a nuestra función

```js
function handleChange(event) {
  console.log(event);
  setState({ username: event.target.value });
}
```

Si tapiamos vamos que tenemos un nativeEvent
Tenemos un syntheticEvent object aquí, esto no es un nativeEvent, el nativeEvent : inputEvent es el evento del input, react tiene un serie performance y optimizacion para nuestros eventos
