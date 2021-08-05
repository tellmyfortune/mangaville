<script>
let manga = [], text = '', decoding = false;
var reader;
function checkFileAPI() {
        if (window.File && window.FileReader && window.FileList && window.Blob) {
            reader = new FileReader();
            return true; 
        } else {
            alert('The File APIs are not fully supported by your browser. Fallback required.');
            return false;
        }
    }

    let files, input, path;
    $: {console.log(files)
        
    path = document.getElementById("file");
    console.log(path)
    }

    const onChange = (event) => {
  const value = event.target.value;

  // this will return C:\fakepath\somefile.ext
  console.log(value);

}

let title = "";

const generate = () => {
    manga = text.split(",");
    text = "";
    console.log("pu chiki chiki")
    console.log(`${manga[0]} ${manga[1]}`)
}

$: title = `${manga[0]} ${manga[1]}`;

</script>



<div class="flex-grow w-full overflow-y-hidden flex justify-center flex-col items-center">
 
    <img src="cover.jpg" class="w-full flex content-center" alt="MangaVille Cover" />
    <div class="max-x-6xl w-5/6 text-xl text-white font-light mt-5 lg:px-14 px-0 text-center">MangaVille is the fastest Manga Reader you will ever find. All you need is to go to our <a href="https://www.youtube.com/channel/UCKSqc_By2ak-KwAkZdBS_9A/playlists" target="_blank"><b class="text-purple-600">YouTube Channel</b></a>, Find your favourite Manga Playlist, Copy some encoded texts from the link given in the discription and then paste it here. Boom! All done!<br>Happy Reading!</div>
    <label class="flex flex-col lg:flex-row items-center lg:items-center lg:justify-center mt-10 w-5/6 space-y-4 lg:space-x-6 max-w-6xl">
            <div class="w-52 flex flex-col flex-none items-center px-4 py-2 bg-purple-700 text-blue rounded-lg shadow-lg tracking-wide uppercase  cursor-pointer hover:bg-blue hover:bg-purple-800">
                <svg class="w-10 h-10" fill="white" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                    <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
                <span class="mt-1 text-base font-normal leading-normal text-white">{files?.[0] ? files[0].name : 'Select a Text file'}</span>
                <input type='file' id="file" class="hidden" bind:files bind:this={input} on:change={onChange}>
            </div>
            <div class="text-gray-200 text-4xl font-light">
                Or
            </div>
            <textarea id="message" placeholder="Paste here..." bind:value={text}  name="message" class="w-full bg-gray-700 bg-opacity-50 rounded border-2 border-gray-800 focus:border-purple-700 h-40 text-base outline-none text-gray-700 py-1 px-3 resize-none leading-6 transition-colors duration-200 ease-in-out"></textarea>
    </label>
    <button class="px-5 py-3 mt-10 text-white text-base font-normal uppercase rounded bg-purple-700" on:click={generate}>Generate</button>
    {#if title !== "undefined undefined" }
    <div class="mt-10 text-3xl font-light text-white" >{title}</div>
    <br>
    {/if}

    {#if manga !== null}
        {#each manga as imageText, i}
        {#if i>1 }
        <img src="data:image/jpeg;base64,{imageText}" alt="One Punch Man"/>
        <br>
        <br>
        {/if}
        {/each}
    {/if}
</div>