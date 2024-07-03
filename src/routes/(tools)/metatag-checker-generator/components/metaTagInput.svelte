<script>
  import { createEventDispatcher } from "svelte";

  export let url = "https://metatags.io/";
  export let loading = false;

  let isValidUrl = true;
  let errorMessage = "";

  const dispatch = createEventDispatcher();

  function validateUrl(input) {
    const urlPattern =
      /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
    return urlPattern.test(input);
  }

  function handleInput() {
    isValidUrl = validateUrl(url);
    errorMessage = isValidUrl ? "" : "Please enter a valid URL";
  }

  function handleCheck() {
    if (validateUrl(url)) {
      isValidUrl = true;
      errorMessage = "";
      dispatch("check", { url });
    } else {
      isValidUrl = false;
      errorMessage = "Please enter a valid URL";
    }
  }

  // function handleCheck() {
  //   dispatch("check", { url });
  // }
</script>

<div class="my-4 flex">
  <input
    type="text"
    bind:value={url}
    on:input={handleInput}
    placeholder="https://google.com"
    class="rounded-md w-full md:w-48 focus:outline-none focus:ring-2 focus:ring-blue-500 h-10 px-3 border border-gray-300"
  />
  <button
    on:click={handleCheck}
    class="bg-black text-sm p-2 px-2 text-white rounded-md ml-3 hover:bg-gray-800 transition duration-200 ease-in-out"
    disabled={loading || !isValidUrl}
  >
    {#if loading}
      Checking...
    {:else}
      <span class="block sm:hidden">Check</span>
      <span class="hidden sm:block">Check MetaTags</span>
    {/if}
  </button>
  {#if errorMessage}
    <p class="text-red-500 text-sm mt-1">{errorMessage}</p>
  {/if}
</div>
