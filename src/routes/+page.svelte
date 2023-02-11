<script>
	import { toolsLinks } from '../libs/data/toolsLinks';
</script>

<div class="flex flex-col items-center justify-center">
	<title>tools.nicoalz - home</title>
	<h1 class="title-green">home</h1>
	<p class="text-center my-10">
		This web app is a suite of usefool tools for daily use. <br />
		You can click on one of the tool you want to use it.
	</p>
	<ul class="flex menu sm:hidden flex-col justify-center items-center">
		{#each toolsLinks as link}
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<li class="menu__item m-2">
				<a class="menu__link  btn-link" href={link.path}>{link.name}</a>
			</li>
		{/each}
	</ul>
</div>
