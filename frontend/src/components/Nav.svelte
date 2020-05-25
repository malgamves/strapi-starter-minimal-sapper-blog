<script>
	export let segment;
</script>

<style>
	nav {
		border-bottom: 1px solid rgba(21, 10, 34, 0.1);
		font-weight: 400;
		padding: 0 1em;
	}

	ul {
		margin: 0;
		padding: 0;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
		float: left;
	}

	[aria-current] {
		position: relative;
		display: inline-block;
	}

	[aria-current]::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 2px;
		background-color: black;
		display: block;
		bottom: -1px;
	}

	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
	}

	b {
		padding-right: 3em;
	}
</style>

<nav>
	<ul>
		<li><a aria-current='{segment === undefined ? "page" : undefined}' href='.'>the<b>blog.</b></a></li>
		<li><a aria-current='{segment === "about" ? "page" : undefined}' href='about'>about</a></li>


		<!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
		<li><a rel=prefetch aria-current='{segment === "articles" ? "page" : undefined}' href='articles'>articles</a></li>
	</ul>
</nav>
