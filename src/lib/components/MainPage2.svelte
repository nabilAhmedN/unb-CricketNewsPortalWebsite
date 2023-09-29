<script>
	import axios from 'axios';
	import { onMount } from 'svelte';

	let newsData = [];

	// Remove html tag
	function processNewsDetails(details) {
		const withoutTags = details.replace(/<[^>]*>/g, ''); 
		const lines = withoutTags.split('\n'); // Split text into lines
		return lines.slice(0, 2).join('\n'); // Line Limit 
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

<div>
	<div class="container mx-auto">
		<div class="flex flex-col lg:flex-row pt-14 m-6">
			<div class="w-auto lg:w-2/3">
				<div class="flex justify-between">
					<h1 class="font-bold text-[36px]">More Story</h1>
					<button class="text-[#dc4aa9] font-medium text-base">
						<a href="https://unb.com.bd/news/tag/44747">See All</a>
					</button>
				</div>
				{#each newsData as category}
					{#each category.items.slice(6, 10) as newsItem}
						<div class="flex flex-col lg:flex-row lg:gap-4 mb-4 pt-6">
							<div class="min-w-full lg:min-w-[295px] max-w-[324px]">
								{#if newsItem.pic}
									<div class="image-container">
										<img class=" rounded-t-lg lg:rounded-lg" src={newsItem.pic} alt="" />
									</div>
								{/if}
							</div>
							<div class="border-[1px] rounded-b-lg lg:rounded-xl hover:shadow-md">
								<h1 class="font-bold text-2xl px-8 py-[30px] hover:text-[#FF00A5] news-title">
									<a href={newsItem.source_url}>
										{newsItem.title}
									</a>
								</h1>
							</div>
						</div>
					{/each}
				{/each}
			</div>
			<div class="lg:ml-4">
				<div class="bg-[#FF00A5] rounded-xl p-4">
					<h1 class="text-[#fff] text-center font-bold text-lg">Prediction</h1>
					<div class="lg:w-[23rem] pt-3">
						<img
							src="https://cosmosgroup.sgp1.cdn.digitaloceanspaces.com/cwc/quiz_one/WaKdifSDoQ3uK89lLlTFKVKbhGYJGsQwFBCLk5TY.jpg"
							alt=""
						/>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>
<hr />

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
