<script>
	import { page } from '$app/stores';
</script>

<nav>
	<div class="logo">LOST</div>
	<div class="nav-links">
		<a href="/" class:active={$page.url.pathname === '/'}>Home</a>
		<a href="/about" class:active={$page.url.pathname === '/about'}>About</a>
		<a href="/contact" class:active={$page.url.pathname === '/contact'}>Contact</a>
	</div>
</nav>

<style>
	:global(body) {
		margin: 0;
		background-color: #0d0d0d; /* rich black */
		color: #e5e5e5; /* light gray text */
		font-family: 'Segoe UI', sans-serif;
	}

	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem 2rem;
		background-color: #0f172a; /* slate-900 */
		border-bottom: 1px solid #e5e5e5; /* border color */
	}

	.logo {
		font-size: 1.8rem;
		font-weight: bold;
		color: #0ea5e9; /* accent blue */
	}

	.nav-links a {
		margin-left: 1.5rem;
		color: #e5e5e5;
		text-decoration: none;
		position: relative;
		padding: 0.25rem 0;
		border-bottom: 2px solid transparent;
		transition: all 0.3s ease;
	}

	.nav-links a:hover {
		color: #94a3b8; /* blue-gray hover */
		border-color: #94a3b8;
	}

	.active {
		color: #0ea5e9;
		border-color: #0ea5e9;
		font-weight: bold;
	}
</style>
