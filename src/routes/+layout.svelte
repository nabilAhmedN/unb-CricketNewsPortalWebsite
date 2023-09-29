<script>
	import Header from '$lib/components/Header.svelte';
	import '../app.css';
	import Footer from '../lib/components/Footer.svelte';
	import MainPage2 from '../lib/components/MainPage2.svelte';
	import MainPage3 from '../lib/components/MainPage3.svelte';
	import MainPage4 from '../lib/components/MainPage4.svelte';
	import MainPageDublicate from '../lib/components/MainPageDublicate.svelte';
	import MatchInfo from '../lib/components/MatchInfo.svelte';
</script>

<Header />
<!-- <MainPage /> -->
<MainPageDublicate />
<MainPage2 />
<MainPage3 />
<MainPage4 />
<!-- <ApiData/> -->
<MatchInfo />
<Footer />

<slot />
