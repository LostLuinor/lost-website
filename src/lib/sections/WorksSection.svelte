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
        <div class="section-end">
            <!-- <a href="/projects" class="projects-link">Even More...</a> -->
        </div>
</section>

<style>
    .works-section {
            padding: 1rem 0 2rem;
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

    .section-end {
        max-width: 1200px;
        margin: 2.5rem auto 0;
        padding: 0 2rem;
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        gap: 0.75rem;
        text-align: right;
    }

    .section-end p {
        margin: 0;
        color: #94a3b8;
        font-size: 0.95rem;
    }

    .projects-link {
        display: inline-flex;
        align-items: center;
        gap: 0.6rem;
        padding: 0.9rem 1.25rem;
        border-radius: 999px;
        border: 1px solid rgba(14, 165, 233, 0.35);
        background: linear-gradient(135deg, rgba(14, 165, 233, 0.18), rgba(30, 41, 59, 0.9));
        color: #f8fafc;
        text-decoration: none;
        font-weight: 700;
        letter-spacing: 0.01em;
        box-shadow: 0 10px 30px rgba(2, 6, 23, 0.28);
        transition: transform 0.2s ease, border-color 0.2s ease, box-shadow 0.2s ease,
            background 0.2s ease;
    }

    .projects-link::after {
        content: '→';
        font-size: 1rem;
        transition: transform 0.2s ease;
    }

    .projects-link:hover {
        transform: translateY(-2px);
        border-color: rgba(14, 165, 233, 0.7);
        box-shadow: 0 14px 34px rgba(2, 6, 23, 0.36);
        background: linear-gradient(135deg, rgba(14, 165, 233, 0.26), rgba(30, 41, 59, 0.96));
    }

    .projects-link:hover::after {
        transform: translateX(3px);
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

        .section-end {
            padding: 0 2rem;
            align-items: flex-start;
            text-align: left;
        }
    }
</style>
