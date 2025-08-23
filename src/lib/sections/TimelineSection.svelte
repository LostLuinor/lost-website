<script>
    import { onMount } from 'svelte';
    
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

    let timelineElement;
    let progressLine;

    onMount(() => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('animate-in');
                }
            });
        }, {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        });

        // Observe timeline items
        const items = timelineElement.querySelectorAll('.timeline-item');
        items.forEach((item) => observer.observe(item));

        // Scroll progress animation
        const handleScroll = () => {
            if (!timelineElement || !progressLine) return;

            const rect = timelineElement.getBoundingClientRect();
            const windowHeight = window.innerHeight;
            const timelineHeight = timelineElement.offsetHeight;
            
            // Calculate how much of the timeline is visible
            const startOffset = rect.top;
            const endOffset = rect.bottom;
            
            let progress = 0;
            
            if (startOffset <= windowHeight && endOffset >= 0) {
                if (startOffset <= 0) {
                    progress = Math.min(1, (windowHeight - Math.max(0, endOffset - windowHeight)) / Math.min(windowHeight, timelineHeight));
                } else {
                    progress = (windowHeight - startOffset) / (windowHeight + timelineHeight);
                }
                progress = Math.max(0, Math.min(1, progress));
            }
            
            progressLine.style.height = `${progress * 100}%`;
        };

        window.addEventListener('scroll', handleScroll);
        handleScroll(); // Initial call

        return () => {
            observer.disconnect();
            window.removeEventListener('scroll', handleScroll);
        };
    });
</script>

<section class="timeline-section" id="timeline">
    <div class="container">
        <h2>Timeline</h2>
        <div class="timeline" bind:this={timelineElement}>
            <div class="timeline-line">
                <div class="timeline-progress" bind:this={progressLine}></div>
            </div>
            {#each timelineItems as item, index}
                <div class="timeline-item {index % 2 === 0 ? 'left' : 'right'}" style="animation-delay: {index * 0.2}s">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-year">{item.year}</div>
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
        position: relative;
        max-width: 1000px;
        margin: 0 auto;
        padding: 2rem 0;
    }

    .timeline-line {
        position: absolute;
        left: 50%;
        top: 0;
        bottom: 0;
        width: 4px;
        background: repeating-linear-gradient(
            to bottom,
            #334155 0px,
            #334155 10px,
            transparent 10px,
            transparent 20px
        );
        transform: translateX(-50%);
    }

    .timeline-progress {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 0%;
        background: repeating-linear-gradient(
            to bottom,
            #0ea5e9 0px,
            #0ea5e9 10px,
            transparent 10px,
            transparent 20px
        );
        transition: height 0.3s ease-out;
        box-shadow: 0 0 15px rgba(14, 165, 233, 0.6);
    }

    .timeline-item {
        position: relative;
        display: flex;
        margin-bottom: 4rem;
        opacity: 0;
        transition: all 0.8s ease-out;
        align-items: center;
    }

    .timeline-item.left {
        justify-content: flex-end;
        transform: translateX(-100px);
    }

    .timeline-item.right {
        justify-content: flex-start;
        transform: translateX(100px);
    }

    .timeline-item.animate-in {
        opacity: 1;
        transform: translateX(0);
    }

    .timeline-dot {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 16px;
        height: 16px;
        background-color: #0ea5e9;
        border-radius: 50%;
        border: 4px solid #0d0d0d;
        box-shadow: 0 0 0 4px #334155;
        transition: all 0.4s ease;
        z-index: 2;
        transform: translate(-50%, -50%);
    }

    .timeline-item.animate-in .timeline-dot {
        background-color: #06b6d4;
        box-shadow: 0 0 0 4px #0ea5e9, 0 0 25px rgba(14, 165, 233, 0.8);
        transform: translate(-50%, -50%) scale(1.3);
    }

    .timeline-content {
        width: 45%;
        background-color: #1e293b;
        padding: 2rem;
        border-radius: 12px;
        border: 1px solid #334155;
        position: relative;
        transition: all 0.4s ease;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }

    .timeline-item.left .timeline-content {
        margin-right: 2rem;
        text-align: right;
    }

    .timeline-item.right .timeline-content {
        margin-left: 2rem;
        text-align: left;
    }

    .timeline-item.left .timeline-content::after {
        content: '';
        position: absolute;
        right: -15px;
        top: 50%;
        width: 0;
        height: 0;
        border-top: 10px solid transparent;
        border-bottom: 10px solid transparent;
        border-left: 15px solid #1e293b;
        transform: translateY(-50%);
    }

    .timeline-item.right .timeline-content::after {
        content: '';
        position: absolute;
        left: -15px;
        top: 50%;
        width: 0;
        height: 0;
        border-top: 10px solid transparent;
        border-bottom: 10px solid transparent;
        border-right: 15px solid #1e293b;
        transform: translateY(-50%);
    }

    .timeline-item.animate-in .timeline-content {
        transform: translateY(-8px);
        box-shadow: 0 15px 40px rgba(14, 165, 233, 0.15);
        border-color: rgba(14, 165, 233, 0.3);
    }

    .timeline-year {
        font-size: 1.1rem;
        font-weight: bold;
        color: #0ea5e9;
        margin-bottom: 0.5rem;
        opacity: 0.9;
    }

    .timeline-content h3 {
        font-size: 1.4rem;
        color: #e5e5e5;
        margin-bottom: 1rem;
        transition: color 0.3s ease;
    }

    .timeline-item.animate-in .timeline-content h3 {
        color: #06b6d4;
    }

    .timeline-content p {
        color: #cbd5e1;
        line-height: 1.7;
        margin: 0;
        font-size: 1rem;
    }

    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(30px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @media (max-width: 768px) {
        .timeline-section {
            padding: 3rem 0;
        }
        
        h2 {
            font-size: 2rem;
        }
        
        .timeline {
            max-width: 100%;
            padding: 1rem;
        }
        
        .timeline-line {
            left: 30px;
            transform: none;
        }
        
        .timeline-item {
            flex-direction: row;
            justify-content: flex-start !important;
            margin-bottom: 3rem;
            align-items: flex-start;
        }
        
        .timeline-item.left,
        .timeline-item.right {
            transform: translateY(50px);
        }
        
        .timeline-item.animate-in {
            transform: translateY(0);
        }
        
        .timeline-dot {
            left: 30px;
            top: 20px;
            transform: translateX(-50%);
            position: absolute;
        }
        
        .timeline-content {
            width: calc(100% - 80px);
            margin-left: 60px !important;
            margin-right: 0 !important;
            text-align: left !important;
        }
        
        .timeline-content::after {
            display: none;
        }
        
        .timeline-year {
            font-size: 1rem;
        }
        
        .timeline-content h3 {
            font-size: 1.2rem;
        }
        
        .timeline-content p {
            font-size: 0.9rem;
        }
    }
</style>
