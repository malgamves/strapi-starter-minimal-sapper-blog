<script context="module">
	import ApolloClient, { gql } from 'apollo-boost';  
	import moment from 'moment'

	// 1. Create an Apollo client and pass it to all child components
	//    (uses svelte's built-in context)
	const blogQuery = gql`
	query Blogs($Slug: String!) {
		blogs: blogs(where: { Slug: $Slug }) {
			id
			Title
			Description
			Published
			Body
			author {
				username
			}
			Slug
			Cover {
			url
			previewUrl
			alternativeText
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
			query: blogQuery,
			variables: {"Slug" : params.slug} 
		})

		return {post: results.data.blogs}
	}

</script>

<script>
	export let post;
</script>

<style>
	/*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
	*/
	.content :global(h2) {
		font-size: 1.4em;
		font-weight: 500;
	}

	.content :global(pre) {
		background-color: #f9f9f9;
		box-shadow: inset 1px 1px 5px rgba(0,0,0,0.05);
		padding: 0.5em;
		border-radius: 2px;
		overflow-x: auto;
	}

	.content :global(pre) :global(code) {
		background-color: transparent;
		padding: 0;
	}

	.content :global(ul) {
		line-height: 1.5;
	}

	.content :global(li) {
		margin: 0 0 0.5em 0;
	}
</style>

<svelte:head>
	<title>{post.Title}</title>
</svelte:head>

{#each post as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<h1>{post.Title}</h1>
		<h3>{moment().to(post.Published)} by {post.author.username}</h3>

		<div class='content'>
	{@html post.Body} </div>

{/each}

