<script>
	import { toolsLinks } from '../data/toolsLinks';
</script>

<ul class="menu flex justify-center">
	{#each toolsLinks as link}
		<li class="menu__item m-2">
			<a class="menu__link  btn-link" href={link.path}>{link.name}</a>
		</li>
	{/each}
</ul>
