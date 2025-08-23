<script>
    const skillsData = [
        {
            category: "Languages",
            items: ["Java", "Python", "C", "Dart", 'Haskell']
        },
        {
            category: "Frameworks & Libraries",
            items: ["Flutter", "Svelte", "Node.js", "TensorFlow", "PyTorch"]
        },
        {
            category: "Soft Skills",
            items: ["Problem Solving", "Critical Thinking", "Self-learning"]
        }
    ];
</script>

<section class="skills-section" id="skills">
    <div class="container">
        <h2>(Skills...)</h2>
        <div class="skills-grid">
            {#each skillsData as skillGroup}
                <div class="skill-category">
                    <h3>{skillGroup.category}</h3>
                    <div class="skill-items">
                        {#each skillGroup.items as skill}
                            <div class="skill-tablet">
                                {skill}
                            </div>
                        {/each}
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<style>
    .skills-section {
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
        margin-bottom: 3rem;
        text-align: center;
    }

    .skills-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 3rem;
        max-width: 1000px;
        margin: 0 auto;
    }

    .skill-category {
        text-align: center;
    }

    .skill-category h3 {
        font-size: 1.5rem;
        color: #e5e5e5;
        margin-bottom: 1.5rem;
        font-weight: 600;
    }

    .skill-items {
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
        justify-content: center;
    }

    .skill-tablet {
        background: rgba(30, 41, 59, 0.8);
        backdrop-filter: blur(6px);
        border: 1px solid rgba(14, 165, 233, 0.3);
        border-radius: 25px;
        padding: 0.75rem 1.5rem;
        font-size: 0.9rem;
        color: #cbd5e1;
        transition: all 0.3s ease;
        cursor: default;
        white-space: nowrap;
    }

    .skill-tablet:hover {
        background: rgba(14, 165, 233, 0.2);
        border-color: rgba(14, 165, 233, 0.6);
        color: #ffffff;
        transform: translateY(-2px);
        box-shadow: 0 5px 15px rgba(14, 165, 233, 0.3);
    }

    @media (max-width: 768px) {
        .skills-section {
            padding: 3rem 0;
        }
        
        h2 {
            font-size: 2rem;
        }
        
        .skills-grid {
            grid-template-columns: 1fr;
            gap: 2rem;
        }
        
        .skill-category h3 {
            font-size: 1.3rem;
        }
        
        .skill-tablet {
            font-size: 0.85rem;
            padding: 0.6rem 1.2rem;
        }
    }
</style>
