<script>
  import "../styles/Cart.css";

  let cartItems = [
    {
      name: "Mechanical Keyboard",
      itemNo: "KB-12345",
      size: "Full Size",
      color: "Black",
      qty: 1,
      price: 120.0,
      image: "public/keyboard.jpg",
    },
    {
      name: "Wireless Headphones",
      itemNo: "HP-67890",
      size: "One Size",
      color: "Matte Black",
      qty: 1,
      price: 250.0,
      image: "public/headphones.jpg",
    },
    {
      name: "Gaming Laptop",
      itemNo: "LT-54321",
      size: "15-inch",
      color: "Silver",
      qty: 1,
      price: 1500.0,
      image: "public/laptop.jpg",
    },
  ];

  let subtotal = cartItems.reduce((acc, item) => acc + item.price, 0);

  let showSpecs = {}; // Store dropdown states

  function toggleSpecs(index) {
    showSpecs[index] = !showSpecs[index];
    showSpecs = { ...showSpecs }; // Ensure reactivity
  }
</script>

<div class="cart-container">
  <h2>MY SHOPPING BAG</h2>
  <div class="cart-items">
    {#each cartItems as item, index}
      <div class="cart-item">
        <img src={item.image} alt={item.name} />
        <div class="item-details">
          <h3>{item.name}</h3>
          <p>ITEM NO: {item.itemNo}</p>
          <button class="toggle-btn" on:click={() => toggleSpecs(index)}>
            {showSpecs[index] ? "Hide Details" : "View More"}
          </button>
          <div class="specs" style="max-height: {showSpecs[index] ? '200px' : '0'}; opacity: {showSpecs[index] ? '1' : '0'};">
            <p>SIZE: {item.size}</p>
            <p>COLOR: {item.color}</p>
            <p>QTY: {item.qty}</p>
          </div>
        </div>
        <div class="price">${item.price.toFixed(2)}</div>
      </div>
    {/each}
  </div>
  
  <div class="summary">
    <h3>SUMMARY</h3>
    <div class="promo">
      <input type="text" placeholder="Do you have a promo code?" />
      <button>APPLY</button>
    </div>
    <p><strong>SUBTOTAL:</strong> ${subtotal.toFixed(2)}</p>
    <p>Shipping: TBD</p>
    <p>Sales Tax: TBD</p>
    <p><strong>ESTIMATED TOTAL:</strong> ${subtotal.toFixed(2)}</p>
    <button class="checkout">CHECKOUT</button>
  </div>
</div>
