# Practice - JavaScript Events

## Overview

This practice lesson will help you understand how JavaScript Events work.

Flatiron Supermarket wants to further improve the functionality of their website. They would like to be able to keep track of all items added to the cart and display a message on the web page that shows the quantity for each item that was added to the cart as well as the total price for all items in the cart.

## Tools and Resources

It is recommended that you use the Visual Studio Code (VSCode) IDE for this practice lesson.

Useful considerations and terminology:

**Event**: Something a user does on a web page or something that happens on a web page.

**Event handler**: A callback function that executes code in response to an event.

**click event**: An event that occurs when a user clicks on an element on a web page.

**change event**: An event that occurs when a user selects or changes a value for an element on a web page that contains a value attribute.

Here are some other useful resources:
- MDN
  - [Introduction to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)
  - [Event reference (Web Events)](https://developer.mozilla.org/en-US/docs/Web/Events)
  - [Element](https://developer.mozilla.org/en-US/docs/Web/API/Element)
    - [Element: click event](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event)
  - [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)
    - [HTMLElement: change event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/change_event)

## Instructions

**Fork and clone** this practice lesson into your local environment. Navigate into its
directory in the terminal, then run `code .` to open the files in Visual Studio
Code.

Then, open the `index.html` file on your browser to run the application.

Write your code in the `index.js` file. There is some starter code provided in `index.js`.

These are your tasks:

1. `selectedItem`: Declare a variable in global scope named `selectedItem` using the `let` keyword and assign it the value of the first item from the `items` array.
2. `totalPrice`: Declare a variable in global scope named `totalPrice` using the `let` keyword and assign it the value of `0`.
3. Declare a function named `displayItemDetails()`.
4. Declare a function named `addToCart()`.
5. Declare a function named `addCartItemMessageToList()` that has 1 parameter named `item`.
6. Call the `displayItemDetails()` function on the next line after all variables and functions have been declared.
7. `displayItemDetails()`: When the `displayItemDetails()` function is called, the following actions should take place:
    - The `textContent` attribute for the `<div>` element with the id `item-name` is set to the value of the `name` key for the `object` stored in the `selectedItem` variable.
    - The `src` attribute for the `<img>` element with the id `item-image` is set to the value of the `image` key for the `object` stored in the `selectedItem` variable.
    - The `alt` attribute for the `<img>` element with the id `item-image` is set to the value of the `name` key for the `object` stored in the `selectedItem` variable.
    - The `textContent` attribute for the `<span>` element with the id `item-price` is set to the value of the `price` key for the `object` stored in the `selectedItem` variable.
    - The `textContent` attribute for the `<span>` element with the id `item-number-in-cart` is set to the value of the `numberInCart` key for the `object` stored in the `selectedItem` variable.
8. Add an event listener to the `<button>` element with the id of `add-to-cart` that will allow the `<button>` element to listen for a `click` event and will call the `addToCart()` function in response to the `click` event.
9. `addToCart()`: When the `addToCart()` function is called, the following actions should take place:
    - Increment the value of the `numberInCart` key for the `object` stored in the `selectedItem` variable.
    - Update the `textContent` attribute for the `<span>` element with the id `item-number-in-cart` so that its value increases by 1.
      - Hint: The value of the `textContent` attribute is a `string` and will need to be converted to a `number` when increasing its value or performing any mathematical operations with its value.
    - The value of `totalPrice` is set to `0`.
    - The `textContent` attribute for the `<h2>` element with the id of `cart-message` is set to `The following items are in your cart:`.
    - Clears the contents of the `<ul>` element with the id of `cart-list` so it no longer has any elements nested inside it.
    - Iterate over the array stored in the `items` variable using an array iterator method such as `forEach()`. For each of the items in the array stored in the `items` variable, `if` the value of the `numberInCart` key for the item is greater than `0`, the `addCartItemMessageToList()` function is called and the item is passed in as an argument to the `addCartItemMessageToList()` function.
    - The `textContent` attribute for the `<h2>` element with the id of `total-price-message` is set to a `string` that includes "The total price will be $" + the value of the `totalPrice` variable. For example, if the value of the `totalPrice` variable is `5.97`, the text should read "The total price will be $5.97".
10. `addCartItemMessageToList(item)`: When the `addCartItemMessageToList()` function is called, the following actions should take place:
    - An `<li>` element is created.
    - The `className` attribute for the `<li>` element is set to `cart-item-message item`.
    - The `textContent` attribute for the `<li>` element is set to a `string` that contains the values of the `numberInCart` key, the `name` key, and the `price` key for the `object` stored in the `item` parameter, in the following format: "`numberInCart` `name`(s), which cost $`price` each". For example, if the value of the `item` parameter’s `numberInCart` key is `7`, if the value of the `item` parameter’s `name` key is `apple`, and if the value of the `item` parameter’s `price` key is `1.99`, the text should read `7 apple(s), which cost $1.99 each`.
    - The `<li>` element is appended to the `<ul>` element with the id of `cart-list`.
    - The value of the `price` key for the `object` stored in the `item` parameter is multiplied by the value of the `numberInCart` key for the `item` parameter, the result is added to the value of the `totalPrice` variable, and the sum is stored in the `totalPrice` variable as the updated total price.
11. Add an event listener to the `<select>` element with the id of `item-select` that will allow the `<select>` element to listen for a `change` event. The event listener should have an event handler (callback function) that does the following in response to the `change` event:
    - Sets the value of the `selectedItem` variable to an item whose `name` is strictly equal to the `value` of the option that was selected from the `<select>` element’s dropdown menu.
      - Hint: You can use the `find()` array iterator method to iterate over the array stored in the `items` variable and find the item whose `name` is strictly equal to the `value` of the option that was selected.
    - Calls the `displayItemDetails()` function.

## Solution

```javascript
const items = [
    {
        name: 'apple',
        image: 'images/items/apple.png',
        price: 1.99,
        numberInCart: 0
    },
    {
        name: 'banana',
        image: 'images/items/banana.png',
        price: 0.99,
        numberInCart: 0
    },
    {
        name: 'pineapple',
        image: 'images/items/pineapple.png',
        price: 2.99,
        numberInCart: 0
    }
];

let selectedItem = items[0];
let totalPrice = 0;

function displayItemDetails(){
    const itemNameDiv = document.getElementById('item-name');
    itemNameDiv.textContent = selectedItem.name;

    const itemImage = document.getElementById('item-image');
    itemImage.src = selectedItem.image;
    itemImage.alt = selectedItem.name;

    const itemPriceSpan = document.getElementById('item-price');
    itemPriceSpan.textContent = selectedItem.price;

    const itemNumberInCartSpan = document.getElementById('item-number-in-cart');
    itemNumberInCartSpan.textContent = selectedItem.numberInCart;
}

function addToCart(){
    selectedItem.numberInCart++;
    const itemNumberInCartSpan = document.getElementById('item-number-in-cart');
    itemNumberInCartSpan.textContent = Number(itemNumberInCartSpan.textContent) + 1;

    totalPrice = 0;

    const cartMessageElement = document.getElementById('cart-message');
    cartMessageElement.textContent = "The following items are in your cart:";

    const cartList = document.getElementById('cart-list');
    cartList.textContent = '';

    items.forEach(item => {
        if(item.numberInCart > 0){
            addCartItemMessageToList(item);
        }
    });

    const totalPriceMessageElement = document.getElementById('total-price-message');
    totalPriceMessageElement.textContent = `The total price will be $${totalPrice}`;
}

function addCartItemMessageToList(item){
    const liElement = document.createElement('li');
    liElement.className = 'cart-item-message item';
    liElement.textContent = `${item.numberInCart} ${item.name}(s), which cost $${item.price} each`;

    const cartList = document.getElementById('cart-list');
    cartList.appendChild(liElement);

    totalPrice = (item.price * item.numberInCart) + totalPrice;
}

displayItemDetails();

const addToCartButton = document.getElementById('add-to-cart');
addToCartButton.addEventListener('click', addToCart);

const itemSelect = document.getElementById('item-select');
itemSelect.addEventListener('change', (event) => {
    selectedItem = items.find(item => {
        return item.name === event.target.value;
    });
    displayItemDetails();
});
```