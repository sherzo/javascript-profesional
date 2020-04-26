# Clase #2 - Scope

El Scope o ámbito es lo que define el tiempo de vida de una variable, en que partes de nuestro código pueden ser usadas.

## Global Scope

Variables disponibles de forma global se usa la palabra var, son accesibles por todos los scripts que se cargan en la página. Aquí hay mucho riesgo de sobreescritura.

## Function Scope

Variables declaradas dentro de una función sólo visibles dentro de ella misma (incluyendo los argumentos que se pasan a la función).

## Block Scope

Variables definidas dentro de un bloque, por ejemplo variables declaradas dentro un loop while o for. Se usa let y const para declarar este tipo de variables.

## Module Scope

Cuando se denota un script de tipo module con el atributo type="module las variables son limitadas al archivo en el que están declaradas.

```js
    // Global Scope
      // var message = 'Hello, Platzi!';
      // var $ = function(message) {
      //   console.log('Say: ' + message);
      // };

      // Function Scope
      // function printNumbers() {
      //   var i;
      //   for (i = 0; i < 10; i++) {
      //     function eventuallyPrintNumber(n) {
      //       setTimeout(function() {
      //         console.log(n);
      //       }, 100);
      //     }

      //     eventuallyPrintNumber(i);
      //   }
      // }

      // printNumbers();

      // Block Scope
      function printNumbers2() {
        for (let i = 0; i < 10; i++) {
          setTimeout(function() {
            console.log(i);
          }, 100);
        }
      }

      printNumbers2();

      // Module Scope
```
