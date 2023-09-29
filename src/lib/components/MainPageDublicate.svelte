<script>
	import axios from 'axios';
	import { onMount } from 'svelte';

	let newsData = [];

	
	function processNewsDetails(details) {
		const withoutTags = details.replace(/<[^>]*>/g, ''); 
		const lines = withoutTags.split('\n'); 

		if (lines.length >= 3) {
			return lines.slice(1, 3).join('\n'); 
		} else {
			return withoutTags; 
		}
	}

	onMount(async () => {
		try {
			const response = await axios.get('https://unb.com.bd/api/en/cricket'); 
			newsData = response.data;
			console.log(newsData);
		} catch (error) {
			console.error('Error fetching data:', error);
		}
	});
</script>

<div class="bg-[#320073]">
	<div class="container mx-auto">
		<div class="flex flex-col lg:flex-row px-7 lg:px-4 pt-14 pb-36 gap-4">
			{#each newsData as category}
				{#each category.items.slice(0, 1) as newsItem}
					<div class="w-full lg:w-[48%]">
						<a href={newsItem.source_url}>
							{#if newsItem.pic}
								<div class="image-container">
									<img class="rounded-lg " src={newsItem.pic} alt="" />
								</div>
							{/if}
							<h1 class="text-slate-200 hover:text-[#FF00A5] font-bold lg:text-[32px] pt-3">
								<a href={newsItem.source_url} target="_blank">{newsItem.title}</a>
							</h1></a
						>
						<p class="text-slate-200 pt-3 text-xl hidden md:block">
							{#if newsItem.news_details}
								{processNewsDetails(newsItem.news_details)}...
							{/if}
						</p>
					</div>
				{/each}
			{/each}
			<div class="flex-1">
				<div class="grid grid-cols-2 gap-4">
					{#each newsData as category}
						{#each category.items.slice(1, 5) as newsItem}
							<div>
								<div class="image-container">
									<img src={newsItem.pic} alt="" class="rounded-lg" />
								</div>
								<h1 class="mt-2 text-slate-200 hover:text-[#FF00A5] text-xs lg:text-xl font-bold pt-3">
									<a href={newsItem.source_url} target="_blank">{newsItem.title}</a>
								</h1>
							</div>
						{/each}
					{/each}
				</div>
			</div>
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
