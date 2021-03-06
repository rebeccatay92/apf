You've made it pretty far through this module (and your blog looks sweet). Awesome job!

Now's the time to grab some tea, because we're going to throw some terminology at you. It's great that now you're proficient at React, but as you go forward with programming, there are some concepts that are worth thinking about.

## Imperative and Declarative Programming

Imperative and declarative programming are two terms that you might encounter if you hang out with developers long enough. Most developers begin by writing _imperative_ code. That is to say, most developers:
1. outline what they need to do
2. write it out step by step.

Writing pseudocode is an excellent example of writing things out step by step, the imperative way. For example, if we were to ask everyone in the room to say there name we could conceptually write it out as follows:

```
ask everyone in the room to line up
for every person in the line
  ask each person to come to the front of the room
  ask each person to then speak their name
```
So to step through this the imperative way of thinking, let's open [jsbin](http://jsbin.com/):

1.. Naturally, we could write that out in Javascript by creating an array of those people.

```js
let room = ['omily', 'lichard', 'kathew', 'cecelious'];
```
> Note the ES6 syntax with 'let' instead of 'var'!

2.. Next, we would loop through them, and assign each active speaker to a variable named _person_.

```js
let room = ['omily', 'lichard', 'kathew', 'cecelious'];

for (let i = 0; i < room.length; i++) {
  let person = room[i];
}
```


3.. Finally, we have them speak their name - or in our case, we'll just _console.log()_ their name out as represented by the _person_ variable.

```js
let room = ['omily', 'lichard', 'kathew', 'cecelious'];

for (let i = 0; i < room.length; i++) {
  let person = room[i];
  console.log("Imperative way: " + person);
}
```

> Run this in JSBin and check the console tab. It works - we've built this function using the *Imperative* way of thinking.

You have explicitly listed out each step, paying attention to each and every detail of what you need to achieve. Imperative programming focuses on the _why_, _how_, _where_, and _when_ your code executes. It allows precise control over your code and allows for line-by-line code execution - you're writing every single thing that happens.

Now, let's break from this approach for just a moment. Below that function in JSBin (leave the array!), let's look at building something in the **declarative** manner.

Now, if we want to perform the same action, we could write our loop like so:

```js
room.forEach((person) => {
  console.log("Declarative way: " + person);
});
```
> Run it! It still lists the people in the room. Consider how much less code it took.

What happened? Well, Javascript has a built-in method that loops over arrays for you. `.forEach()` does the same thing that `for` loop you wrote above - except you had to write a lot less.

`forEach` is a method in declarative programming. Instead of writing every single step yourself - instead of explicitly writing the _why_, _how_, _where_, and _when_ of your program - this method only cares about *what* you want.

Instead of taking the time to write out a specific set of instructions to receive a result, you focus on just one thing: the result. This might sound a little confusing at first, so open up JSBin and try solving the following problem.

#### Practice: Applying a Discount to Items in a Shopping Cart

You notice that your favorite series is on sale this month. You've been holding off, but today is the day! You're going to pick it up and treat yourself. After filling your shopping cart up, you peruse the internet for a discount coupon. Finally, you found one! You furiously enter in `TREATYOSELF2017` into your cart's coupon code input box, and instantaneously your cart reflects the discounted prices. Success!

How is this discount coded?

An **imperative** approach might:
1. declare an object consisting of the items in the cart with the original prices.
2. loop through that object with a 'for' loop, updating the price as it goes.

And this would be explicitly coded line by line, like this:

```js
// Imperative approach
// oh boy! Zelda games! On sale! I need them!
let items = [
  {
    title: 'Breath of the Wild',
    price: 49.99
  },
  {
    title: 'The Minish Cap',
    price: 29.99
  },
  {
    title: 'Twilight Princess',
    price: 49.99
  }
];

// calculate the discount of 50% off
let discountedItems = [];
// loop on through
for (let i = 0; i < items.length; i++) {
  // create a new item, update the sale price thanks to the coupon, and push into the discountedItems array
  discountedItems.push({
    title: items[i]['title'], // keep the title
    price: items[i]['price'] * 0.5  // update the price
  });
}
```

The imperative approach to writing code gives us full control of *how* we add the updated price into the new array. In this case, we:
1. _When_ we create the Object, we set the initial attributes.
2. access attributes directly through indices that represent _which_ Object and _what_ attribute we want to select.
3. _How_ we do this is we create a new array and update the values to push to the new object.

> Try it. Add `console.log(items); console.log(discountedItems);`
and hit `run` in JSBin. It works!

This is fairly clean code, but we could write more succinct code using a **declarative** style. We'll use the Array's built-in method `.map` to accomplish the same thing. We'll focus on _what_ we want - just the updated values. We'll let `.map` take care of the _how_.

```js
let discountedItems = items.map((item) => {
  return {
    title: item.title,
    price: item.price * 0.5
  }
});
```
> Try it! This goes right after the "items" array declaration, replacing all the calculation code (the `for` loop and the discountedItems array before that).

Using the declarative approach, we declare that we intend to .map through an array and create a newly updated version of it.

_But what if that method breaks?_ you might be thinking? While a problem, you know exactly what is broken - the `.map` method (or more likely your syntax is incorrect). This allows for easy debugging and testing. Consider how you would debug the imperative version of the code instead. How would your approach differ?

#### Wrapping It Up

Declarative and imperative are two different styles of writing code.

Imperative is commonly found in object-oriented programming environments where you focus on a line-by-line execution path working with objects.

With the focus on simplicity in modern web development, some developers have been leveraging declarative techniques. React.js is one framework that uses a declarative approach; Vue.js is another. You'll find that many asynchronous Javascript techniques rely on declarative programming techniques for ease of readability.

While neither way is incorrect, declarative code tends to lead to DRY, clean code. As a final fun fact - functional programming is a subset of declarative programming. If you've ever used a functional language, such as Haskell or Lisp, or written calculus, you've likely written declarative code.
