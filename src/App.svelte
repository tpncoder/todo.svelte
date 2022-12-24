<script>
import ItemAction  from './lib/ItemAction.svelte'
import Notifications from 'svelte-notifications';
</script>

<svelte:head>
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Overpass">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" />
</svelte:head>

<main>
	<Notifications>	
		<ItemAction/>
	</Notifications>	
</main>
