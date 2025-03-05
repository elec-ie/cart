<script>
  let cartItems = [
    { id: "VL-001", name: "Viva Leaf Tulsi Basil Honey", price: 14.00, quantity: 1, img: "/honey.jpg" }
  ];

  let suggestedItems = [
    { name: "Snack Attack", price: 30.00, img: "/snack.jpg" },
    { name: "Cacao Sampaka Specialty Chocolate", price: 50.00, img: "/chocolate.jpg" },
    { name: "Saladini Sellato Crescent Knife", price: 125.00, img: "/knife.jpg" }
  ];

  function increaseQuantity(item) {
    item.quantity++;
  }

  function decreaseQuantity(item) {
    if (item.quantity > 1) item.quantity--;
  }
</script>

<div class="cart-container">
  <h1>CART</h1>
  
  <div class="cart-items">
    <div class="cart-header">
      <span>Cart Items</span>
      <span>Price</span>
      <span>Quantity</span>
      <span>Subtotal</span>
    </div>

    {#each cartItems as item}
      <div class="cart-item">
        <img src={item.img} alt={item.name} />
        <div class="details">
          <p>{item.name}</p>
        </div>
        <p class="price">${item.price.toFixed(2)}</p>
        <div class="quantity">
          <button on:click={() => decreaseQuantity(item)}>-</button>
          <span>{item.quantity}</span>
          <button on:click={() => increaseQuantity(item)}>+</button>
        </div>
        <p class="subtotal">${(item.price * item.quantity).toFixed(2)}</p>
      </div>
    {/each}
  </div>

  <div class="suggested-items">
    <h2>Many Customers Added the Following:</h2>
    <div class="suggested-grid">
      {#each suggestedItems as item}
        <div class="suggested">
          <img src={item.img} alt={item.name} />
          <p>{item.name}</p>
          <p class="price">${item.price.toFixed(2)}</p>
          <button>Add to Your Order</button>
        </div>
      {/each}
    </div>
  </div>

  <div class="order-summary">
    <p class="subtotal-text">Subtotal: ${cartItems.reduce((sum, item) => sum + item.price * item.quantity, 0).toFixed(2)}</p>
    <p class="grand-total">Grand Total: ${cartItems.reduce((sum, item) => sum + item.price * item.quantity, 0).toFixed(2)}</p>
    <button class="checkout">Proceed to Checkout</button>
    <button class="continue">Continue Shopping</button>
  </div>
</div>

<style>
  .cart-container {
    width: 85%;
    max-width: 1200px;
    margin: auto;
    padding: 20px;
    font-family: 'Arial', sans-serif;
  }

  h1 {
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 20px;
  }

  .cart-items {
    background: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  }

  .cart-header {
    display: grid;
    grid-template-columns: 3fr 1fr 1fr 1fr;
    font-weight: bold;
    padding-bottom: 10px;
    border-bottom: 2px solid #ddd;
  }

  .cart-item {
    display: grid;
    grid-template-columns: 3fr 1fr 1fr 1fr;
    align-items: center;
    padding: 15px 0;
    border-bottom: 1px solid #ddd;
  }

  img {
    width: 70px;
    height: auto;
    border-radius: 5px;
  }

  .details {
    margin-left: 10px;
  }

  .price, .subtotal {
    font-weight: bold;
  }

  .quantity {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .quantity button {
    padding: 5px 10px;
    font-size: 16px;
    border: none;
    background: #0071e3;
    color: white;
    border-radius: 5px;
    cursor: pointer;
  }

  .quantity button:hover {
    background: #005bb5;
  }

  .suggested-items {
    margin-top: 40px;
  }

  .suggested-grid {
    display: flex;
    gap: 20px;
    margin-top: 15px;
  }

  .suggested {
    text-align: center;
    background: #fff;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
    width: 200px;
  }

  .suggested img {
    width: 100%;
    height: auto;
    border-radius: 5px;
  }

  .suggested .price {
    font-weight: bold;
    margin: 8px 0;
  }

  .suggested button {
    background: #0071e3;
    color: white;
    border: none;
    padding: 8px 15px;
    font-size: 14px;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.3s;
  }

  .suggested button:hover {
    background: #005bb5;
  }

  .order-summary {
    margin-top: 30px;
    padding: 20px;
    background: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
    text-align: right;
  }

  .subtotal-text, .grand-total {
    font-size: 18px;
    font-weight: bold;
  }

  .checkout, .continue {
    width: 100%;
    padding: 12px;
    font-size: 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
    transition: 0.3s;
  }

  .checkout {
    background: #0071e3;
    color: white;
  }

  .checkout:hover {
    background: #005bb5;
  }

  .continue {
    background: #ddd;
    color: #333;
  }

  .continue:hover {
    background: #bbb;
  }
</style>
