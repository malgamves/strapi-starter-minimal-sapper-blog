<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<script context="module">
	import ApolloClient, { gql } from 'apollo-boost';  
	//import blogQuery from '.../data/blogposts.gql';

	// 1. Create an Apollo client and pass it to all child components
	//    (uses svelte's built-in context)
	const blogQuery = gql`
	query Blogs {  
		blogs {
			id
			Title
			Decription
			Body
			Cover {
			url
			}
		}
	}
	`;
	export async function preload({params, query}) {
		const client = new ApolloClient({ 
			uri: 'http://localhost:1337/graphql',
			fetch: this.fetch
			 });
		const results = await client.query({
			query: blogQuery
		})

		return {posts: results.data.blogs}
	}

</script>

<script>
	export let posts;
</script>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

<ul>
	{#each posts as post}
		<h2>{post.Title}</h2>
		<h3>{post.Decription}</h3>
		<img alt='Success Kid' src={'http://localhost:1337' + post.Cover.url}>
	{/each}
</ul>