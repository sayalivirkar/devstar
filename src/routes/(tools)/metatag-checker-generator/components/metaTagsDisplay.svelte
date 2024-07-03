<script>
  import { fade } from "svelte/transition";

  export let metaTags = null;
  export let error = null;
  export let url = "";
  export let loading = false;
</script>

{#if error}
  <p class="text-red-500 text-center w-full md:w-[50%] mt-8 flex-auto p-5 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">{error}</p>
{:else}
  <div
    class="w-full md:w-[50%] mt-8 flex-auto p-5 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
    transition:fade
  >
    {#if loading}
      <h2
        class="text-xl mb-4 text-center font-extrabold tracking-tight leading-none text-gray-900 border-b pb-4 dark:text-white"
      >
        Loading Meta Tags...
      </h2>
      <div class="flex justify-center items-center h-32">
        <div
          class="animate-spin rounded-full h-16 w-16 border-t-2 border-b-2 border-gray-900 dark:border-white"
        ></div>
      </div>
    {:else if metaTags}
      <div>
        <h2
          class="text-xl mb-4 text-center font-extrabold tracking-tight leading-none text-gray-900 border-b pb-4 dark:text-white"
        >
          Meta Tags for {url}
        </h2>
        <ul class="space-y-2">
          {#each Object.entries(metaTags.metaTags) as [key, value]}
            <li class="dark:text-white"><strong>{key}:</strong> {value}</li>
          {/each}
        </ul>
      </div>
    {/if}
  </div>
{/if}
