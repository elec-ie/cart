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
  let showSpecs = {};

  function toggleSpecs(index) {
    showSpecs[index] = !showSpecs[index];
    showSpecs = { ...showSpecs };
  }
</script>

<div class="cart-container">
  <h1 class="cart-header">MY SHOPPING BAG</h1>
  
  <div class="cart-body">
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
            <div class="specs {showSpecs[index] ? 'open' : ''}">
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
        <button class="dark-btn">APPLY</button>
      </div>
      <div class="billdetails">
        <div class="bill-row">
          <span>SUBTOTAL:</span> <span>${subtotal.toFixed(2)}</span>
        </div>
        <div class="bill-row">
          <span>Shipping:</span> <span>TBD</span>
        </div>
        <div class="bill-row">
          <span>Sales Tax:</span> <span>TBD</span>
        </div>
        <div class="bill-row" style="font-weight: bold; border-top: 2px solid #555; padding-top: 8px;">
          <span>ESTIMATED TOTAL:</span> <span>${subtotal.toFixed(2)}</span>
        </div>
      </div>      
      <button class="checkout dark-btn">CHECKOUT</button>
    </div>
  </div>
</div>  