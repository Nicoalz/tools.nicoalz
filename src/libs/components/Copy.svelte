<script>
	export let text;
	let isCopied = false;

	function copyText() {
		navigator.clipboard.writeText(text);
		isCopied = true;
		setTimeout(() => {
			isCopied = false;
		}, 2000);
	}
</script>

<button on:click={copyText} class="btn-brown text-xs">
	{#if isCopied}
		Copied!
	{:else}
		Copy
	{/if}
</button>
