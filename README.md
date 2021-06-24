youtube channel JavaScript de Noob a Pro   --   https://www.youtube.com/watch?v=4INJF9fc6Ys&t=4s


# Preguntas Entrevista de Trabajo para Desarrollador JR. REACT JS [#1 Objetos]


### Esta este objeto declarado correctamente ? Como accederiamos a la primera llave ?
```json
let person = {
  "first-name": "Jhon",
  "last-name": "Smith",
  "age": 25
}
```
Respuesta: Si, es correcto
Respuesta: person["first-name"]


### Dado el siguiente objeto, itera para extraer los 3 nombres de los clientes:

```js
let company = {
  name: "Bar Company",
  address: "Bla bla street",
  phone: 0034323432,
  clients: ["Ralf", "Leona", "Clark"]
}
```

  Respuesta: 
  ```js
  company.clients.map(client => console.log(client))
  Respuesta: 
  for ( let client of company.clients ) console.log(client)
  ```

### Del mismo objeto, extraer las llaves
  Respuesta: 
  ```js
  for(let key in company)console.log(key)
  ```

### Del mismo objeto, extraer los valores
  Respuesta:
  ```js
  for(let key in company)console.log(company[key])
  ```

### Ahora queremos extraer las llaves y los valores
  Respuesta: // El for para entries devuelve individualmente, no array
  ```js
  for(let [key, value] of Object.entries(company))console.log(key + ' ' + value)
  ```

### Al pasar el objeto company como prop a otro componente (en react), queremos cambiar el nombre de la llave "name" a "companyName". Como lo harias ?
  Respuesta: En ES5 tendriamos que hacer un for loop, desde ES6 (existe lña desestructuracion de objetos), podemos hacer lo siguiente:
  ```js
  const { name: companyName, address, phone, clients } = company
  ```

### Mediante el metodo map, vamos a iterar un array de objetos del tipo company, y pasaremos el objeto como prop al componente. Queremos asegurarnos de que los datos muestren un texto para el telefono, incluso si la compañia que estamos pasando no incluye el numero. Destructura la informacion, asegurandote de que, por defecto, si el objeto no tiene la llave phone, nos muestre el texto "no number available"
  Respuesta:
  ```js
  const { name, address, phone = "no number available", clients } = company
  console.log(phone) // si no existe imprime "no number available", como hice desestructuracion NO tengo que llamar asi "company.phone"
  ```


### Dada la siguiente funcion, extrae las llaves del objeto retornado. 
### Esto a que nos recuerda en React ?
```js
const getDetails = () => {
  return {
    age: 25,
    name: "Flora",
  }
}
```
  Respuesta:
  ```js
  const { age, name } = getDetails()
  ```
  Respuesta2: Esto nos recuerda en React a Hooks

### En el objeto company, cambiar "name" a "companyName", "address" a "companyAddress", y almacena el resto.
  Respuesta:
  ```js
  const { name: companyName, address: companyAddress, ...rest } = company
  ```

### Haz un refactor del siguiente codigo, utilizando restructuring

```js
let company = {
  name: "Bar Company",
  address: {
    street: "Bla bla street", 
    zipcode: 111131,
    city: "JSCity",
    country: "JSCountry",
  },
  phone: 0034323432,
  clients: ["Ralf", "Leona", "Clark"]
}

En formato ES5
let name = company.name;
let street = company.address.street;
let country = company.address.country;
```

  Respuesta:
  ```js
  let { name, address: { street, country} } = company
  ```


// ----------------------------------------------------------------------------------------------

## Preguntas Entrevista de Trabajo para Desarrollador JR. REACT [#2 Arrays]
https://www.youtube.com/watch?v=Rxw1u2CXOXI


### Obtener los elementos a y c, utilizando ES5 y ES6 destructuring

```js
const letters = ["a", "b", "c"];
```
  Respuesta:
  ```js
  ES5 
  const a = letters[0];
  const c = letters[2];

  ES6
  const [a,  , c] = letters;  // a = "a"  // b = undefined  // c = "c"
  ```

### Dado el siguiente array, extrae el primer y segundo elemento, y el resto, mantenlos guardados en otro array

```js
const tennisPlayers = ["Federer", "Jocovic", "Nadal", "Thiem", "Zverev", "Tsitsipas"]
```
  Respuesta:
  ```js
  const [primero, segundo, ...rest] = tennisPlayers;  
  // primero = "Federer"
  // segundo = "Jocovic"
  // rest = ["Nadal", "Thiem", "Zverev", "Tsitsipas"]

  // !rest element must be LAST element
  ```

### ahora extrae el primer y sexto elemento, y el resto, mantenlos guardados en otro array

  Respuesta:
  ```js
  // debemos reorganizar el array, asi:
  [primero, segundo, tercero, cuarto, quinto, sexto] = ["Federer", "Tsitsipas", "Nadal", "Thiem", "Zverev", "Jocovic"]

  const [primero, segundo, ...rest] = tennisPlayers;  
  // primero = "Federer"
  // segundo = "Tsitsipas"
  // rest = ["Nadal", "Thiem", "Zverev", "Tsitsipas"]

  // !rest element must be LAST element
  ```

### ahora iterar en el array, y anhadirle el ranking

  Respuesta:
  ```js
  ES6
  tennisPlayers.map((player, index) => index+1 + "-" + player);
  // 0: "1-Federer"
  // 1: "2-Jocovic"
  // 2: "3-Nadal"
  // 3: "4-Thiem"
  // 4: "5-Zverev"
  // 5: "6-Tsitsipas"

  ES5
  for (let i=0; i < tennisPlayers.length; i++) {
    console.log(i+1 + "-" + tennisPlayers[i])
  }
  // "1-Federer"
  // "2-Jocovic"
  // "3-Nadal"
  // "4-Thiem"
  // "5-Zverev"
  // "6-Tsitsipas"
  ```

### intercambiar los valores de dos variables

```js
let a = "Hey", b = "Bye"
```
Respuesta:
  ```js
  [a, b] = [b, a];  //  ["Bye", "Hey"]
  ```

### que imprime ?
```js
const array = [a,  , c];
const [first, second] = array
// [ a, undefined]
```