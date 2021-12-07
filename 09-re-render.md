# Re-render a React Application

**El problema de esto que tengo estar actualizando la pagina para ver el tiempo local actualizado**

```js
<script type="text/babel">
  const rootElement = document.getElementById("root"); const time = new
  Date().toLocaleTimeString(); const element = <div>{time}</div>;
  ReactDOM.render(element, rootElement);
</script>
```

Voy a llamar a setInterval para pasarle ticket casa 1 mili segundo

**Ahora vamos como solo se actualiza la expresión {time} y no el div <div>hello</div>**

```js
<script type="text/babel">
  const rootElement = document.getElementById("root");

  function tick() {
    const time = new Date().toLocaleTimeString();

    const element = (
      <div>
        <div>hello</div>
        {time}
      </div>
    );

    ReactDOM.render(element, rootElement);
  }
  tick();
  setInterval(tick, 1000);
</script>
```

Ahora vamos a ver como se hace un Render de toda nuestra App, acá esta inyectando nuestro elemento pero hace un re Render de toda nuestra App esto no es lo mas óptimo por causa de una paraje de problemas

Ahora tenemos 2 input aquellos se están actualizando cada segundo, pero cuando estoy en el Focus del input comienza de nuevo y me saca del el input

```js
<script type="text/babel">
      const rootElement = document.getElementById("root");

      function tick() {
        const time = new Date().toLocaleTimeString();

        const element = `
          <div>
            <div>hello</div>
            <input value="${time}" />
            <input value="${time}" />
          </div>
        `;
        rootElement.innerHTML = element;
        // ReactDOM.render(element, rootElement);
      }

      // tick();
      setInterval(tick, 1000);
    </script>
```

## React no tiene este problema

Ahora volvemos y todo esto obtiene un actualización pero el valor solamente se actualiza en nuestra app, tenemos ambos valor actualizados para nuestros inputs, pero no un re Render de nuestro div #root o la App por completa

## Esto ayuda para:

1-El performance de nuestra app
2- La accesibilidad > ya que recae mantiene nuestro Focus en nuestro input (independiente a que el valué del input es actualizado)

React hace el re Render por ti pero solo actualiza lo necesario, react va a comparar los elementos por ti y va retornar el tiempo actualizado de estos 2 elementos del DOM actualiza lo que es diferente al ultimo tiempo y retorna JSX

```js
<script type="text/babel">
  const rootElement = document.getElementById("root");

  function tick() {
    const time = new Date().toLocaleTimeString();

    const element = (
      <div>
        <div>hello</div>
        <input value={time} />
        <input value={time} />
      </div>
    );

    ReactDOM.render(element, rootElement);
  }

  // tick();
  setInterval(tick, 1000);
</script>
```
