<script lang="ts">
  import axios from 'axios'
  import svelteLogo from './assets/svelte.svg'
  import Counter from './lib/Counter.svelte'
  let isLoading = false
  let url = ""
  let res = null

</script>

<main>
  <input bind:value={url}>
  <button disabled={isLoading} on:click={async()=>{
    try {
      res = null
       isLoading = true
      res =await axios.post("https://localhost:3000/url",{url})
     
      isLoading = false

    } catch (error) {
      console.log(error)
    }
   }}>submit</button>
{#if isLoading}
<h1>loading....</h1>
{/if}

{#if res!=null}
   <img src={"https://"+res.data.imageLink} alt=""/>
   <p>sku name {res.data.skuName}</p>
   <p>productName {res.data.productName}</p>
   <p>price {res.data.price}</p>
{/if}
   



</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>