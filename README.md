<img alt="Ignite" src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2fbacb7a-e460-44a3-8fc5-e66f96dae148%2Fcover-reactjs.png?table=block&id=51e4099a-6e2f-4d4b-ae94-f9fe75bb769d&width=5120&userId=1b109781-8635-4162-80d6-714377721793&cache=v2" />

<h3 align="center">
Challenge 03: Creating a shopping cart hook
</h3>

<p align="center">
  <img alt="Languages" src="https://img.shields.io/github/languages/count/filipebteixeira98/ignite-reactjs-hook-challenge?color=%235963C5" />
  <img alt="repo-size" src="https://img.shields.io/github/repo-size/filipebteixeira98/ignite-reactjs-hook-challenge?color=%235761C3" />
  <img alt="lastcommit" src="https://img.shields.io/github/last-commit/filipebteixeira98/ignite-reactjs-hook-challenge?color=%235761C3" />
  <img alt="License" src="https://img.shields.io/github/license/filipebteixeira98/ignite-reactjs-hook-challenge?color=%235E69D7" />
  <img alt="Issues" src="https://img.shields.io/github/issues/filipebteixeira98/ignite-reactjs-hook-challenge?color=%235965E0">
  <a href="mailto:filipebarrosteixeira98@gmail.com">
   <img alt="Email" src="https://img.shields.io/badge/-filipebarrosteixeira98%40gmail.com-%23525DCB" />
  </a>
</p>

## :rocket: About the challenge

In this challenge, you will have to create an application to train what you have learned so far in ReactJS

This will be an application where your main objective is to create a shopping cart hook. You will have access to two pages, a component and a hook to implement the features requested in this challenge:

- Add a new product to the cart;
- Remove a product from the cart;
- Change the quantity of a product in the cart;
- Calculation of the sub-total and total cart prices;
- Inventory validation;
- Display of error messages;
- Among others.

## :construction_worker: Preparing for the challenge

For this challenge, in addition to the concepts seen in class, we will use some new things to make our application even better. So, before going directly to the challenge code, we’ll explain a little bit of:

- Fake API with JSON Server;
- Preserve cart data with localStorage API;
- Show errors with toastify.

### Fake API with JSON Server

Just as we use MirageJS in module 2 to simulate an API with transaction data from the dt.money application, we will use JSON Server to simulate an API that has the information of genres and films.

Navigate to the created folder, open it in Visual Studio Code and execute the following commands in the terminal:

```bash
yarn
yarn server
```

Then you will see the message:

<img alt="server" src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1abc3356-2936-4106-a4fe-a3fc8efd1373%2FUntitled.png?table=block&id=7fe88f6f-62c6-45c7-a898-d1672dbbe6bd&width=1420&userId=&cache=v2" width=300/>

Notice that it has started a fake API with the resources `/stock` and `/products` on `localhost` on port `3333` from the information in the server.json file located at the root of your project. Accessing these routes in your browser, you can see the return of the information already in JSON:

<img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0fe33995-e128-480c-aaf9-c8d77e0f5544%2FUntitled.png?table=block&id=c98c49ef-d0be-4306-a2e5-028e363c58c6&width=380&userId=&cache=v2" height=300/>
<img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc89f74cb-4e41-4658-91d4-f8358a973088%2FUntitled.png?table=block&id=fa8ff43b-a903-4ad6-972f-d165a0e5ad94&width=1820&userId=&cache=v2" width=300/>

That way, you just need to consume these API routes normally with Axios.

### Preserving cart with localStorage API

To preserve the cart data even if we close the application, we will use the **localStorage API**

This is an API that allows us to persist data in the browser in a key-value scheme (similar to what we have with JSON objects). Since this is a global API, you don't need to import anything before using it.

To save the data, you must use the `setItem` method. As a first argument you must enter the name you want to give the registration, in the case of this challenge it is `mandatory` to use the name `@RocketShoes:cart`. The second argument, on the other hand, is the value of the record that **must** be in the `string` format. Below is an example:

```js
localStorage.setItem('@RocketShoes:cart', cart);
```

To retrieve the data, you must use the `getItem` method, passing as the registration argument which, in the case of this challenge, is `mandatory` to use as `@RocketShoes:cart`. Below is an example:

```js
const storagedCart = localStorage.getItem('@RocketShoes:cart');
```

### Showing errors with toastify

o show the errors on screen, we will use a lib called **react-toastify**. It helps to show temporary and quick information in a very beautiful way.

Of all the methods, we will only use `error` and it will be mandatory to use predefined messages for the tests to pass.

## :wrench: What should I edit in the application?

With the template already cloned, the dependencies installed and the fake API running, you must complete where there is no code with the code to achieve the objectives of each test. The documents that must be edited are:

