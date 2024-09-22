<script lang="ts">
    import { page } from '$app/stores';
    import { browser } from '$app/environment';
    import { onMount } from 'svelte';

	let info = [
		{text: "ask", url: "https://dontasktoask.com"},
		{text: "hello", url: "https://nohello.net/en/"},
		{text: "try", url: "https://tryitands.ee"}]

	function sleep(ms) {
		return new Promise((resolve) => setTimeout(resolve, ms));
	}

	async function wait(ms, access) {
		await sleep(ms);
		window.location.href = access.url;
	}

	onMount(() => {
		const param = $page.url.searchParams;
		const str = param.toString().slice(0, -1);
		for (const element in info) {
			if (info[element].text == str) {
				if (browser) {
					wait(2000, info[element]);
				}
				break;
			}
		}
	})

</script>

{#each info as {text, url}, _}
    {text}: <a href={url}>{url}</a>
    <br>
{/each}



<p>I will list here some useful links for interacting with people. In case I get the feeling someone wastes my or even their own time with useless stuff. </p>


<br> how to use: /redirect?name
