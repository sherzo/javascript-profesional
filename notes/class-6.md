# Clase #6 - Prototype

En Javascript todo son objetos, no tenemos clases, no tenemos ese plano para crear objetos.

Todos los objetos “heredan” de un prototipo que a su vez hereda de otro prototipo y así sucesivamente creando lo que se llama la **prototype chain**.

La keyword new crea un nuevo objeto que “hereda” todas las propiedades del prototype de otro objeto. No confundir prototype con **proto** que es sólo una propiedad en cada instancía que apunta al prototipo del que hereda.

## Un objeto común y corriente

Creamos

```js
const zelda = {
  name: "Zelda",
};

zelda.saludar = function () {
  console.log(`Hola soy ${this.name}`);
};

zelda.saludar();

const link = {
  name: "Link",
};

link.saludar = function () {
  console.log(`Hola soy ${this.name}`);
};

link.saludar();
```

## Seamos un poco más eficientes

```js
function Hero(name) {
  const hero = {
    name: name,
  };

  hero.saludar = function () {
    console.log(`Hola soy ${this.name}`);
  };

  return hero;
}
const zelda = Hero("Zelda");
zelda.saludar();

const link = Hero("Link");
link.saludar();
```

## Aun podemos mejorar más

Así podemos evitar tener que crear la misma función cada vez.

```js
const heroMethods = {
  saludar: function () {
    console.log(`Me llamo ${this.name}`);
  },
};

function Hero(name) {
  const hero = {
    name: name,
  };
  hero.saludar = heroMethods.saludar;
  return hero;
}

const zelda = Hero("Zelda");
zelda.saludar();

const link = Hero("Link");
link.saludar();
```

## Object.create

Con `Object.create` crea un nuevo objeto y este tendrá los metodos de un objeto a `_proto_` del nuevo objeto.

```js
const nuevoObjeto = Object.create(objeto);
const heroMethods = {
  saludar: function () {
    console.log(`Soy superheroe! ${this.name}`);
  },
};

function Hero(name) {
  const hero = Object.create(heroMethods);
  hero.name = name;

  return hero;
}

const zelda = Hero("Zelda");
zelda.saludar();

const link = Hero("Link");
link.saludar();
```

## Los métodos de hero dentro de Hero

```js
const heroMethods = {
  saludar: function () {
    console.log(`Soy superheroe! ${this.name}`);
  },
};

function Hero(name) {
  const hero = Object.create(Hero.prototype);
  hero.name = name;

  return hero;
}

Hero.prototype.saludar = function () {
  console.log(`Soy superheroina! ${this.name}`);
};

const zelda = Hero("Zelda");
zelda.saludar();

const link = Hero("Link");
link.saludar();
```

## Usand new

New realmente es un atajo (azucar sintactica) para llevar Hero.prototype al objeto que estamos creando.

```js
function Hero(name) {
  // this = Object.create(Hero.prototype); Esto es lo que sucede internamente
  this.name = name;
  // return this; Esto ocurre implicito
}

Hero.prototype.saludar = function () {
  console.log(`New: ${this.name}`);
};

const zelda = new Hero("Zelda");
zelda.saludar();

const link = new Hero("Link");
link.saludar();
```
