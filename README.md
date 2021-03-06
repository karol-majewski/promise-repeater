# promise-repeater [![build status][ci_badge]][github_ci]

⏰ Repeat promises until they resolve successfully or hit the maximum attempt limit


## Installation

~~~sh
npm install @jakedeichert/promise-repeater
~~~


## Usage

~~~js
import { repeat } from '@jakedeichert/promise-repeater';

// Create an async/promise function that you want to attempt multiple times.
const promiseFunc = async () => {
    if (Math.random() < 0.5) throw new Error();
    return 'success';
};


// Repeat this promise until it resolves or hits the maximum attempt limit.
// This example will reject after 5 attempts.
const val1 = await repeat(promiseFunc).maxAttempts(5).start();


// You can also specify a delay (ms) between attempts.
// This example waits 1 second between attempts.
const val2 = await repeat(promiseFunc).maxAttempts(5).delay(1000).start();


// You could also attempt an infinite amount of times.
const val3 =  await repeat(promiseFunc).unlimitedAttempts().delay(1000).start();
~~~

Try this out on [RunKit](https://npm.runkit.com/@jakedeichert/promise-repeater)






[github_ci]: https://github.com/jakedeichert/promise-repeater/actions?query=workflow%3ACI
[ci_badge]: https://github.com/jakedeichert/promise-repeater/workflows/CI/badge.svg?branch=master
