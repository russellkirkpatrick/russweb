<script>
	import '../app.css';

	import Footer from '../lib/Footer.svelte'
	let { children } = $props();
</script>



{@render children()}

<Footer />
