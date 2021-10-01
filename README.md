# ES6 Cheatsheet

Instead of wasting a large amount of time searching for simple solutions for everyday ES6 problems, this quirky ES6 cheatsheet enables you to find solutions faster. Just choose what fits your requirements.

#### This Cheatsheet is ever growing! So, go ahead and pick your solutions.

##### Table of content

1.	[OBJECTS](#1-objects)
	1.	[Create object](#11-create-object)
	1. 	[Copy, clone object](#12-copy-clone-object)
	1.	[Create/Access object properties](#13-createAccess-object-properties)
	1.  [Freeze, seal object ](#14-Freeze-seal-object )
	1.  [Delete object properties](#15-Delete-object-properties)
	1.  [Miscellaneous](#16-Miscellaneous)
1.	[ARRAYS][#2-arrays]


## 1. OBJECTS

TEST / REFERENCE OBJECT

```javascript

'use strict'

// Following object 'User' is used as  
// reference/prototype for snippet examples

const User = {	
	id: null,
	name: null,
	address: {
		street: null,
		state: null,
		country: null
	}
}

```

#### 1.1 Create object

- with Object constructor
```javascript
const objWithConstructor = new Object()
```

- without 'new' keyword 
```javascript
const objWithoutNewKeyword = Object()
```

- with object literal/initializer notation
```javascript
const objLiteral = { /* key : value */ }
```

- with Object.prototype as prototype
```javascript
const objWithObjectPrototype = Object.create( Object.prototype )
```	
> -----------------------------------------------------

> :small_blue_diamond: A NOTE TO REMEMBER :small_blue_diamond:

> Object literal notation and Object.create(Object.prototype) are equivalent

> -----------------------------------------------------

- with prototype
```javascript
const objWithUserAsPrototype = Object.create( User ) 
```

- without prototype
```javascript
const objWithNoPrototype = Object.create( null ) 
```	

- with properyObject argument
```javascript
const objWithProperyObjectArgument = Object.create( {}, {
	foo: {
		value: 'foo value',
		writable: true,
		configurable: true,
		enumerable: true
	}
})
```

- with key-value pairs
```javascript
const keyValuePairs = [
	['key01', 'val01'],
	['key02', 'val02']
]
const objWithKeyValuePairs = Object.fromEntries(keyValuePairs)
```

> -----------------------------------------------------

> :small_blue_diamond: A NOTE TO REMEMBER :small_blue_diamond:

> Object.entries() is useful when converting from a map to an object

> -----------------------------------------------------

- with mutation on target object
```javascript
const mutatedUser = Object.assign( User, {newProp: 'newProp value'} )
```

#### 1.2 Copy, clone object

- create a shallow clone 
```javascript
const userShallowClone = Object.assign( {}, User )
```

- create a shallow clone with object literal notation and spread operator
```javascript
const userShallowCloneWithSpreadSyntax = { ...User }
```

- create a deep clone
```javascript
const userDeepClone = JSON.parse( JSON.stringify(User) )
```

#### 1.3 Create/Access object properties

- access - with dot notation
```javascript
let objPropWithDotNotation = User.id
```

- access - with bracket notation
```javascript
let objPropWithBracketNotation = User['id']
```

- create - with dot notation
```javascript
User.newPropWithDotNotation = 'New property with dot notation'
```

- create - with bracket notation
```javascript
User['prop with spaces'] = 'New property with bracket notation and spaces in the key'
```

- create - with property descriptor (single property)
```javascript
Object.defineProperty( User, 'propWithDescriptor01', {
	value: 'Read only prop set with property descriptor',
	writable: false, // readonly
	enumerable: true, // accessible in loops/iterations
	configurable: false // can not delete
})
```

- create - with property descriptor (multiple property)
```javascript
Object.defineProperties( User, {
	'propWithDescriptor02': { value: 'Prop with descriptor 02', writable: true }, // descriptor object
	'propWithDescriptor03': { value: 'Prop with descriptor 03', writable: false }, // descriptor object
	// more props...
})
```

> -----------------------------------------------------

> :small_blue_diamond: A NOTE TO REMEMBER :small_blue_diamond:

> Property descriptor allow us to write readonly, enumerable and configurable properties

> -----------------------------------------------------

- access - all (enumerable) keys
```javascript
const allObjectKeys = Object.keys(User)
```

- access - all (enumerable) values
```javascript
const allObjectValues = Object.values(User)
```

- access - all (enumerable) key-values pairs [key, value] as array collection
```javascript
const allKeyValuesOfObject = Object.entries( User )
```

#### 1.4 Freeze, seal object 

- freeze an object
	- no new properties can be added
	- no properties can be deleted
	- no property value can be changed
	- property descriptors can not be changed
```javascript
const objToFreeze = { prop: 21 }
Object.freeze( objToFreeze )
```

- seal an object
	- can not add new properties
	- can not delete existing properties
	- though, values of the existing writable properties can be changed
```javascript
const objToSeal = { prop: 21 }
Object.seal( objToSeal )

// following won't delete the property
delete objToSeal.prop

// following code chnages the value of the prop
objToSeal.prop = 13
```

#### 1.5 Delete object properties

- delete configurable properties
```javascript
delete User.id
```

> -----------------------------------------------------

> :small_blue_diamond: A NOTE TO REMEMBER :small_blue_diamond:

> 'delete obj.prop', returns true, if the property is configurable, else returns false.

> -----------------------------------------------------


#### 1.6 Miscellaneous

- check if the object has the specified property as its own property and not inherited
```javascript
console.log( User.hasOwnProperty('name') )
// expected output : true
console.log( User.hasOwnProperty('toString') )
// expected output : false, becuase it's inherited
```

> -----------------------------------------------------

> :small_blue_diamond: A NOTE TO REMEMBER :small_blue_diamond:

> Arrays are objects, so 'hasOwnProperty' method can be used in arrays!

> Example, let msgArr = [ "hello", "world" ]; msgArr.hasOwnProperty(1); Expected output : true

> -----------------------------------------------------

- check if the object is frozen
```javascript
Object.isFrozen( objToFreeze ) // true
```

- check if the object is sealed
```javascript
Object.isSealed( objToSeal ) // true
```

## 2. ARRAYS

In JavaScript, arrays are high-level, (ordered) list like objects. All arrays inherit from global `Array` object.

#### 2.1 Create array

- with Array constructor
```javascript
const arrWithContructor = new Array(1, 2)
// or
const arrWithContructor = Array(1, 2)
```

- with bracket notation / array literal
```javascript
const arrWithBracketNotation = [1, 2]
```

- with non-zero length and without any items
```javascript
let arrLength = 2
const arrWithNonZeroLength = new Array(arrLength)
// or
const arrWithNonZeroLength = Array(arrLength)
// or
const arrWithNonZeroLength = []
arrWithNonZeroLength.length = arrLength
```

> **NOTE** : let arr = [21] and new Array(21) are not the same! 
> The first one creates an array with an item that has value of 21, 
> where second one creates an array of length 21 with empty slots.