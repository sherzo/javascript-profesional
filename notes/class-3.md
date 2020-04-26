# Clase #3 - Closures

Son funciones que regresan una función o un objeto con funciones que mantienen las variables que fueron declaradas fuera de su scope.

Los **closures** nos sirven para tener algo parecido a variables privadas, característica que no tiene JavaScript por default. Es decir encapsulan variables que no pueden ser modificadas directamente por otros objetos, sólo por funciones pertenecientes al mismo.

```js
// Closures
      // printColor

      // IIFE
      (function() {
        let color = 'green';

        function printColor() {
          console.log(color);
        }

        printColor();
      })();

      // Funciones que regresan funciones
      function makeColorPrinter(color) {
        let colorMessage = `The color is ${color}`;

        return function() {
          console.log(colorMessage);
        };
      }

      let greenColorPrinter = makeColorPrinter('green');
      console.log(greenColorPrinter());

      variables "privadas"
      const counter = {
        count: 3,
      };
      console.log(counter.count);
      counter.count = 99;
      console.log(counter.count);

      function makeCounter(n) {
        let count = n;

        return {
          increase: function() {
            count = count + 1;
          },
          decrease: function() {
            count = count - 1;
          },
          getCount: function() {
            return count;
          },
        };
      }

      let counter = makeCounter(7);

      console.log('The count is:', counter.getCount());
      counter.increase();
      console.log('The count is:', counter.getCount());
      counter.decrease();
      counter.decrease();
      counter.decrease();
      counter.decrease();
      console.log('The count is:', counter.getCount());

      counter.count = 0;
      console.log('The count is:', counter.getCount());
```
