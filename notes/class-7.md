# Clase #7 - Herencia Prototipal

Por default los objetos en JavaScript tienen cómo prototipo a **Object** que es el punto de partida de todos los objetos, es el prototipo padre. Object es la raíz de todo, por lo tanto tiene un prototipo padre _undefined_.

Cuando se llama a una función o variable que no se encuentra en el mismo objeto que la llamó, se busca en toda la prototype chain hasta encontrarla o regresar _undefined_.

La función **hasOwnProperty** sirve para verificar si una propiedad es parte del objeto o si viene heredada desde su prototype chain.

```js
function Hero(name) {
  this.name = name;
}

Hero.prototype.saludar = function () {
  console.log(`Hola, soy ${this.name}.`);
};

const zelda = new Hero("Zelda");

// propiedades de la instancia
console.log("Name:", zelda.name);
// propiedades de la "clase"
console.log("Saludar:", zelda.saludar);

// propiedades heredadas ej: toString
console.log("toString:", zelda.toString);

// hasOwnProperty (de dónde sale toString o esto?)
console.log(
  'zelda.hasOwnProperty("saludar"):',
  zelda.hasOwnProperty("saludar")
);

// inspeccionemos el prototipo del zelda
// inspeccionemos el prototipo del Hero
// inspeccionemos el prototipo del Object
```

> > Si un propiedad o método no existe en un objeto este lo buscara en su **prototype** (de quien herda) si no lo encontrace allí lo va a buscar en el **prototype** de dicho **prototype** si no lo encuentra devolvera _undefined_
