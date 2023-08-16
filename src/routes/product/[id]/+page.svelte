<script>
	import { page } from '$app/stores';
	import ProductHeader from './ProductHeader.svelte';

	$: console.log($page);
</script>

<ProductHeader />
<h1>product: {$page.params.id}</h1>
