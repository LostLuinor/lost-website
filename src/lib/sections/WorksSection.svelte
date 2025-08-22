<script>
    // Import ProjectCard if you want to reuse it
    // import ProjectCard from '$lib/ProjectCard.svelte';
    
    // Add your works/projects data here
    const works = [
        {
            title: "Project 1",
            description: "Brief description of your first project",
            imageUrl: "/images/project1.jpg",
            link: "https://github.com/yourusername/project1"
        },
        {
            title: "Project 2",
            description: "Brief description of your second project",
            imageUrl: "/images/project2.jpg",
            link: "https://github.com/yourusername/project2"
        },
        {
            title: "Project 3",
            description: "Brief description of your third project",
            imageUrl: "/images/project3.jpg",
            link: "https://github.com/yourusername/project3"
        }
    ];
</script>

<section class="works-section" id="works">
    <div class="container">
        <h2>Works</h2>
        <div class="works-grid">
            {#each works as work}
                <div class="work-card">
                    <img src={work.imageUrl} alt={work.title} />
                    <div class="work-content">
                        <h3>{work.title}</h3>
                        <p>{work.description}</p>
                        <a href={work.link} target="_blank" rel="noopener noreferrer" class="work-link">
                            View Project
                        </a>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<style>
    .works-section {
        padding: 4rem 0;
        background-color: #0f172a;
        color: #e5e5e5;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    h2 {
        font-size: 2.5rem;
        color: #0ea5e9;
        margin-bottom: 3rem;
        text-align: center;
    }

    .works-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
    }

    .work-card {
        background-color: #1e293b;
        border: 1px solid #334155;
        border-radius: 8px;
        overflow: hidden;
        transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .work-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 8px 32px rgba(14, 165, 233, 0.15);
    }

    .work-card img {
        width: 100%;
        height: 200px;
        object-fit: cover;
    }

    .work-content {
        padding: 1.5rem;
    }

    .work-content h3 {
        font-size: 1.3rem;
        color: #e5e5e5;
        margin-bottom: 1rem;
    }

    .work-content p {
        color: #cbd5e1;
        line-height: 1.6;
        margin-bottom: 1.5rem;
    }

    .work-link {
        display: inline-block;
        background-color: #0ea5e9;
        color: #fff;
        padding: 0.5rem 1rem;
        text-decoration: none;
        border-radius: 4px;
        transition: background-color 0.2s ease;
    }

    .work-link:hover {
        background-color: #0284c7;
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
