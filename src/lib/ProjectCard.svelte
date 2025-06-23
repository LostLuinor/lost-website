<script>
    export let title;
    export let description;
    export let fullDescription;
    export let imageUrl;
    export let githubUrl;

    let isOpen = false;

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
            isOpen = false;
        }
    }

    // Prevent background scroll when modal is open
    $: {
        if (isOpen) {
            document.body.style.overflow = 'hidden';
        } else {
            document.body.style.overflow = '';
        }
    }
</script>

<!-- Compact Card -->
<div
    class="card"
    role="button"
    tabindex="0"
    aria-label="Open project details"
    on:click={toggle}
    on:keydown={handleKeydown}
>
    <img src={imageUrl} alt="Preview of {title} project" />
    <h3>{title}</h3>
    <p>{description}</p>
</div>

<!-- Modal -->
{#if isOpen}
    <div
        class="modal-overlay"
        role="dialog"
        tabindex="0"
        aria-modal="true"
        aria-label="Project details modal"
        on:click={toggle}
        on:keydown={handleModalKeydown}
    >
        <div
            class="modal"
            role="document"
            tabindex="0"
            on:click|stopPropagation
        >
            <img src={imageUrl} alt="Preview of {title} project" />
            <h2>
                <a href={githubUrl} target="_blank" rel="noopener noreferrer">{title}</a>
            </h2>
            <p>{fullDescription}</p>
            <button class="close" on:click={toggle} aria-label="Close modal">Close</button>
        </div>
    </div>
{/if}

<style>
    .card {
        background-color: #1e293b;
        color: #e5e5e5;
        border: 1px solid #334155;
        border-radius: 8px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.2s ease, box-shadow 0.2s;
        outline: none;
    }
    .card:hover,
    .card:focus {
        transform: scale(1.03);
        box-shadow: 0 4px 24px 0 rgba(14, 165, 233, 0.15);
    }
    .card img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    height: 200px;
    max-width: 300px;
    object-fit: cover;
}
    .card h3 {
        margin: 0.75rem;
        color: #0ea5e9;
    }
    .card p {
        margin: 0 0.75rem 1rem;
        font-size: 0.9rem;
        color: #cbd5e1;
    }

    .modal-overlay {
        position: fixed;
        inset: 0;
        background: rgba(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;
    }
    .modal {
        background-color: #0f172a;
        border: 1px solid #334155;
        padding: 2rem;
        border-radius: 12px;
        width: 75%;
        max-width: 70%;
        max-height: 90vh;
        overflow-y: auto;
        box-shadow: 0 8px 32px 0 rgba(14, 165, 233, 0.15);
        box-sizing: border-box;
    }
    .modal img {
        display: block;
        margin-left: auto;
        margin-right: auto;
        max-width: 500px;
        max-height: 50vh;
        object-fit: cover;
    }

    /* For small screens */
    @media (max-width: 600px) {
        .modal img {
            width: 100%;
            max-width: 90vw;
            max-height: 30vh;
        }
    }
    .modal h2 a {
        color: #0ea5e9;
        text-decoration: none;
    }
    .modal h2 a:hover {
        text-decoration: underline;
    }
    .modal p {
        color: #e5e5e5;
        line-height: 1.6;
    }
    .close {
        margin-top: 1.5rem;
        background: #334155;
        color: white;
        border: none;
        padding: 0.5rem 1rem;
        cursor: pointer;
        border-radius: 6px;
        transition: background 0.2s;
    }
    .close:hover {
        background: #475569;
    }
    /* For Firefox */
    .modal {
        scrollbar-width: thin;
        scrollbar-color: #334155 #1e293b;
    }
</style>