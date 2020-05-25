<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		font-weight: 400;
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
		padding-bottom: 1em;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<svelte:head>
	<title>a minimal sapper blog</title>
</svelte:head>
<p>welcome to</p>
<h1>the<b>blog.</b></h1>

<figure>
	<img alt='the birds on a line' src='bird-bg.png'>
	<figcaption>where less is more</figcaption>
</figure>

<p><strong>we're minimal and that might seem boring, except you're actually paying attention.</strong></p>
<p class="link"><a href="about">find out why</a>...</p>