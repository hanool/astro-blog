# How to implement custom `await until condition` with Javascript.

## Things to learn

1. Promise Object
2. resolve and poll

## example

```javascript
function until(conditionFunction) {
	const poll = resolve => {
		if (conditionFunction()) resolve();
		else setTimeout(_ => poll(resolve), 400);
	}

	return new Promise(poll);
}

async function myFunction(number) {
	var x = 11;
	// ...

	await until(_ => someFlag === true);

	//...
}
```
