<script>
  let imageUrl = "";
  let imageName = "";

  // upload functionality to show name of file and display preview
  function handleFileChange(event) {
    const file = event.target.files[0];
    if (file) {
      imageUrl = URL.createObjectURL(file);
      imageName = file.name;
    }
  }
</script>

<!-- <div class="flex flex-col mt-8"> -->
<!-- container -->
<div
  class="mr-0 mt-0 md:mr-10 md:mt-8 p-5 h-fit bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 w-full md:w-[40%]"
>
  <!-- heading div -->
  <div
    class="text-xl mb-4 text-center font-extrabold tracking-tight leading-none text-gray-900 pb-4 border-b dark:text-white"
  >
    <h1>MetaTag Generator</h1>
  </div>
  <!-- form with input like dragdrop title and descrp -->
  <form class="max-w-md mx-auto">
    <div class="flex flex-col mb-5">
      <h1 class="text-sm text-gray-500 dark:text-gray-400 m-1">Image</h1>
      <div class="flex items-center justify-center w-full">
        <label
          for="dropzone-file"
          class="flex flex-col items-center justify-center w-full h-64 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50 dark:bg-gray-700 hover:bg-gray-100 dark:border-gray-600 dark:hover:border-gray-500 dark:hover:bg-gray-600 relative"
        >
          {#if imageUrl}
            <img
              src={imageUrl}
              alt="Selected pic"
              class="absolute inset-0 w-full h-full object-cover rounded-lg"
            />
            <div
              class="absolute inset-0 w-full h-full bg-gray-900 bg-opacity-50 flex items-center justify-center"
            >
              <span class="text-white text-sm">{imageName}</span>
            </div>
          {:else}
            <div class="flex flex-col items-center justify-center pt-5 pb-6">
              <svg
                class="w-8 h-8 mb-4 text-gray-500 dark:text-gray-400"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 20 16"
              >
                <path
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M13 13h3a3 3 0 0 0 0-6h-.025A5.56 5.56 0 0 0 16 6.5 5.5 5.5 0 0 0 5.207 5.021C5.137 5.017 5.071 5 5 5a4 4 0 0 0 0 8h2.167M10 15V6m0 0L8 8m2-2 2 2"
                />
              </svg>
              <p class="mb-2 text-sm text-gray-500 dark:text-gray-400">
                <span class="font-semibold">Click to upload</span> or drag and drop
              </p>
              <p class="text-xs text-gray-500 dark:text-gray-400">
                SVG, PNG, JPG (MAX. 800x400px)
              </p>
            </div>
          {/if}
          <input
            id="dropzone-file"
            type="file"
            class="hidden"
            on:change={handleFileChange}
          />
        </label>
      </div>
    </div>
    <div class="relative z-0 w-full mb-5 group">
      <input
        type="text"
        name="floating_title"
        id="floating_title"
        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer"
        placeholder=" "
        required
      />
      <label
        for="floating_title"
        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6"
        >Title</label
      >
    </div>
    <div class="relative z-0 w-full mb-5 group">
      <label
        for="message"
        class="text-sm text-gray-500 block mb-2 font-medium dark:text-white"
        >Your message</label
      >
      <textarea
        id="message"
        rows="4"
        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        placeholder="Write your thoughts here..."
      ></textarea>
    </div>

    <div class="flex justify-center items-center">
      <button
        type="submit"
        class="text-white bg-gray-700 hover:bg-gray-800 focus:ring-4 focus:outline-none focus:ring-gray-300 font-medium rounded-lg text-sm w-full sm:w-auto px-10 py-2.5 text-center dark:bg-gray-600 dark:hover:bg-gray-700 dark:focus:ring-blue-800"
        >Get Code</button
      >
    </div>
  </form>
</div>

<!-- </div> -->
