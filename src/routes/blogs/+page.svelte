<script>
	import BlogCard from '$lib/components/blog/BlogCard.svelte';
	import { onMount } from 'svelte';

	let blogs = [];

	onMount(async () => {
		// Get all JSON files from the blogs folder
		const blogFiles = import.meta.glob('/static/blogs/*.json');
		
		// Load all blog files
		const blogPromises = Object.entries(blogFiles).map(async ([path, resolver]) => {
			const response = await fetch(path.replace('/static', ''));
			return await response.json();
		});
		
		blogs = await Promise.all(blogPromises);
		
		// Sort blogs by date (newest first)
		blogs.sort((a, b) => new Date(b.date) - new Date(a.date));
	});
</script>

<div class="blogs-container">
	<h1>Blog Posts</h1>
	<p class="subtitle">Thoughts, tutorials, and insights on web development and technology</p>

	<div class="blog-list">
		{#each blogs as blog}
			<BlogCard
				title={blog.title}
				description={blog.description}
				fullContent={blog.fullContent}
				imageUrl={blog.imageUrl}
				tags={blog.tags}
				date={blog.date}
				readTime={blog.readTime}
			/>
		{/each}
	</div>
</div>

<style>
	.blogs-container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 2rem 0;
	}

    h1 {
        margin-bottom: 1.5rem;
    }

	.subtitle {
		color: #94a3b8;
		font-size: 1.1rem;
		margin-bottom: 3rem;
	}

	.blog-list {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	@media (max-width: 768px) {
		h1 {
			font-size: 2rem;
		}

		.subtitle {
			font-size: 1rem;
		}
	}
</style>

