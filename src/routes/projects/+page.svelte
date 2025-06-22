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
			title: 'RC Car',
			description: 'Smart RC car with crash alerts 🚗💥',
			fullDescription: 'An Arduino-powered RC car that detects crashes using a gyroscope, UV sensor, and gas sensor. Sends SMS alerts with GPS coordinates using A7670C.',
			imageUrl: '/images/rccar.png',
			githubUrl: 'https://github.com/yourname/crash-car'
		},
		{
			title: 'Energy Monitoring System',
			description: 'Smart Energy Monitoring System ⚡',
			fullDescription: 'This project implements an IoT-based Smart Energy Monitoring System designed to monitor electrical parameters such as voltage, current, power, energy consumption, frequency, and power factor in real-time. The system leverages the ESP8266 Wi-Fi module and the PZEM-004T energy sensor to collect data from a connected load (e.g., a household bulb). The data is transmitted via WebSocket to a Flutter-based mobile/web application for real-time visualization and a Python script for data logging into a CSV file for historical analysis. This solution is cost-effective, scalable, and suitable for smart home or small-scale industrial energy monitoring.',
			imageUrl: '/images/energy.png',
			githubUrl: 'https://github.com/LostLuinor/IoT-Based-Smart-Energy-Monitoring-System'
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
