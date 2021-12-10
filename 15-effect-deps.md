# Manage the useEffect dependency array

Tenemos useEffects en el render inicial, cada click voy tener otro useEffects, el efecto esta corriendo actualiza el localStorage, para hacer set del name value, esto es un efecto secundario no necesita estar corriendo porque el name value no tiene que cambiar. Nosotros solo tenemos que cambiar sincronizar el localStorage value con el name value nosotros tenemos en memoria para el state de este componente

React useEffects acepta un segundo argumento como una optimización que combate este problema, el segundo argument es un una dependencia de array
[ ]

```js
React.useEffect(() => {
  console.log("greeting useEffects");
  () => window.localStorage.setItem("name", name); //guarda actualiza
}, [name]);
```

Donde tu pasas tu dependencias por tu efecto secundario o side Effects. Esto donde tu pasas cualquiera que tu quieras hacer seguro tu sincronizas el state completo con el state global de nuestra aplicación

En este caso solamente una cosa queremos obtener para sincronizar nuestro state de localStorage con el state de nuestra app es el (value) name. Para nuestra dependencia de array nosotros vamos a proveer el name.

Si grabamos obtenemos que que el saludo es llamado al iniciar por que useEffect, ahora cuando doy click en el button no llama a useEffect podemos verlo en la consola.

Luego cuando actualizo en value del name vamos ver que useEffects es llamado y se ejecuta en la consola por el nombre es cambiado y todo el state global ahora afuera es sincronizado con el state de la App y reactivar va llamar a useEffect callback

se actualiza ya que cambia el valor en el input cuando escribo y este es una dependencia del efecto -> tiene persentencia ademas name en la app

**"Es muy importante
Mantenga su array de dependencia precisa o, de lo contrario, puede perderse la sincronización del estado del mundo con el estado de su aplicación."**

Importante que mantengamos esta lista de dependencia aquí, luego tu podrías estar perdido afuera sincronizando el state del stateglobal que pasa en tu app, usuarios podrían estar perdido al guardar tu trabajo, por ejemplo si eliminamos el name desde el array y guardamos esto

```js
React.useEffect(() => {
  console.log("greeting useEffects");
  () => window.localStorage.setItem("name", name); //guarda actualiza
}, []);
```

No sabemos que efecto se esta ejecutando o actualizando

React.useEffect(() => {
console.log("greeting useEffects");
() => window.localStorage.setItem("name", name); //guarda actualiza
}, [name]);
En cambio si actualizamos el nombre se ejecuta el el efecto secundario ya que ese valor es parte de demencia del array depende de este valor el efecto

Si escribo en el state de mi applicacion veo que state se comienza a actualizar pero no obtiene lo consolé.log()

Si guardo y refresco voy ver que va estar guardo en el input el nombre que anote antes.
El usuario de esta App se encuentra perdido por que ne mi código la propiedad no fue sincronizada con el state de mi aplicación el state global fuera de mi App

La ayuda vacía puede ser un misterio por es eso react Team creo el plugin -> Eslint plugin

La dependencia de array en algunos casos puede ser no necesaria todo depende del programa o contexto, pero en este caso nosotros podemos añadir una simple dependencia de array, con una dependencia que nuestro efecto llama dentro de esto
-> **quiere decir que el efecto depende de este valor, lo llamamos cuando es necesario**
