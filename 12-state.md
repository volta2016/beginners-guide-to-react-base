# Manejo de state

htmlFor=“” -> htmlFor es una instancia del atributo for, pero en jsx sirve para vincular a un input en este caso vinculamos a name

```js
<form>
  <label htmlFor="name">name:</label>
  <input id="name" type="text" />
</form>
```

A menos que se active una repetición y se llame a su función, el DOM no se actualizará

Esto es donde para desencadenar un re render, toda esta función podría ser llamada, luego del name que podría ser configurado en el colectivo de la basura y crear una nueva variable, Intanciando react tiene que ser llamado con react HOOK para la mantención
del state para un componente

Podemos pasarle un default valué o un string vacío a useState

const name = React.useState("");

useState -> retorna un array

Para instanciar y obtener re asignar aquel variable nosotros podemos llamar a setName()

const handleChange = (event) => setName(event.target.value);

Si guardamos esto ahora todo trabaja

Esto seria la base del hook:

```js
const stateArray = React.useState("");
const name = stateArray[0];
const setName = stateArray[1];
```

Desestructurar la matriz del HOOK useState en lugar de usar el índice. Su código será mucho más legible.

Ahora quedaría nuestro code de esta manera:

```js
<script type="text/babel">
      const state = { eventCount: 0, username: "" };

      function Greetings() {
        const [name, setName] = React.useState("");

        const handleChange = (event) => setName(event.target.value);

        return (
          <div>
            <form>
              <label htmlFor="name">name:</label>
              <input onChange={handleChange} id="name" type="text" />
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

usamos el state en un react function component -> usamos useState Hook desde react -> que acepta un inicial value

Cuando nuestro componente Greetings esta en el render inicial va tener el valor que pasamos por defecto y va ser nuestra variable name que es el primer valor del array

const [name, setName] = React.useState("");

La función de actualización de useState activa una reinterpretación. Use esto con eventos para actualizar fácilmente su aplicación

El segundo valor del array es una función actualizadora -> desencadena un re render de todo el function componente.

React.useState() es llamado de nuevo y puede ignorar el inicial value intanciado, obtenemos el valor actual de name nuestro primer parámetro de nuestro hook useState

Puedes llamar a mas de un state si tu lo necesitas para tu componente

Puede ser el valor por default:

- Boolean
- Array
- Object
- Full
