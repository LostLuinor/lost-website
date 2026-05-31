<script>
    import { browser } from '$app/environment';
    import { onMount } from 'svelte';

    export let title;
    export let description;
    export let fullDescription;
    export let imageUrl;
    export let githubUrl;

    let isOpen = false;
    let modalRef;

    function open() {
        isOpen = true;
    }
    function close() {
        isOpen = false;
    }
    function toggle() {
        isOpen = !isOpen;
    }

    function handleKeydown(event) {
        if (event.key === 'Enter' || event.key === ' ') {
            toggle();
        }
    }

    // Close modal with Escape key
    function handleModalKeydown(event) {
        if (event.key === 'Escape') {
            close();
        }
    }

    // Focus the modal when it opens for better keyboard accessibility
    $: if (isOpen && browser) {
        // prevent background scroll
        document.body.style.overflow = 'hidden';
        // focus modal after paint
        requestAnimationFrame(() => modalRef && modalRef.focus());
    } else if (browser) {
        document.body.style.overflow = '';
    }

    // make sure modal gets focus on mount if already open
    onMount(() => {
        if (isOpen && browser) modalRef && modalRef.focus();
    });
</script>

<!-- Compact Card -->
<div
    class="card"
    role="button"
    tabindex="0"
    aria-label="Open project details"
    on:click={open}
    on:keydown={handleKeydown}
>
    <div class="card-media">
        <img src={imageUrl} alt="Preview of {title} project" />
        <div class="card-overlay">
            <h3>{title}</h3>
            <p class="card-desc">{description}</p>
        </div>
    </div>
</div>

<!-- Modal -->
{#if isOpen}
    <div
        class="modal-overlay"
        role="dialog"
        aria-modal="true"
        aria-label="Project details modal"
        tabindex="-1"
        on:click={(event) => event.target === event.currentTarget && close()}
        on:keydown={handleModalKeydown}
    >
        <div
            class="modal"
            role="document"
            tabindex="-1"
            bind:this={modalRef}
        >
            <button class="modal-close" on:click={close} aria-label="Close modal">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
                    <path d="M18 6L6 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M6 6l12 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
            </button>

            <div class="modal-body">
                <img src={imageUrl} alt="Preview of {title} project" />
                <div class="modal-content">
                    <h2>
                        {title}
                    </h2>
                    <p>{fullDescription}</p>
                    {#if githubUrl}
                        <a class="github-button" href={githubUrl} target="_blank" rel="noopener noreferrer">View on GitHub</a>
                    {/if}
                </div>
            </div>
        </div>
    </div>
{/if}

<style>
    .card {
        background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
        color: #e5e5e5;
        border: 1px solid rgba(255,255,255,0.04);
        border-radius: 12px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.18s ease, box-shadow 0.18s ease;
        outline: none;
        width: 100%;
        max-width: 340px;
    }
    .card:focus,
    .card:hover {
        transform: translateY(-6px) scale(1.01);
        box-shadow: 0 10px 30px rgba(2,6,23,0.5), 0 4px 12px rgba(14,165,233,0.06);
    }

    .card-media {
        position: relative;
        height: 220px;
        overflow: hidden;
    }
    .card-media img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: block;
        transition: transform 0.6s cubic-bezier(.2,.8,.2,1);
    }
    .card:focus .card-media img,
    .card:hover .card-media img {
        transform: scale(1.05);
    }

    .card-overlay {
        position: absolute;
        inset: auto 0 0 0;
        padding: 12px 14px;
        background: rgba(0, 0, 0, 0.78);
        color: #e6eef8;
    }
    .card-overlay h3 {
        margin: 0;
        color: #7dd3fc;
        font-size: 1.05rem;
    }
    .card-desc {
        margin: 6px 0 0;
        font-size: 0.85rem;
        color: #cbd5e1;
        opacity: 0.95;
    }

    .modal-overlay {
        position: fixed;
        inset: 0;
        background: rgba(2,6,23,0.8);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;
        padding: 24px;
        animation: fadeIn 160ms ease-out;
    }
    @keyframes fadeIn { from { opacity: 0 } to { opacity: 1 } }

    .modal {
        background-color: #0b0b0d;
        border: 1px solid rgba(255,255,255,0.02);
        padding: 1.5rem 1.75rem;
        border-radius: 12px;
        width: 100%;
        max-width: 960px;
        max-height: 92vh;
        overflow-y: auto;
        box-shadow: 0 24px 80px rgba(2,6,23,0.75), 0 8px 24px rgba(0,0,0,0.45);
        position: relative;
        box-sizing: border-box;
        display: flex;
        flex-direction: column;
    }

    .modal-close {
        position: absolute;
        right: 14px;
        top: 14px;
        background: transparent;
        border: none;
        color: #cbd5e1;
        cursor: pointer;
        padding: 0;
        width: 36px;
        height: 36px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 8px;
    }
    .modal-close:hover { background: rgba(255,255,255,0.02); transform: scale(1.05); }

    .modal-body {
        display: flex;
        gap: 1.25rem;
        align-items: flex-start;
    }
    .modal-body img {
        width: 42%;
        max-width: 380px;
        border-radius: 8px;
        object-fit: cover;
    }
    .modal-content {
        width: 58%;
    }
    .modal-content h2 { margin: 0 0 0.5rem; color: #e6e6e6; }
    .modal-content p { color: #e5e5e5; line-height: 1.6; }

    .github-button {
        display: inline-block;
        margin-top: 1rem;
        background: linear-gradient(90deg,#0ea5e9,#7dd3fc);
        color: #021025;
        padding: 0.5rem 0.9rem;
        border-radius: 8px;
        text-decoration: none;
        font-weight: 600;
    }

    /* Responsive tweaks */
    @media (max-width: 820px) {
        .modal-body { flex-direction: column; }
        .modal-body img, .modal-content { width: 100%; }
        .modal-close { right: 18px; top: 18px; }
    }

    @media (max-width: 420px) {
        .card { max-width: 100%; border-radius: 10px; }
        .card-media { height: 180px; }
        .modal { padding: 1rem; }
        .modal-close { right: 10px; top: 10px; }
    }

    /* For Firefox */
    .modal { scrollbar-width: thin; scrollbar-color: rgba(255,255,255,0.06) transparent; }
</style>