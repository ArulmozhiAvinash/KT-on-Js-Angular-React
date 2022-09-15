# KT-on-Js-Angular-React
A reference guide for JS
an object-oriented computer programming language commonly used to create interactive effects within web browsers

You may often hear that almost everything in JavaScript is non-blocking (asynchronous). What does that mean?

JavaScript is a single threaded language, meaning that only one thing can be run at a time. Some other languages are multi-threaded, which means they can run multiple processes at once.
ASync execution:

console.log('Starting');
setTimeout(function() {
  console.log('Running');
}, 2000);
console.log('ending');

Why is that not in the order that we coded it in? Shouldn't the timeout cause the code to pause for two seconds, log running and then log ending?

Next, it will parse the next few lines which is the setTimeout() function. 
It will say "okay I won't do anything yet but after two seconds I will come back to this code". 
It moves on and logs "ending". 
2 seconds later, the callback that the setTimeout function queued up comes back and is executed.

That is what is referred to as the call stack.

The call stack and event loop is a pretty complicated thing to understand.



~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Declarative programming is when you write your code in such a way that it describes what you want to do, and not how you want to do it. It is left up to the compiler to figure out the how

With imperative programming, you tell the compiler what you want to happen, step by step
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~







~~~~~~~~~~~~~~~~~~~~~~
Promises are JavaScript objects that represent an eventual completion or failure of an asynchronous operation. You can achieve results from performing asynchronous operations using the callback approach or by using promises.
But there are some minor differences between the two.

A key difference between the two is when using the callback approach, we’d normally just pass a callback into a function that would then get called upon completion in order to get the result of something. In promises, however, you attach callbacks on the returned promise object.

Callback:

function getMoneyBack(money, callback) {
  if (typeof money !== 'number') {
    callback(null, new Error('money is not a number'))
  } else {
    callback(money)
  }
}

const money = getMoneyBack(1200)
console.log(money)

Promise:
function getMoneyBack(money) {
  return new Promise((resolve, reject) => {
    if (typeof money !== 'number') {
      reject(new Error('money is not a number'))
    } else {
      resolve(money)
    }
  })
}

getMoneyBack(1200).then((money) => {
  console.log(money)
})

So the question is why do we need promises in JavaScript?

Callback Hell
One common issue for using the callback approach is that when we end up having to perform multiple asynchronous operations at a time, we can easily end up with something that is known as callback hell, which can become a nightmare as it leads to unmanageable and hard-to-read code. In other words, it’s every developer’s worst nightmare.
const add = (num1, num2, function add10ToResult ) =>{
	let addtionResult = num1 + num2;
	add10ToResult(addtionResult, printResult)
	
}
Promise Chaining
Promise chaining becomes absolutely useful when we need to execute a chain of asynchronous tasks. Each task that’s being chained can only start as soon as the previous task has completed, controlled by the .thens of the chain.

const add = (num1, num2) => new Promise((resolve) => resolve(num1 + num2))

add(2, 4)
  .then((result) => {
    console.log(result) // result: 6
    return result + 10
  })
  .then((result) => {
    console.log(result) // result: 16
    return result
  })
  .then((result) => {
    console.log(result) // result: 16
  })
