# JSX Interpolacion

Podemos interpolar gracias a los template literals para poder aplicar valores dinámicos.

También interpolar directamente gracias a los curly braces {} nuestras variables.

```js
<script type="text/babel">
    const rootElement = document.getElementById("root");
    //the text Hello World tiene 11 characters
    //the text "" has No tiene characters
    function CharacterCount({ text }) {
      const length = text.length ? text.length : "no";
      return (
        <div>
          {`the text "${text}" has`} <strong>{length}</strong> characters
        </div>
      );
    }

    const element = (
      <>
        <CharacterCount text="Hello World" />
        <CharacterCount text="" />
      </>
    );

    ReactDOM.render(element, rootElement);
</script>
```

**Cuando se escribe React, se cambia regularmente entre JSX y JS. Las expresiones de JavaScript se pueden escribir dentro de JSX usando llaves**

A qué se reducen las expresiones de JavaScript dentro de JSX. El JSX:

```js
function CharacterCount({text}) {
 return (
   <div>
     {`The text "${text}" has `}
     {text.length ? <strong>{text.length}</strong> : 'No'}
     {' characters'}
 )
}
```

El compilado JavaScript

```js
 function Character Count(_ref) {
   var text = _ref.text;
   return React.createElement("div", null,
   "The text \"".concat(text,"\" has "),
 text.length ? React.createElement("strong", null,
 text.length) : 'No' ' characters')
   ;
 }
```

1- Tenemos props syntax
2- children sintaxis
3- Closing tag

Terminado el div tenemos js de nuevo y en los curly brackets, también dentro de la expresiones podemos hacer for loops, if statement o una expresión, que js evalue su valor

**Pasamos el el statement como argumento**

React.createElement("div", null, if(statement) {})

no hace setido pasar un statement como argumento a una función esa es la razón que los {} curly brackets dentro de jsx, por que curly brackets básicamente le dice hey babel tu obtienes esta parte, todo entre estos 2 curly brackets y justo en este statement de createElement call(el tercer argumento recordemos que primero es el elemento del dom, luego las props) es bueno entender como babel compila jsx puede ayudar usar tu jsx mas efectivo

Tenemos los curly brackets pero dentro volvemos a jsx de nuevo en el ejemplo de el ternario tenemos elementos html para el Render

```js
function CharacterCount({ text }) {
  //js
  return (
    <div>
      {/*js*/ `the text "${text}" has `}{" "}
      {text.length ? <strong>text.length </strong> : "No"} {`characters`}
    </div>
    //js
  );
}
```

Tenemos js luego vamos dentro de jsx es muy comun entre js y jsx la interpolación

Javascript ademas tiene interpolación si hablamos de template literals aquí tenemos templete literal:

```js
{
  /*js*/ `the text "${text}" has `;
}
{
  (" ");
}
```
