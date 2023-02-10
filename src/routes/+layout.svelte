<script>
	import '../app.css';
	import Menu from '../libs/components/Menu.svelte';
</script>

<div class="container flex flex-col items-center justify-center w-full mx-auto">
	<h1 class="text-blue-300 text-3xl font-bold mb-12">tools.nicoalz</h1>
	<div class="flex w-full">
		<div class="w-2/12">
			<Menu />
		</div>
		<div class="w-10/12">
			<slot />
		</div>
	</div>
</div>
