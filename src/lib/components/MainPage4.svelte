<script>
	import cover from '$lib/images/download.svg';

	import axios from 'axios';
	import { onMount } from 'svelte';

	let newsData = [];
	let frontData = [];

	function processNewsDetails(details) {
		const withoutTags = details.replace(/<[^>]*>/g, ''); 
		const lines = withoutTags.split('\n'); 
		return lines.slice(0, 2).join('\n'); 
	}

	onMount(async () => {
		try {
			const response = await axios.get('https://unb.com.bd/api/video-galleries'); 
			newsData = response.data.slice(1, 5);
			frontData = response.data.slice(0, 1);
			console.log(newsData);
		} catch (error) {
			console.error('Error fetching data:', error);
		}
	});
</script>

<div id="photo-album" class="bg-cover mt-20 pb-20" style="background-image: url('{cover}') ">
	<div class="container mx-auto">
		<div class="flex justify-between pt-20 px-4">
			<h1 class="font-bold text-4xl text-[#ffffff]">Photos / Featured Videos</h1>
			<button class="font-medium text-base text-[#ffffff] hover:text-[#FF00A5]"><a href="https://www.unb.com.bd/subcategory/20/Cricket" target="_blank">See All</a></button>
		</div>

		<div class="flex flex-col lg:flex-row px-4 pt-8 gap-8">
			{#each frontData as category}
				<div class="flex flex-col">
					<a href={category.sourceUrl}>
						<div class="image-container">
							<img class="w-[78rem] rounded-lg" src={category.imageLink} alt="" />
						</div>
						<div class="pt-6 font-bold text-2xl">
							<h1 class="text-[#ffffff] hover:text-[#FF00A5]">
								
								<a href={category.sourceUrl} target="_blank">{category.title}</a>
							</h1>
						</div>
					</a>
				</div>
			{/each}

			<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-8">
				{#each newsData as category}
					<div>
						{#if category.imageLink}
							<div class="relative image-container">
								<img src={category.imageLink} alt="" class="w-full h-auto rounded-lg" />
								<div class="absolute inset-0 flex items-center justify-center">
									<button class="bg-white text-gray-800 rounded-full p-1 hover:bg-gray-200">
										<svg
											xmlns="http://www.w3.org/2000/svg"
											width="40"
											height="40"
											viewBox="0 0 32 32"
											><path
												fill="none"
												d="M11 23a1 1 0 0 1-1-1V10a1 1 0 0 1 1.447-.894l12 6a1 1 0 0 1 0 1.788l-12 6A1.001 1.001 0 0 1 11 23Z"
											/><path
												fill="#320073"
												d="M16 2a14 14 0 1 0 14 14A14 14 0 0 0 16 2Zm7.447 14.895l-12 6A1 1 0 0 1 10 22V10a1 1 0 0 1 1.447-.894l12 6a1 1 0 0 1 0 1.788Z"
											/></svg
										>
									</button>
								</div>
							</div>
						{/if}
						<div>
							<h1 class="font-medium text-base text-[#ffffff] hover:text-[#FF00A5] pt-5">
								<a href={category.sourceUrl} target="_blank">{category.title}</a>
							</h1>
						</div>
					</div>
				{/each}
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
