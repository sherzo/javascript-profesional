# Clase #10 - Promesas

Para crear las promesas usamos la clase Promise. El constructor de Promise recibe un sólo argumento, un callback con dos parámetros, resolve y reject. resolve es la función a ejecutar cuando se **resuelve** y **reject** cuando se rechaza.

El async/await es sólo syntax sugar de una promesa, por debajo es exactamente lo mismo.

La clase Promise tiene algunos métodos estáticos bastante útiles:

* Promise.all. Da error si una de las promesas es rechazada.
* Promise.race. Regresa sólo la promesa que se resuelva primero.
