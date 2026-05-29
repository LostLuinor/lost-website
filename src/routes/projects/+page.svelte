<script>
	import ProjectCard from '$lib/components/project/ProjectCard.svelte';

	const projects = [
		{
			title: 'Quantum Maze Solver',
			description: 'AI-powered maze solving algorithm using quantum computing principles',
			fullDescription:
				'A sophisticated maze solver that combines quantum computing algorithms with classical AI pathfinding. Built using Python and Qiskit, this project demonstrates quantum superposition for exploring multiple paths simultaneously, achieving faster solving times compared to traditional algorithms.',
			imageUrl: '/images/maze.png',
			githubUrl: 'https://github.com/LostLuinor/Quantum-Maze-Solver'
		},
		{
			title: 'Emotion Detection System',
			description: 'Real-time facial emotion recognition using deep learning',
			fullDescription:
				'Advanced computer vision system that detects and classifies human emotions in real-time using TensorFlow and OpenCV. Trained on tens of thousands of facial images with strong accuracy across multiple emotion categories.',
			imageUrl: '/images/emotion.jpg',
			githubUrl: 'https://github.com/LostLuinor/emotion-detection'
		},
		{
			title: 'Smart RC Car',
			description: 'Autonomous remote-controlled car with obstacle avoidance',
			fullDescription:
				'Arduino-based autonomous vehicle equipped with ultrasonic sensors, camera module, and WiFi connectivity. Features include manual remote control, autonomous navigation, object detection, and real-time video streaming.',
			imageUrl: '/images/rccar.png',
			githubUrl: 'https://github.com/LostLuinor/smart-rc-car'
		},
		{
			title: 'Energy Monitoring Dashboard',
			description: 'IoT-based home energy consumption tracking system',
			fullDescription:
				'Full-stack web application for monitoring home energy usage in real-time. Built with a modern frontend, Node.js backend, and database storage. Includes historical data visualization, cost analysis, and alerting for unusual usage patterns.',
			imageUrl: '/images/energy.png',
			githubUrl: 'https://github.com/LostLuinor/IoT-Based-Smart-Energy-Monitoring-System'
		}
	];

</script>

<svelte:head>
	<title>Projects | LOST</title>
	<meta
		name="description"
		content="Selected projects and experiments built by LOST, presented as interactive project cards."
	/>
</svelte:head>

<section class="projects-page">
	<div class="projects-grid-wrap">
		<div class="section-heading">
			<h1>Projects and Experiments</h1>
		</div>

		<div class="projects-grid">
			{#each projects as project}
				<ProjectCard
					title={project.title}
					description={project.description}
					fullDescription={project.fullDescription}
					imageUrl={project.imageUrl}
					githubUrl={project.githubUrl}
				/>
			{/each}
		</div>
	</div>

	<div class="projects-footer">
		<p>
			Each card opens into a detailed view with the longer description and source repository.
			The page is designed to stay lightweight while still feeling intentional and polished.
		</p>
	</div>
</section>

<style>
	h1 {
        /* text-align: center; */
        /* color: #0ea5e9; */
        margin-bottom: 1.5rem;
    }
	.projects-page {
		max-width: 1200px;
		margin: 0 auto;
		padding: 3rem 1.5rem 4rem;
		color: #e5e5e5;
	}

	.projects-hero {
		display: grid;
		grid-template-columns: minmax(0, 1.5fr) minmax(280px, 0.9fr);
		gap: 2rem;
		align-items: stretch;
		padding: 2rem;
		border: 1px solid rgba(51, 65, 85, 0.85);
		border-radius: 24px;
		background:
			radial-gradient(circle at top left, rgba(14, 165, 233, 0.16), transparent 34%),
			radial-gradient(circle at bottom right, rgba(15, 23, 42, 0.9), rgba(15, 23, 42, 0.95));
		box-shadow: 0 24px 80px rgba(2, 6, 23, 0.45);
	}

	.hero-copy h1 {
		margin: 0.25rem 0 1rem;
		font-size: clamp(3rem, 7vw, 5.5rem);
		line-height: 0.95;
		letter-spacing: -0.05em;
	}

	.eyebrow,
	.section-heading p {
		margin: 0;
		color: #38bdf8;
		text-transform: uppercase;
		letter-spacing: 0.16em;
		font-size: 0.8rem;
		font-weight: 700;
	}

	.lede {
		max-width: 60ch;
		margin: 0;
		color: #cbd5e1;
		font-size: 1.05rem;
		line-height: 1.7;
	}

	.hero-stats {
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
		gap: 1rem;
		margin-top: 1.75rem;
	}

	.hero-stats div,
	.hero-panel {
		border: 1px solid rgba(51, 65, 85, 0.85);
		background: rgba(15, 23, 42, 0.72);
		border-radius: 18px;
	}

	.hero-stats div {
		padding: 1rem;
	}

	.stat-value {
		display: block;
		color: #f8fafc;
		font-size: 1.15rem;
		font-weight: 700;
		margin-bottom: 0.25rem;
	}

	.stat-label {
		color: #94a3b8;
		font-size: 0.92rem;
		line-height: 1.4;
	}

	.hero-panel {
		padding: 1.5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.hero-panel h2,
	.section-heading h2 {
		margin: 0 0 1rem;
		font-size: 1.5rem;
	}

	.hero-panel ul {
		margin: 0;
		padding-left: 1.1rem;
		color: #cbd5e1;
		display: grid;
		gap: 0.75rem;
	}

	.section-divider {
		width: 100%;
		height: 2px;
		background: linear-gradient(to right, transparent, #475569, transparent);
		margin: 2.25rem 0;
		opacity: 0.65;
	}

	.projects-grid-wrap {
		display: grid;
		gap: 1.5rem;
	}

	.section-heading {
		display: flex;
		flex-direction: column;
		gap: 0.35rem;
	}

	.section-heading h2 {
		margin: 0;
		font-size: clamp(1.8rem, 4vw, 2.6rem);
	}

	.projects-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 1.5rem;
	}

	.projects-footer {
		margin-top: 2.5rem;
		padding: 1.25rem 1.5rem;
		border: 1px solid rgba(51, 65, 85, 0.75);
		border-radius: 18px;
		background: rgba(15, 23, 42, 0.5);
		color: #94a3b8;
		line-height: 1.7;
	}

	@media (max-width: 900px) {
		.projects-hero {
			grid-template-columns: 1fr;
		}

		.hero-stats {
			grid-template-columns: 1fr;
		}
	}

	@media (max-width: 640px) {
		.projects-page {
			padding: 2rem 1rem 3rem;
		}

		.projects-hero {
			padding: 1.25rem;
		}

		.hero-copy h1 {
			font-size: clamp(2.5rem, 14vw, 4rem);
		}

		.projects-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
