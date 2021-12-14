# Hookflow

## Mount:

- Run Lazy initializaer -> corre una lenta inicialización - Esto es un useState callback

## Render:

- Render -> Luego obtenemos un reader function que finaliza después de la lenta inicialización que es llama es llamada
- React updates DOM
- Cleanup LayoutEffects Nosotros limpiamos el layoutEffects
- Run LayoutEffects Luego nuestro corre nuestro layoutEffects
- Browser pianos screen el navegador pinta nuestras pantallas
- Cleanup Effects limpiamos nuestros efectos
- Run Effects luego corre nuestros efectos

## Unmount:

Cuando el componente es desmontado limpia todo nuestros efectos

![hookflow](image/hookflow.png)
