# ES6 Cheatsheet

Instead of wasting a large amount of time searching for simple solutions for everyday ES6 problems, this quirky ES6 cheatsheet enables you to find solutions faster. Just choose a way based on your requirements.

#### This Cheatsheet is ever growing! So, go ahead and pick your solutions.

## ES6 Objects

``` javascript

	// ------------------------------------------------
	// Following is a test object used as prototype or for references
	// ------------------------------------------------

	const User = {	
		id: null,
		name: null,
		address: {
			street: null,
			state: null,
			country: null
		}
	}

	// ------------------------------------------------
	// Create / Copy / Clone object/s 
	// ------------------------------------------------

	// create - with Object constructor
	const objWithConstructor = new Object()

	// create - without 'new' keyword
	const objWithoutNewKeyword = Object()

	// create - with object literal/initializer notation
	const objLiteral = { /* key : value */ }

	// create - with Object.prototype as prototype
	const objWithOjectPrototype = Object.create( Object.prototype )	

	// ** Note ** 
	// -- object literal notation and Object.create(Object.prototype) are equivalent

	// create - with prototype
	const objWithUserAsPrototype = Object.create( User ) 

	// create - without prototype
	const objWithNoPrototype = Object.create( null ) 

	// create - with properyObject argument
	const objWithProperyObjectArgument = Object.create( {}, {
		foo: {
			value: 'foo value',
			writable: true,
			configurable: true,
			enumerable: true
		}
	})

	// create - with key-value pairs
	const keyValuePairs = [
		['key01', 'val01'],
		['key02', 'val02']
	]
	const objWithKeyValuePairs = Object.fromEntries(keyValuePairs)

	// ** Note ** 
	// -- Object.entries() is useful when converting from a map to an object

	// copy - with mutation on target object
	const mutatedUser = Object.assign( User, {newProp: 'newProp value'} )

	// copy - as a shallow clone 
	const userShallowClone = Object.assign( {}, User )

	// copy - with spread operator as a shallow clone with object literal notation
	const userShallowCloneWithSpreadSyntax = { ...User }

	// copy - deep clone
	const userDeepClone = JSON.parse( JSON.stringify(User) )

	// ------------------------------------------------
	// Objects Properties : Create, Access
	// ------------------------------------------------	

	// access - with dot notation
	let objPropWithDotNotation = User.id

	// access - with bracket notation
	let objPropWithBracketNotation = User['id']

	// set - with dot notation
	User.newPropWithDotNotation = 'New property with dot notation'

	// set - with bracket notation
	User['prop with spaces'] = 'New property with bracket notation and spaces in the key'

	// set - with property descriptor (single property)
	Object.defineProperty( User, 'propWithDescriptor01', {
		value: 'Read only prop set with property descriptor',
		writable: false, // readonly
		enumerable: true, // accessible in loops/iterations
		configurable: false // can not delete
	})

	// set - with property descriptor (multiple property)
	Object.defineProperties( User, {
		'propWithDescriptor02': { value: 'Prop with descriptor 02', writable: true }, // descriptor object
		'propWithDescriptor03': { value: 'Prop with descriptor 03', writable: false }, // descriptor object
		// more props...
	})

	// ** Note ** 
	// -- property descriptor allow to write readonly, enumerable and configurable properties

	// access - all (enumerable) keys
	const allObjectKeys = Object.keys(User)

	// access - all (enumerable) values
	const allObjectValues = Object.values(User)

```