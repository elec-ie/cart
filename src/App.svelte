<script>
  import Cart from "./routes/Cart.svelte";
</script>

<main>
  <Cart />
</main>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(to right, #ffffff, #f6f6f6);
    font-family: 'SF Pro Display', sans-serif;
  }
</style>
