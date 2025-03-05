<script>
  export let products = [
    { id: 1, name: "MacBook Pro", price: 1999, image: "/laptop.jpg" },
    { id: 2, name: "Wireless Headphones", price: 299, image: "/headphones.jpg" },
    { id: 3, name: "Gaming Mouse", price: 79, image: "/mouse.jpg" }
  ];
</script>

<h2>🛍️ Products</h2>
<div class="products-container">
  {#each products as product}
    <div class="product-card">
      <img src={product.image} alt={product.name} />
      <div class="product-info">
        <h3>{product.name}</h3>
        <p>${product.price}</p>
      </div>
    </div>
  {/each}
</div>

<style>
  h2 {
    color: #333;
  }

  .products-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }

  .product-card {
    width: 250px;
    background: #fff;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    text-align: center;
    transition: transform 0.2s ease-in-out;
  }

  .product-card:hover {
    transform: scale(1.05);
  }

  .product-card img {
    width: 100%;
    height: 160px;
    object-fit: cover;
  }

  .product-info {
    padding: 15px;
  }

  .product-info h3 {
    margin: 5px 0;
    font-size: 18px;
  }

  .product-info p {
    color: #007bff;
    font-size: 16px;
    font-weight: bold;
  }
</style>
