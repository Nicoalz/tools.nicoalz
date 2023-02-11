<script>
	import '../app.css';
	import Menu from '../libs/components/Menu.svelte';
	import MenuMobile from '../libs/components/MenuMobile.svelte';
	import IoIosMenu from 'svelte-icons/io/IoIosMenu.svelte';
	let isMenuOpen = false;
</script>

<div class="container flex flex-col items-center justify-center w-full mx-auto">
	<header class="w-full flex justify-between sm:justify-center items-center my-8 px-10 sm:px-0">
		<div class="block sm:hidden">
			<button class="h-10 w-10 text-black" on:click={() => (isMenuOpen = !isMenuOpen)}>
				<IoIosMenu />
			</button>
			<div>
				<MenuMobile bind:isMenuOpen />
			</div>
		</div>
		<div>
			<a href="/" class="text-blue-300 text-4xl sm:text-7xl border-white font-bold inline-block">
				<h1>tools.nicoalz</h1></a
			>
		</div>
	</header>

	<div class="flex flex-col justify-between w-full">
		<div class="w-full mb-8 hidden sm:block">
			<Menu />
		</div>
		<div class="w-full max-w-5xl mx-auto px-4 sm:px-0">
			<slot />
		</div>
	</div>
</div>
