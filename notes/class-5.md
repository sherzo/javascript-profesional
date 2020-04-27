# Clase #5 - Los métodos call, apply y bind

Estas funciones nos sirven para establecer el valor de this, es decir cambiar el contexto que se va usar cuando la función sea llamada.

Las funciones **call, apply y bind** son parte del prototipo Function. Toda función usa este prototipo y por lo tanto tiene estas tres funciones.

* **functionName.call().** Ejecuta la función recibiendo como primer argumento el this y los siguientes son los argumentos que recibe la función que llamó a call.

* **functionName.apply().** Ejecuta la función recibiendo como primer argumento el this y como segundo un arreglo con los argumentos que recibe la función que llamó a apply.

* **functionName.bind().** Recibe como primer y único argumento el this. No ejecuta la función, sólo regresa otra función con el nuevo this integrado.

```js
  // Establece `this` usando `call`
  function saludar() {
    console.log(`Hola. Soy ${this.name} ${this.apellido}`);
  }

  const richard = {
    name: 'Richard',
    apellido: 'Kaufman López',
  };

  saludar.call(richard);

  // Establece `this` usando `call` y pasar argumentos a la función
  function caminar(metros, direccion) {
    console.log(`${this.name} camina ${metros} metros hacia ${direccion}.`);
  }

  caminar.call(richard, 400, 'norte');

  // Establece `this` usando `apply` y pasar argumentos a la función
  const valores = [800, 'noreste'];
  caminar.apply(richard, valores);

  /*
    Call - comma
    Apply - arreglo
  */

  // Establecer `this` en una nueva función usando `bind`
  const daniel = { name: 'Daniel', apellido: 'Sánchez' };
  const danielSaluda = saludar.bind(daniel);
  danielSaluda();

  const danielCamina = caminar.bind(daniel, 2000);
  danielCamina('oeste');

  // Cuándo es útil usar uno de estos métodos
  const buttons = document.getElementsByClassName('call-to-action');
  // buttons.forEach(button => {
  //   button.onclick = () => alert('Nunca pares de aprender!');
  // });

  // NodeList
  Array.prototype.forEach.call(buttons, button => {
    button.onclick = () => alert('Nunca pares de aprender!');
  });
```
