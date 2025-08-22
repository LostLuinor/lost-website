<script>
    // Add timeline data here
    const timelineItems = [
        {
            year: "2024",
            title: "Current Role",
            description: "Add your current position or project here."
        },
        {
            year: "2023",
            title: "Previous Experience",
            description: "Add your previous experience or achievement here."
        },
        {
            year: "2022",
            title: "Education/Project",
            description: "Add educational background or major project here."
        }
    ];
</script>

<section class="timeline-section" id="timeline">
    <div class="container">
        <h2>Timeline</h2>
        <div class="timeline">
            {#each timelineItems as item}
                <div class="timeline-item">
                    <div class="timeline-year">{item.year}</div>
                    <div class="timeline-content">
                        <h3>{item.title}</h3>
                        <p>{item.description}</p>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<style>
    .timeline-section {
        padding: 4rem 0;
        background-color: #0d0d0d;
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

    .timeline {
        display: flex;
        flex-direction: column;
        gap: 2rem;
        max-width: 800px;
        margin: 0 auto;
    }

    .timeline-item {
        display: flex;
        gap: 2rem;
        align-items: flex-start;
    }

    .timeline-year {
        font-size: 1.5rem;
        font-weight: bold;
        color: #0ea5e9;
        min-width: 80px;
        flex-shrink: 0;
    }

    .timeline-content {
        flex: 1;
        border-left: 2px solid #334155;
        padding-left: 2rem;
        padding-bottom: 1rem;
    }

    .timeline-content h3 {
        font-size: 1.3rem;
        color: #e5e5e5;
        margin-bottom: 0.5rem;
    }

    .timeline-content p {
        color: #cbd5e1;
        line-height: 1.6;
    }

    @media (max-width: 768px) {
        .timeline-section {
            padding: 3rem 0;
        }
        
        h2 {
            font-size: 2rem;
        }
        
        .timeline-item {
            flex-direction: column;
            gap: 0.5rem;
        }
        
        .timeline-content {
            border-left: none;
            border-top: 2px solid #334155;
            padding-left: 0;
            padding-top: 1rem;
        }
        
        .timeline-year {
            min-width: auto;
        }
    }
</style>
