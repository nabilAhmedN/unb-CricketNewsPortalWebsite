<script>
  import { onMount } from 'svelte';
  import axios from 'axios';

  let newsData = [];

  // Function to remove HTML tags and limit text to two lines
  function processNewsDetails(details) {
    const withoutTags = details.replace(/<[^>]*>/g , ''); // Remove HTML tags
    const lines = withoutTags.split('\n'); // Split text into lines
    return lines.slice(0, 2).join('\n'); // Limit to two lines
  }

  onMount(async () => {
    try {
      const response = await axios.get('https://unb.com.bd/api/bn/sports'); // Replace with the actual URL to your JSON data
      newsData = response.data;
      console.log(newsData);
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  });
</script>

<div>
  {#each newsData as category}
    <h2>{category.category}</h2>
    <ul>
      {#each category.items as newsItem}
        <li>
          <a href={newsItem.source_url} target="_blank">{newsItem.title}</a>
          {#if newsItem.pic}
            <img src={newsItem.pic} alt={newsItem.title} />
          {/if}
          {#if newsItem.news_details}
            <p>{processNewsDetails(newsItem.news_details)}</p>
          {/if}
        </li>
      {/each}
    </ul>
  {/each}
</div>
