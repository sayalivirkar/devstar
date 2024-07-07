<script>
  export let url = "https://metatags.io/";
  export let loading = false;

  function handleCheck() {
    dispatch("check", { url });
  }
</script>

<div class="my-4 flex">
  <input
    type="text"
    bind:value={url}
    placeholder="https://google.com"
    class="rounded-md w-full md:w-48 focus:outline-none focus:ring-2 focus:ring-blue-500 h-10 px-3 border border-gray-300"
  />
  <button
    on:click={handleCheck}
    class="bg-black text-sm p-2 px-2 text-white rounded-md ml-3 hover:bg-gray-800 transition duration-200 ease-in-out"
    disabled={loading}
  >
    {#if loading}
      Checking...
    {:else}
      <span class="block sm:hidden">Check</span>
      <span class="hidden sm:block">Check MetaTags</span>
    {/if}
  </button>
</div>
