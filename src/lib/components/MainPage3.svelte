<script>
	import axios from 'axios';
	import { onMount } from 'svelte';

	let newsData = [];

	function processNewsDetails(details) {
		const withoutTags = details.replace(/<[^>]*>/g, ''); 
		const lines = withoutTags.split('\n'); 
		return lines.slice(0, 2).join('\n'); 
	}

	onMount(async () => {
		try {
			const response = await axios.get('https://unb.com.bd/api/bn/sports'); 
			newsData = response.data;
			console.log(newsData);
		} catch (error) {
			console.error('Error fetching data:', error);
		}
	});
</script>

<div class="container mx-auto">
	<div class="pt-14 m-6">
		<div class="flex justify-between">
			<h1 class="font-bold text-2xl">আইসিসি ক্রিকেট বিশ্বকাপ ভারত ২০২৩</h1>
			<button class="font-medium text-base text-[#d20a46]"
				><a
					href="https://unb.com.bd/bangla/subcategory/14/%E0%A6%95%E0%A7%8D%E0%A6%B0%E0%A6%BF%E0%A6%95%E0%A7%87%E0%A6%9F"
					>আরও দেখুন</a
				>
			</button>
		</div>

		<div class="grid grid-cols-1 lg:grid-cols-2 pt-9 gap-6">
			{#each newsData as category}
				{#each category.items.slice(0, 4) as newsItem}
					<div class="flex flex-col lg:flex-row">
						<div class="min-w-full lg:min-w-[295px] max-w-[295px] mr-0 lg:mr-5">
							{#if newsItem.pic}
								<div class="image-container">
									<img class="rounded-t-lg lg:rounded-lg" src={newsItem.pic} alt={newsItem.title} />
								</div>
							{/if}
						</div>
						<div class="border-[1px] rounded-b-lg lg:rounded-xl hover:shadow-md">
							<h1 class="font-bold text-lg hover:text-[#FF00A5] p-4">
								<a href={newsItem.source_url} target="_blank">{newsItem.title}</a>
							</h1>
						</div>
					</div>
				{/each}
			{/each}
		</div>
	</div>
</div>

<style>
	.image-container {
		display: inline-block;
		overflow: hidden; 
		position: relative;
	}

	.image-container img {
		transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
		max-width: 100%;
	}

	.image-container:hover img {
		transform: scale(1.1); 
		opacity: 0.8; 
	}
</style>
