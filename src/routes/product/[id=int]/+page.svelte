<script lang="ts">
	import { page } from '$app/stores';
	import type { PageData } from './$types';
	import ProductHeader from './ProductHeader.svelte';

	export let data: PageData;

	$: console.log($page);
</script>

{data.user.name}
<ProductHeader />
<h1>product: {$page.params.id}</h1>
