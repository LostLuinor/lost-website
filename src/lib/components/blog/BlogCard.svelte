<script>
	import { browser } from '$app/environment';
	import { onMount } from 'svelte';

	export let title;
	export let description;
	export let fullContent;
	export let imageUrl;
	export let tags = [];
	export let date;
	export let readTime;

	let isExpanded = false;
	let modalRef;

	function open() {
		isExpanded = true;
	}
	function close() {
		isExpanded = false;
	}
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
			close();
		}
	}

	// Prevent background scroll & focus modal when expanded
	$: if (isExpanded && browser) {
		document.body.style.overflow = 'hidden';
		requestAnimationFrame(() => modalRef && modalRef.focus());
	} else if (browser) {
		document.body.style.overflow = '';
	}

	onMount(() => {
		if (isExpanded && browser) modalRef && modalRef.focus();
	});
</script>

<!-- Compact Card -->
{#if !isExpanded}
	<div
		class="blog-card"
		role="button"
		tabindex="0"
		aria-label="Open blog post {title}"
		on:click={open}
		on:keydown={handleKeydown}
	>
		<div class="card-image">
			<img src={imageUrl} alt={title} />
			<div class="image-caption">
				<h3 class="card-title">{title}</h3>
				<div class="card-meta">
					<span class="date">{date}</span>
					<span class="separator">•</span>
					<span class="read-time">{readTime}</span>
				</div>
			</div>
		</div>

		<div class="card-content">
			<p class="card-description">{description}</p>
			<div class="card-tags">
				{#each tags as tag}
					<span class="tag">{tag}</span>
				{/each}
			</div>
		</div>
	</div>
{/if}

<!-- Expanded View (Modal) -->
{#if isExpanded}
	<div
		class="modal-overlay"
		role="dialog"
		aria-modal="true"
		aria-label="Blog post details"
		on:click={close}
		on:keydown={handleExpandedKeydown}
	>
		<div class="modal" role="document" tabindex="-1" bind:this={modalRef} on:click|stopPropagation>
			<button class="close-btn" on:click={close} aria-label="Close">
				<svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
					<path d="M18 6L6 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
					<path d="M6 6l12 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
				</svg>
			</button>

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
		gap: 1.25rem;
		background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
		border: 1px solid rgba(255,255,255,0.04);
		border-radius: 12px;
		overflow: hidden;
		cursor: pointer;
		transition: transform 0.18s ease, box-shadow 0.18s ease;
		padding: 0.9rem;
		align-items: stretch;
		max-width: 920px;
	}

	.blog-card:focus,
	.blog-card:hover {
		transform: translateY(-6px);
		box-shadow: 0 12px 36px rgba(2,6,23,0.45), 0 6px 16px rgba(14,165,233,0.06);
	}

	.card-image {
		position: relative;
		flex-shrink: 0;
		width: 260px;
		height: 160px;
		border-radius: 10px;
		overflow: hidden;
		box-shadow: inset 0 -40px 80px rgba(0,0,0,0.15);
	}

	.card-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		display: block;
		transition: transform 0.6s cubic-bezier(.2,.8,.2,1);
	}
	.blog-card:hover .card-image img,
	.blog-card:focus .card-image img { transform: scale(1.04); }

	.image-caption {
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;
		padding: 12px;
		background: rgba(0,0,0,0.78);
		color: #e6eef8;
	}

	.card-content {
		flex: 1;
		display: flex;
		flex-direction: column;
		gap: 0.6rem;
		min-width: 0;
		justify-content: center;
	}

	.card-title { display: none; }

	.card-description {
		font-size: 0.98rem;
		color: #cbd5e1;
		margin: 0;
		line-height: 1.5;
		display: -webkit-box;
		-webkit-line-clamp: 3;
		line-clamp: 3;
		-webkit-box-orient: vertical;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.card-tags {
		display: flex;
		flex-wrap: wrap;
		gap: 0.45rem;
	}

	.tag {
		background: rgba(51,65,85,0.6);
		color: #7dd3fc;
		padding: 0.25rem 0.65rem;
		border-radius: 999px;
		font-size: 0.78rem;
		font-weight: 600;
	}

	.card-meta {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		font-size: 0.85rem;
		color: #94a3b8;
	}

	.separator { color: rgba(255,255,255,0.06); }

	/* Modal Styles */
	.modal-overlay {
		position: fixed;
		inset: 0;
		background: rgba(2,6,23,0.8);
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 1000;
		padding: 20px;
		animation: fadeIn 160ms ease-out;
	}

	.modal {
		background-color: #0b0b0d; /* darker neutral background */
		border: 1px solid rgba(255,255,255,0.02);
		border-radius: 12px;
		width: 100%;
		max-width: 960px;
		max-height: 92vh;
		overflow-y: auto;
		box-shadow: 0 24px 80px rgba(2,6,23,0.75), 0 8px 24px rgba(0,0,0,0.45);
		position: relative;
		padding: 1.5rem 1.75rem;
		box-sizing: border-box;
	}

	.close-btn {
		position: absolute;
		top: 14px;
		right: 14px;
		background: transparent;
		color: #cbd5e1;
		border: none;
		width: 36px;
		height: 36px;
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 8px;
		cursor: pointer;
	}
	.close-btn:hover { background: rgba(255,255,255,0.02); transform: scale(1.05); }

	.modal-header { margin-bottom: 1.25rem; }

	.modal-image {
		width: 100%;
		max-height: 420px;
		object-fit: cover;
		border-radius: 10px;
		margin-bottom: 1rem;
	}

	.modal-title {
		font-size: 2rem;
		font-weight: 700;
		color: #e6e6e6;
		margin: 0 0 0.75rem 0;
		line-height: 1.15;
	}

	.modal-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 0.75rem; }

	.modal-meta { color: #9aa3ab; font-size: 0.95rem; margin-bottom: 1rem; }

	.modal-content { color: #e5e5e5; line-height: 1.8; font-size: 1rem; }
	.modal-content :global(p) { margin-bottom: 1rem; }
	.modal-content :global(h1), .modal-content :global(h2), .modal-content :global(h3) { color: #e6e6e6; margin-top: 1.5rem; margin-bottom: 0.75rem; }
	.modal .tag { background: rgba(255,255,255,0.02); color: #cbd5e1; }
	.modal-content :global(code) { background: #0f172a; padding: 0.2rem 0.4rem; border-radius: 4px; font-family: 'Ubuntu Mono', monospace; }
	.modal-content :global(pre) { background: #0f172a; padding: 1rem; border-radius: 8px; overflow-x: auto; margin: 1rem 0; }

	/* Scrollbar styling */
	.modal { scrollbar-width: thin; scrollbar-color: rgba(255,255,255,0.06) transparent; }
	.modal::-webkit-scrollbar { width: 8px; }
	.modal::-webkit-scrollbar-track { background: transparent; }
	.modal::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.04); border-radius: 6px; }

	/* Responsive Design */
	@media (max-width: 880px) {
		.blog-card { flex-direction: column; gap: 0.9rem; }
		.card-image { width: 100%; height: 200px; }
		.card-image img { transform-origin: center; }
		.card-content { padding: 0 0.25rem; }
		.card-description { -webkit-line-clamp: 4; }
	}

	@media (max-width: 420px) {
		.card-image { height: 160px; }
		.modal { padding: 1rem; }
		.modal-title { font-size: 1.4rem; }
		.modal-image { max-height: 200px; }
	}
</style>
