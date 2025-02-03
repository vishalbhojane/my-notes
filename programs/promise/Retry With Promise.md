Sometimes, you may need to retry an asynchronous operation if it fails. You can create a utility function to handle retries with Promises

```js
function retryPromise(fn, retries) {
	return fn().catch((error) => {
		if (retries > 0) {
			console.log(`Retrying... (${retries} attempts left)`);
			return retryPromise(fn, retries - 1);
		} else {
			return Promise.reject(error);
		}
	});
}
```

Usage

```js
function fetchData() {
	return new Promise((resolve, reject) => {
		// Simulate an asynchronous operation that may fail
		const success = Math.random() > 0.5;
		setTimeout(() => {
			success ? resolve('Data fetched successfully') : reject('Fetch failed');
		}, 1000);
	});
}

retryPromise(fetchData, 3)
	.then((result) => {
		console.log(result);
	})
	.catch((error) => {
		console.error('All retries failed:', error);
	});
```