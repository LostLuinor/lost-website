<script>
    // Import ProjectCard component
    import ProjectCard from '$lib/components/project/ProjectCard.svelte';
    
    // Add your works/projects data here
    const works = [
        {
            title: "Quantum Maze Solver",
            description: "AI-powered maze solving algorithm using quantum computing principles",
            fullDescription: "A sophisticated maze solver that combines quantum computing algorithms with classical AI pathfinding. Built using Python and Qiskit, this project demonstrates quantum superposition for exploring multiple paths simultaneously, achieving 40% faster solving times compared to traditional algorithms.",
            imageUrl: "/images/maze.png",
            githubUrl: "https://github.com/LostLuinor/Quantum-Maze-Solver"
        },
        {
            title: "Emotion Detection System",
            description: "Real-time facial emotion recognition using deep learning",
            fullDescription: "Advanced computer vision system that detects and classifies human emotions in real-time using TensorFlow and OpenCV. Trained on over 35,000 facial images with 94% accuracy across 7 emotion categories. Features include live webcam processing and batch image analysis.",
            imageUrl: "/images/emotion.jpg",
            githubUrl: "https://github.com/LostLuinor/emotion-detection"
        },
        {
            title: "Smart RC Car",
            description: "Autonomous remote-controlled car with obstacle avoidance",
            fullDescription: "Arduino-based autonomous vehicle equipped with ultrasonic sensors, camera module, and WiFi connectivity. Features include manual remote control, autonomous navigation, object detection, and real-time video streaming. Built using C++ and integrated with mobile app control.",
            imageUrl: "/images/rccar.png",
            githubUrl: "https://github.com/LostLuinor/smart-rc-car"
        },
        {
            title: "Energy Monitoring Dashboard",
            description: "IoT-based home energy consumption tracking system",
            fullDescription: "Full-stack web application for monitoring home energy usage in real-time. Built with React frontend, Node.js backend, and MongoDB database. Features include historical data visualization, cost analysis, and automated alerts for unusual consumption patterns.",
            imageUrl: "/images/energy.png",
            githubUrl: "https://github.com/LostLuinor/IoT-Based-Smart-Energy-Monitoring-System"
        }
    ];
</script>

<section class="works-section" id="works">
    <div class="container">
        <h2>(Works...)</h2>
        <div class="works-grid">
            {#each works as work}
                <ProjectCard 
                    title={work.title}
                    description={work.description}
                    fullDescription={work.fullDescription}
                    imageUrl={work.imageUrl}
                    githubUrl={work.githubUrl}
                />
            {/each}
        </div>
    </div>
</section>

<style>
    .works-section {
        padding: 1 rem 0;
            color: #e5e5e5;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    h2 {
        font-size: 2.5rem;
        margin-bottom: 3rem;
        text-align: right;
    }

    .works-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
    }

    @media (max-width: 768px) {
        .works-section {
            padding: 3rem 0;
        }
        
        h2 {
            font-size: 2rem;
        }
        
        .works-grid {
            grid-template-columns: 1fr;
        }
    }
</style>
