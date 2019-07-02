# Javascript - Higher Order Functions

> In this example codes we will look at some of the very powerful higher 
order built in functions and working with `fetch` api. We will look at 
***forEach***, ***map***, ***filter***, ***reduce***, ***sort** as well as creating ***custom higher order function***.

```
/**
 * @author Jino
 * @email jinowilbertolacson@gmail.com
 * @create date 2019-07-02 17:07:21
 * @modify date 2019-07-02 17:07:21
 */
 
//Rest API endpoint starwars

const apiStarWars = "https://swapi.co/api/planets/?format=json"
let response = await fetch(apiStarWars);
let data = await response.json();
const starWarsPlanet = data.results;
//console.log(starWarsPlanet)

```

#### 1. Loops
```
Example: for loop

for(let i = 0; i < starWarsPlanet.length; i++) {
   console.log(starWarsPlanet[i].films);
}

Example: forEach

starWarsPlanet.forEach(function(planet) {
   console.log(planet.films);
});


```

#### 2. Filter
```
Example 1: using for loop

let planetRotation = [];
for(let i = 0; i < starWarsPlanet.length; i++) {
   if(rotation.rotation_period >= 24 && rotation.rotation_period <= 27) {
     planetRotation.push(starWarsPlanet[i]);
   }
}

Example 2: using filter

const planetRotation1 = starWarsPlanet.filter(function(rotation){
  if(rotation.rotation_period >= 24 && rotation.rotation_period <= 27) return true;
})

Example 3: using filter in es6 format

const planetRotation2 = starWarsPlanet.filter(rotation => (rotation.rotation_period >= 24 && rotation.rotation_period <= 27));

console.log(planetRotation1);
console.log(planetRotation2);

```


#### 3. Mapping
```
Example 1: 

const planets1 = starWarsPlanet.map(function(planet) {
   return planet.name;
});

Example 2:

//with string templates
const planets2 = starWarsPlanet.map(function(planet) {
   return`${planet.name} [${planet.population} - ${planet.rotation_period}]`;
});

Example 3:

//using es6 format
const planets3 = starWarsPlanet.map(planet => planet.orbital_period)

//..etc
//const planet4 = starWarsPlanet.map().map()

console.log(planets1)
console.log(planets2)
console.log(planets3)
```


#### 4. Sorting
```
Example 1:

const sortedPlanetsByRotation1  = starWarsPlanet.sort(function(cmp1, cmp2) {
  if(cmp1.name > cmp2.name) {
     return 1;
   } else {
     return -1;
   }
 });

Example 2:

const sortedPlanetsByRotation2 = starWarsPlanet.sort((a, b) => (a.name > b.name ? 1 : -1));

Example 3:

const sortPlanetNames = starWarsPlanet.sort((a, b) => a.name - b.name);

console.log(sortedPlanetsByRotation1);
console.log(sortedPlanetsByRotation2);
console.log(sortPlanetNames);

```

#### 5. Reducing
```
Example 1:

let rotationSum1 = 0;
for(let i = 0; i < starWarsPlanet.length; i++) {
   rotationSum1 += starWarsPlanet[i].orbital_period;
}

Example 2:

const rotationSum2 = starWarsPlanet.reduce(function(total, rotatePeriod) {
   return total + rotatePeriod.rotation_period;
}, 0);

Example 3:


Example 4: using es6 format

const rotationSum3 = starWarsPlanet.reduce((total, rotatePeriod) => total + rotatePeriod.rotation_period, 0);


const rotationSum4 = starWarsPlanet.reduce((total, movements) => total + (movements.rotation_period - movements.orbital_period), 0);

console.log(rotationSum)

```


## Custom high order function
> An example code of custom high order function 
```
//Array of language
const stringsOfArray = ['JavaScript', 'Python', 'PHP', 'Java', 'C'];

//Custom function that accepts two arguments array and function(item){}
function higherMapForEach(arr, fn) {
  const newArr = [];
  for(let i = 0; i < arr.length; i++) {
    newArr.push(
      fn(arr[i])
    );
  }
  return newArr;
}

//Call custom higher order function
const lenArray = higherMapForEach(stringsOfArray, function(item) {
  return item.length;
});

// prints [ 10, 6, 3, 4, 1 ]
console.log(lenArray);
```

#### Some useful resources

[Array Destructor](https://javascript.info/destructuring-assignment)

[Object Desctructor](https://javascript.info/destructuring-assignment#object-destructuring)

[Smart function parameter declaration](https://javascript.info/destructuring-assignment#smart-function-parameters)

