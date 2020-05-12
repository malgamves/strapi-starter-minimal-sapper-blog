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
			Description
			Published
			Body
			Slug
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

<style>
	ul {
		margin: 0 0 1em 0;
		line-height: 1.5;
	}
</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<h1>Recent posts</h1>

<ul>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<li><a rel='prefetch' href='blog/{post.Slug}'>{post.Title}</a></li>
	{/each}
</ul>