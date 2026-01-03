<script>
	import { browser } from '$app/environment';

	export let title;
	export let description;
	export let fullContent;
	export let imageUrl;
	export let tags = [];
	export let date;
	export let readTime;

	let isExpanded = false;

	function toggle() {
		isExpanded = !isExpanded;
	}

	function handleKeydown(event) {
		if (event.key === 'Enter' || event.key === ' ') {
			event.preventDefault();
			toggle();
		}
	}

	// Close expanded card with Escape key
	function handleExpandedKeydown(event) {
		if (event.key === 'Escape') {
			isExpanded = false;
		}
	}

	// Prevent background scroll when expanded
	$: {
		if (browser) {
			if (isExpanded) {
				document.body.style.overflow = 'hidden';
			} else {
				document.body.style.overflow = '';
			}
		}
	}
</script>

<!-- Compact Card -->
{#if !isExpanded}
	<div
		class="blog-card"
		role="button"
		tabindex="0"
		aria-label="Expand {title}"
		on:click={toggle}
		on:keydown={handleKeydown}
	>
		<div class="card-image">
			<img src={imageUrl} alt={title} />
		</div>
		<div class="card-content">
			<h3 class="card-title">{title}</h3>
			<p class="card-description">{description}</p>
			<div class="card-tags">
				{#each tags as tag}
					<span class="tag">{tag}</span>
				{/each}
			</div>
			<div class="card-meta">
				<span class="date">{date}</span>
				<span class="separator">•</span>
				<span class="read-time">{readTime}</span>
			</div>
		</div>
	</div>
{/if}

<!-- Expanded View (Modal) -->
{#if isExpanded}
	<div
		class="modal-overlay"
		role="dialog"
		tabindex="0"
		aria-modal="true"
		aria-label="Blog post details"
		on:click={toggle}
		on:keydown={handleExpandedKeydown}
	>
		<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
		<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
		<div class="modal" role="document" tabindex="0" on:click|stopPropagation on:keydown={() => {}}>
			<button class="close-btn" on:click={toggle} aria-label="Close">×</button>
			<div class="modal-header">
				<img src={imageUrl} alt={title} class="modal-image" />
				<h2 class="modal-title">{title}</h2>
				<div class="modal-tags">
					{#each tags as tag}
						<span class="tag">{tag}</span>
					{/each}
				</div>
				<div class="modal-meta">
					<span class="date">{date}</span>
					<span class="separator">•</span>
					<span class="read-time">{readTime}</span>
				</div>
			</div>
			<div class="modal-content">
				{@html fullContent}
			</div>
		</div>
	</div>
{/if}

<style>
	/* Compact Card Styles */
	.blog-card {
		display: flex;
		gap: 1.5rem;
		background-color: #1e293b;
		border: 1px solid #334155;
		border-radius: 12px;
		overflow: hidden;
		cursor: pointer;
		transition: all 0.3s ease;
		padding: 1.25rem;
		align-items: center;
	}

	.blog-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 8px 24px rgba(14, 165, 233, 0.2);
		border-color: #0ea5e9;
	}

	.card-image {
		flex-shrink: 0;
		width: 200px;
		height: 150px;
		border-radius: 8px;
		overflow: hidden;
	}

	.card-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.card-content {
		flex: 1;
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
		min-width: 0;
	}

	.card-title {
		font-size: 1.5rem;
		font-weight: 700;
		color: #0ea5e9;
		margin: 0;
		line-height: 1.3;
	}

	.card-description {
		font-size: 0.95rem;
		color: #cbd5e1;
		margin: 0;
		line-height: 1.5;
		display: -webkit-box;
		-webkit-line-clamp: 2;
		line-clamp: 2;
		-webkit-box-orient: vertical;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.card-tags {
		display: flex;
		flex-wrap: wrap;
		gap: 0.5rem;
	}

	.tag {
		background-color: #334155;
		color: #0ea5e9;
		padding: 0.25rem 0.75rem;
		border-radius: 16px;
		font-size: 0.8rem;
		font-weight: 500;
	}

	.card-meta {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		font-size: 0.85rem;
		color: #94a3b8;
	}

	.separator {
		color: #475569;
	}

	/* Modal Styles */
	.modal-overlay {
		position: fixed;
		inset: 0;
		background: rgba(0, 0, 0, 0.75);
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 1000;
		padding: 2rem;
	}

	.modal {
		background-color: #0f172a;
		border: 1px solid #334155;
		border-radius: 16px;
		width: 100%;
		max-width: 900px;
		max-height: 90vh;
		overflow-y: auto;
		box-shadow: 0 20px 60px rgba(14, 165, 233, 0.3);
		position: relative;
		padding: 2.5rem;
	}

	.close-btn {
		position: absolute;
		top: 1rem;
		right: 1rem;
		background: #334155;
		color: #e5e5e5;
		border: none;
		border-radius: 50%;
		width: 40px;
		height: 40px;
		font-size: 1.5rem;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: all 0.2s;
		z-index: 10;
	}

	.close-btn:hover {
		background: #475569;
		transform: scale(1.1);
	}

	.modal-header {
		margin-bottom: 2rem;
	}

	.modal-image {
		width: 100%;
		max-height: 400px;
		object-fit: cover;
		border-radius: 12px;
		margin-bottom: 1.5rem;
	}

	.modal-title {
		font-size: 2.5rem;
		font-weight: 700;
		color: #0ea5e9;
		margin: 0 0 1rem 0;
		line-height: 1.2;
	}

	.modal-tags {
		display: flex;
		flex-wrap: wrap;
		gap: 0.5rem;
		margin-bottom: 1rem;
	}

	.modal-meta {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		font-size: 0.95rem;
		color: #94a3b8;
	}

	.modal-content {
		color: #e5e5e5;
		line-height: 1.8;
		font-size: 1rem;
	}

	.modal-content :global(p) {
		margin-bottom: 1rem;
	}

	.modal-content :global(h1),
	.modal-content :global(h2),
	.modal-content :global(h3) {
		color: #0ea5e9;
		margin-top: 2rem;
		margin-bottom: 1rem;
	}

	.modal-content :global(code) {
		background: #1e293b;
		padding: 0.2rem 0.4rem;
		border-radius: 4px;
		font-family: 'Ubuntu Mono', monospace;
	}

	.modal-content :global(pre) {
		background: #1e293b;
		padding: 1rem;
		border-radius: 8px;
		overflow-x: auto;
		margin: 1rem 0;
	}

	/* Scrollbar styling */
	.modal {
		scrollbar-width: thin;
		scrollbar-color: #334155 #1e293b;
	}

	.modal::-webkit-scrollbar {
		width: 8px;
	}

	.modal::-webkit-scrollbar-track {
		background: #1e293b;
	}

	.modal::-webkit-scrollbar-thumb {
		background: #334155;
		border-radius: 4px;
	}

	.modal::-webkit-scrollbar-thumb:hover {
		background: #475569;
	}

	/* Responsive Design */
	@media (max-width: 768px) {
		.blog-card {
			flex-direction: column;
			padding: 1rem;
		}

		.card-image {
			width: 100%;
			height: 200px;
		}

		.card-title {
			font-size: 1.25rem;
		}

		.modal {
			padding: 1.5rem;
			margin: 1rem;
		}

		.modal-title {
			font-size: 1.75rem;
		}

		.modal-image {
			max-height: 250px;
		}
	}
</style>
