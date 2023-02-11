<script>
	import { toolsLinks } from '../data/toolsLinks';
	export let isMenuOpen;
</script>

<ul
	class={`transform transition duration-300 z-20 absolute menu flex flex-col justify-start items-center bg-gray-700 top-0 left-0 w-[50%] h-full pt-20 ${
		isMenuOpen ? 'translate-x-0' : '-translate-x-full'
	}`}
>
	{#each toolsLinks as link}
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<li class="menu__item m-2" on:click={() => (isMenuOpen = false)}>
			<a class="menu__link  btn-link" href={link.path}>{link.name}</a>
		</li>
	{/each}
</ul>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div
	class={`transform transition duration-300 cursor-pointer absolute top-0 left-0 w-full h-full bg-black/50 z-10 ${
		!isMenuOpen && 'hidden'
	}`}
	on:click={() => (isMenuOpen = false)}
/>
