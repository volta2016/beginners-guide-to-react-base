# Side Effects

Para llamar a un sideEffects en react hay que hacer esto usar useEffect
Este es otro HOOK -> esta función puede ser llamada todo el tiempo cuando el componente Greeting es renderiado

Guardamos un valor en localStorage

**window.localStorage.setItem("name", name);**

1- Primer valor el nombre
2- segundo valor la variable el valor

Ahora podemos ver que tenemos guardado el actual valor en el localStorage

Si refresco no tengo la carga del valor name dentro de mi input y el valor en el localStorage fue limpiado

Esto es por que el initialState nuestro state como un string vacío nosotros no tenemos que tomar el valor el localStorage dentro de la cuenta por que tenemos un render corriendo este callback actualizando el localStorage ítem para el name para el nuevo string name vacío

Necesito inicializar el valor cualquiera en el localStorage si hay un string vacío. Aquí nosotros podemos decir

```js
const [name, setName] = React.useState(
  window.localStorage.getItem("name" || "")
);
```

El default valué es un string vacío

Ahora escribimos el nombre en nuestro input y se va actualizando ahora tenemos que **nuestro localStorage tiene persistencia**

Actualizo y sigo teniendo el valor pero el nombre en input se refresca, nosotros en input especificamos el valor de de name

Guardamos y el valor es el mismo que en localStorage en memory para el state de react componente

Refrescamos, nosotros siempre obtenemos el valor desde el desde el localStorage y mantenemos el valor actualizado en el value del input, el localStorage también

Nosotros usamos primero useEffect para actualizar el valor en memoria

```js
React.useEffect(() => {
  window.localStorage.setItem("name", name); //guarda actualiza
});
```

Luego para tener nuestro state inicializado en memoria tiene que ser inicializado el localStorage usando window.localStorage getItem("name" || "")

Y si no hay nada aquí puede inicializar con un “” string vacío por defecto

**Después décimos que el mismo valor de name in memoria nosotros especificamos el valor de de la props value cambiando este input, desde un incontrolado para un controlado input**
