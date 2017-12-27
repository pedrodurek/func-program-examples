# Examples of useful functional programming codes
This document aims to specify some useful functional programming examples written in javascript (ECMAScript 6).

## Reduce
Return an object where each property is the name of an ice cream flavor and each value is an integer that's the total count of that flavor.

```
const data = [
	{ name: 'Tyler', favoriteIceCreams: ['Strawberry', 'Vanilla', 'Chocolate', 'Cookies & Cream'] },
	{ name: 'Richard', favoriteIceCreams: ['Cookies & Cream', 'Mint Chocolate Chip', 'Chocolate', 'Vanilla'] },
	{ name: 'Amanda', favoriteIceCreams: ['Chocolate', 'Rocky Road', 'Pistachio', 'Banana'] },
	{ name: 'Andrew', favoriteIceCreams: ['Vanilla', 'Chocolate', 'Mint Chocolate Chip'] },
	{ name: 'David', favoriteIceCreams: ['Vanilla', 'French Vanilla', 'Vanilla Bean', 'Strawberry'] },
	{ name: 'Karl', favoriteIceCreams: ['Strawberry', 'Chocolate', 'Mint Chocolate Chip'] }
 ]

const iceCreamTotals = data.reduce((acc, obj) => {
    
    obj.favoriteIceCreams.forEach((value) => {
        
        if (!acc[value]) {
            acc[value] = 0    
        }   
        acc[value]++
        
    })
    return acc
    
}, {})
```

Result:
```
{ 
	Strawberry: 3,
	Vanilla: 4,
	Chocolate: 5,
	'Cookies & Cream': 2,
	'Mint Chocolate Chip': 3,
	'Rocky Road': 1,
	Pistachio: 1,
	Banana: 1,
	'French Vanilla': 1,
	'Vanilla Bean': 1 
}
```


## Filter and Map
Filter the common objects in the xs which are in the ys (from the id).

```
const xs = [{
    id: 1,
    valor: '10'
}, {
    id: 2,
    valor: '20' 
}, {
    id: 3,
    valor: '30' 
}]
const ys = [{
    id: 1,
    valor: '10' 
}, {
    id: 4,
    valor: '50' 
}]

// First way
const result = xs.filter((x) => ys.map((y) => y.id).includes(x.id))

// Second way
const result = xs.filter((x) => ys.filter((y) => x.id === y.id).length)

// Third way
const foo = ys.map((y) => y.id);
const bar = new Set(foo);
const result = xs.filter((x) => bar.has(x.id));
```

Result:
```
[{
    id: 1,
    valor: '10'
}]
```

