# Manipular el DOm con react useRef

El archivo minificado llama vanilla tilt. Vanilla toma el DOM y hace que react cuando el usuario pase mouse over tome el DOM note, nosotros queremos obtener el dom NODE, nosotros queremos obtener esto es el DOM nodo creado por este elemento

```jsx
<div className="tilt-root">
```

**Recuerda que este es react element -> no es el DOM node**

Vamos a usar ref props:

Necesito pasarle una referencia es un objeto que puede ser manipunable

- Paso mi referencia a un elemento de react

```jsx
function Tilt({ children }) {
  const tiltRef = React.useRef();

  return (
    <div ref={tiltRef} className="tilt-root">
      <div className="tilt-child">{children}</div>
    </div>
  );
}
```

tiltRef es un objeto que tiene una actual propiedad, la actual propiedad, es es actual valor para la referencia de este objeto, porque pasamos esta referencia a un div con la prop llamada ref, es la actual propiedad del DOM node que react ha creado para este div

**Interactuar con el dom es un efecto secundario la lógica para esto puede ser useEffect**

```jsx
React.useEffect(() => {
  console.log(tiltRef.current);
});
```

Ahora refrescamos y obtenemos el DOM node, con la propiedad **.current** traemos el elemento y sin esta propiedad el objeto como tal y podemos ver sus propiedades

Elemento:

```jsx
<div class="tilt-root">
  <div class="tilt-child">
    <div class="totally-centered">vanilla-tilt.js</div>
  </div>
</div>
```

Object current:

- {current: div.tilt-root}
  - current: div.tilt-root[[Prototype]]: Object
    - constructor: ƒ Object()hasOwnProperty: ƒ hasOwnProperty()isPrototypeOf: ƒ isPrototypeOf()propertyIsEnumerable: ƒ propertyIsEnumerable()toLocaleString: ƒ toLocaleString()toString: ƒ toString()valueOf: ƒ valueOf()**defineGetter**: ƒ **defineGetter**()**defineSetter**: ƒ **defineSetter**()**lookupGetter**: ƒ **lookupGetter**()**lookupSetter**: ƒ **lookupSetter**()**proto**: (...)get **proto**: ƒ **proto**()set **proto**: ƒ **proto**()

```js
const vanillaTiltOption = {};
```

Acá podemos especificar como queremos traer vanilla tilt para tratar con este DOM node

Para inicializarlo pasamos estos 2 argumentos, ahora tenemos acceso a tildNode y un objeto con las opciones (propiedades) al inicializar vanilla tilt, ahora si damos hover vamos a ver un real cool effect.

VanillaTilt.init(tiltNode, vanillaTiltOptions);

SI damos unclick para el mostrar tilt checbox que puede desmontar el componente desde la pagina removiendo del DOM node.

Todo esto dice que puede que no exista dentro de la pagina pero esto todavía existe en memoria por que ahí esta la referencia para vanilla tilt, lanmentablemente esto podría guiar para la memoria escape si mantenemos montar y desmontar esto de nuevo, vamos a tener un grupo de DOM node configurados alrededor de la memoria que esto no es realmente necesario por el usuario.

Para combatir el problema retornamos una función que puede ser llamada cada vez actualice de nuestro tilt componente

Esto puede remover todas las referencias de nuestro DOM node desde vanilla tilt y escuchadores de event. Acá destruimos e iniciamos con

```js
VanillaTilt.init(tiltNode, vanillaTiltOptions);
return () => {
  tiltNode.VanillaTilt.destroy();
};
```

Entre cada Render de nuestro componente. Vamos añadir una dependencia de array aquí una dependencia para nuestra función porque ninguna de variables puede cambiar en nuestro no necesitamos dependencias, useEffect callback puede cambiar no necesitamos esto para la lista
