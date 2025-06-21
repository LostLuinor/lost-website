<script>
    import { page } from '$app/stores';
    let isOpen = false;
</script>

<nav>
    <div class="logo">LOST</div>

    <!-- Hamburger Menu Button (mobile) -->
    <button
        class="menu-btn"
        aria-label="Toggle navigation"
        aria-expanded={isOpen}
        on:click={() => isOpen = !isOpen}
    >
        <span class:isOpen={isOpen}></span>
        <span class:isOpen={isOpen}></span>
        <span class:isOpen={isOpen}></span>
    </button>

    <!-- Nav Links -->
    <div class="nav-links" class:open={isOpen}>
        <a href="/" class:active={$page.url.pathname === '/'} on:click={() => isOpen = false}>Home</a>
        <a href="/about" class:active={$page.url.pathname === '/about'} on:click={() => isOpen = false}>About</a>
        <a href="/contact" class:active={$page.url.pathname === '/contact'} on:click={() => isOpen = false}>Contact</a>
    </div>
</nav>

<style>
    :global(body) {
        margin: 0;
        background-color: #0d0d0d;
        color: #e5e5e5;
        font-family: 'Segoe UI', sans-serif;
    }

    nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 2rem;
        background-color: #0f172a;
        border-bottom: 1px solid #334155;
        position: relative;
    }

    .logo {
        font-size: 1.8rem;
        font-weight: bold;
        color: #0ea5e9;
    }

    .nav-links {
        display: flex;
        gap: 1.5rem;
    }

    .nav-links a {
        color: #e5e5e5;
        text-decoration: none;
        border-bottom: 2px solid transparent;
        transition: all 0.3s ease;
    }

    .nav-links a:hover {
        color: #94a3b8;
        border-color: #94a3b8;
    }

    .active {
        color: #0ea5e9;
        border-color: #0ea5e9;
        font-weight: bold;
    }

    /* Burger button */
    .menu-btn {
        display: none;
        flex-direction: column;
        gap: 5px;
        cursor: pointer;
        background: none;
        border: none;
    }

    .menu-btn span {
        display: block;
        width: 25px;
        height: 3px;
        background: #e5e5e5;
        border-radius: 2px;
        transition: 0.3s;
    }

    /* Mobile view styles */
    @media (max-width: 768px) {
        .menu-btn {
            display: flex;
        }

        .nav-links {
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            background-color: #1e293b;
            flex-direction: column;
            gap: 1rem;
            padding: 1rem;
            display: none;
        }

        .nav-links.open {
            display: flex;
        }
    }
</style>