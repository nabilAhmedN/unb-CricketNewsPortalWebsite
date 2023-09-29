<script>
    export let product;
  </script>
  
  <h1>Product Details</h1>
  
  {#if product}
    <div>
      <h2>{product.title}</h2>
      <p>{product.description}</p>
      
    </div>
  {:else}
    <p>No product selected</p>
  {/if}
  