- src/components/Header/index.tsx
- src/pages/Home/index.tsx
- src/pages/Cart/index.tsx
- src/hooks/useCart.tsx

### components/Header/index.tsx

<img alt="header" src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F71a7f217-c1bb-426a-8fcc-dfb65db6bb7a%2FUntitled.png?table=block&id=acdec457-aedb-4c92-a020-ee3387283f85&width=2010&userId=&cache=v2" />

You must receive the `cart` array from the hook `useCart` and show on screen the number of different products added to the cart. Thus, if the cart has 4 units of item A and 1 unit of item B, the value to be shown is `2 items`.

### pages/Home/index.tsx

<img alt="main" src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3d320e3c-a052-4f72-994e-aa69617ee85c%2FUntitled.png?table=block&id=c553563e-e14f-4b4d-9f80-b44d96c771b8&width=2020&userId=&cache=v2" width=300/>

You must render the products sought from the fake API on screen with the information of title, image, price, quantity added to the cart. Finally, it is necessary to implement the functionality of adding the chosen product to the cart by clicking on the `ADD TO CART` button.

In this file, we have three important points to be implemented:

- **cartItemsAmount:** You must have information about the quantity of each product in the cart. We suggest creating a key/value array using `reduce` where the key represents the product id and the value the quantity of the product in the cart.
- **loadProducts:** You must search for Fake API products and format the price using the `utils/format` helper
- **handleAddProduct:** You must add the chosen product to the cart.

### pages/Cart/index.tsx

<img alt="cart" src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa34120df-4046-4a84-8133-6eb987bceac6%2FUntitled.png?table=block&id=4e3c96e5-f7a7-4e1a-9fa9-34d99494047b&width=2000&userId=&cache=v2" width=300/>

You must render a table with the image, title, unit price, quantity of units and subtotal price of each product in the cart. In addition, it is also necessary to render the total price of the cart. Finally, it is necessary to implement the functionalities of the buttons to decrement, increase and remove the product from the affection.

In this file, we have five important points to be implemented:

- **cartFormatted:** You must format the cart by adding the fields `priceFormatted`(price of the product) and `subTotal` (price of the product multiplied by the quantity) both properly formatted with `utils/format`.
- **total:** You must have information about the total value of the cart properly formatted with `utils/format`.
- **handleProductIncrement:** You must increase the quantity of the product chosen in the cart by 1 unit.
- **handleProductDecrement:** The quantity of the product chosen in the cart must be reduced by 1 unit, where the minimum value is 1 (in this case the button must be deactivated).
- **handleRemoveProduct:** You must remove the chosen product from the cart.

### hooks/useCart.tsx

Although it does not directly return any rendering of elements in the interface like the other files, this is the heart of the challenge. He is responsible for:

- hook `useCart`;
- context `CartProvider`;
- manipulate `localStorage`;
- display `toasts`.

So this is where you will implement the features that will be used by the rest of the app. The main points are:

- **cart:** You should check if there is any record with the value `@RocketShoes:cart` and return this value if it exists. Otherwise, return an empty array.

- **addProduct:** You must add a product to the cart. However, there are a few things to check

- The updated value of the cart must be perpetuated in **localStorage** using the `setItem` method.
- If the product already exists in the cart, you should not add a new repeated product, just increase the quantity by 1 unit;
- Check if the desired quantity of the product is in stock. Otherwise, use the `error` method of **react-toastify** with the following message:

```js
toast.error('Quantity ordered out of stock');
```

- Capture the errors that occur along the method using `trycatch` and, in catch, use the `error` method of **react-toastify** with the following message:

```js
toast.error('An error occurred trying to add product');
```

- **removeProduct:** You must add a product to the cart. However, there are a few things to check:

- The updated value of the cart must be perpetuated in **localStorage** using the `setItem` method.
- Capture the errors that occur along the method using `trycatch` and, in catch, use the `error` method of **react-toastify** with the following message:

```js
toast.error('Product removal error');
```

- **updateProductAmount:** You must add a product to the cart. However, there are a few things to check:

- The updated value of the cart must be perpetuated in **localStorage** using the `setItem` method.
- If the product quantity is less than or equal to zero, exit the **updateProductAmount** function instantly.
- Check if the desired quantity of the product is in stock. Otherwise, use the `error` method of **react-toastify** with the following message:

```jsx
toast.error('Quantity ordered out of stock');
```

Catch the errors that occur along the method using `trycatch` and, in catch, use the `error` method of react-toastify with the following message:

```jsx
toast.error('Error when changing product quantity');
```

# :page_facing_up: License

This project is under a license [MIT](./LICENSE).

Challenge proposed with 💜 by Rocketseat 👋 [Join this great community!](https://discordapp.com/invite/gCRAFhc)
