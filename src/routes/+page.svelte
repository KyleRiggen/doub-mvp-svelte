<script lang="ts">
	import { onMount } from 'svelte';

	interface Player {
		summonerName: string;
		leaguePoints: number;
	}

	let photos = null;
	let list: Player[] = [];

	onMount(async () => {
		const res = await fetch(
			'https://na1.api.riotgames.com/lol/league/v4/challengerleagues/by-queue/RANKED_SOLO_5x5?api_key=RGAPI-e5abed89-b48f-4bf2-8727-3f1218874da0'
		);
		photos = await res.json();
		list = photos.entries;

		list.sort(function (a, b) {
			var keyA = new Date(a.leaguePoints),
				keyB = new Date(b.leaguePoints);
			// Compare the 2 dates
			if (keyA < keyB) return -1;
			if (keyA > keyB) return 1;
			return 0;
		});
	});
</script>

<h1>Player list</h1>
<ul>
	{#each list as item}
		<li>{item.leaguePoints} - {item.summonerName}</li>
	{/each}
</ul>
