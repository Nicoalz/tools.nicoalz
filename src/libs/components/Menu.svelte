<script>
	import { toolsLinks } from '../data/toolsLinks';
</script>

<ul class="menu">
	{#each toolsLinks as link}
		<li class="menu__item">
			<a class="menu__link" href={link.path}>{link.name}</a>
		</li>
	{/each}
</ul>
