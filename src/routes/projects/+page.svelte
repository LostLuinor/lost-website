<script>
	import ProjectCard from '$lib/ProjectCard.svelte';

	const projects = [
		{
			title: 'Quantum Maze Solver',
			description: 'AI-powered maze navigation 🧠',
			fullDescription: 'This project uses a quantum-inspired algorithm and Mesa-Pygame interface to solve mazes efficiently with wall-hugger fallback logic.',
			imageUrl: '/images/maze.png',
			githubUrl: 'https://github.com/yourname/quantum-maze'
		},
		{
			title: 'Emotion Detector',
			description: 'Real-time facial & voice emotion classifier 🎭',
			fullDescription: 'This uses a multimodal deep learning model to analyze facial expressions and voice tone, combined via Flask backend and Flutter frontend.',
			imageUrl: '/images/emotion.jpg',
			githubUrl: 'https://github.com/yourname/emotion-detector'
		},
		{
			title: 'Crash Detection Car',
			description: 'Smart RC car with crash alerts 🚗💥',
			fullDescription: 'An Arduino-powered RC car that detects crashes using a gyroscope, UV sensor, and gas sensor. Sends SMS alerts with GPS coordinates using A7670C.',
			imageUrl: '/images/rccar.png',
			githubUrl: 'https://github.com/yourname/crash-car'
		},
		{
			title: 'Crash Detection Car',
			description: 'Smart RC car with crash alerts 🚗💥',
			fullDescription: 'An Arduino-powered RC car that detects crashes using a gyroscope, UV sensor, and gas sensor. Sends SMS alerts with GPS coordinates using A7670C.',
			imageUrl: '/images/rccar.png',
			githubUrl: 'https://github.com/yourname/crash-car'
		}
	];
</script>

<h1>Projects</h1>
<div class="project-grid">
	{#each projects as project}
		<ProjectCard {...project} />
	{/each}
</div>

<style>
	h1 {
		/* color: #0ea5e9; */
		margin-bottom: 2rem;
		/* text-align: center; */
	}

	.project-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 1.5rem;
	}
</style>
