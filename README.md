# ES6 Cheatsheet

Instead of wasting a large amount of time searching for simple solutions for everyday ES6 problems, this quirky ES6 cheatsheet enables you to find solutions faster. Just choose what fits your requirements.

#### This Cheatsheet is ever growing! So, go ahead and pick your solutions.

##### Table of content

1.	[ES6 Objects](##es6-objects)
	1.	[CREATE OBJECT](####CREATE-OBJECT)
	1. 	[COPY, CLONE OBJECT](####COPY-CLONE-OBJECT)
	1.	[CREATE/ACCESS OBJECT PROPERTIES](####CREATE/ACCESS-OBJECT-PROPERTIES)


## 1. ES6 Objects

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

#### 1.1 CREATE OBJECT

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
const objWithOjectPrototype = Object.create( Object.prototype )
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

#### 1.2 COPY, CLONE OBJECT

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

#### 1.3 CREATE/ACCESS OBJECT PROPERTIES

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
