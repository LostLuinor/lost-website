<script>
    import { onMount } from 'svelte';
    
    // Add timeline data here
    const timelineItems = [
        {
            year: "",
            title: "Full Stack Developer Intern @ ArcVision",
            description: "Working on an energy consumption monitoring platform, building both front-end and back-end systems. Learning the ropes of real-world development while contributing to impactful projects."
        },
        {
            year: "",
            title: "Crypto Domain Lead @ bi0sblr",
            description: "Capture The Flag (CTF) enthusiast and active player with team bi0sblr. Leading the crypto domain, solving puzzles, and breaking challenges that test cryptographic thinking."
        },
        {
            year: "",
            title: "Senior Executive @ CodeChef",
            description: "Guiding peers in competitive programming, hosting sessions, and fostering a coding culture. Sharing problem-solving approaches while learning new tricks along the way."
        },
        {
            year: "",
            title: "CS + AI Undergraduate",
            description: "Currently in 5th semester with a CGPA of 8.3. Exploring AI, security, and systems with a hands-on approach to projects and research."
        },
        {
            year: "",
            title: "Clash Royale Grinder",
            description: "Because life isn't all code—hit 10k trophies in Clash Royale ⚔️. Strategy, patience, and late-night grind sessions included. (Need to touch grass ig T-T)"
        }
    ];


    let timelineElement;
    let progressLine;
    let animatedItems = new Set();

    onMount(() => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    const index = parseInt(entry.target.dataset.index);
                    animatedItems.add(index);
                    animatedItems = animatedItems; // Trigger reactivity
                }
            });
        }, {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        });

        // Observe timeline items
        const items = timelineElement.querySelectorAll('.timeline-item');
        items.forEach((item) => observer.observe(item));

        // Fallback: Show items after a short delay if intersection observer fails
        setTimeout(() => {
            for (let i = 0; i < timelineItems.length; i++) {
                animatedItems.add(i);
            }
            animatedItems = animatedItems; // Trigger reactivity
        }, 1000);

        // Scroll progress animation
        const handleScroll = () => {
            if (!timelineElement || !progressLine) return;

            const rect = timelineElement.getBoundingClientRect();
            const windowHeight = window.innerHeight;
            const timelineHeight = timelineElement.offsetHeight;
            
            // Calculate scroll progress more smoothly
            const elementTop = rect.top;
            const elementBottom = rect.bottom;
            
            // Start animation when timeline enters viewport
            const startPoint = windowHeight * 0.8; // Start earlier
            // End animation when timeline bottom reaches middle of screen
            const endPoint = windowHeight * 0.5;
            
            let progress = 0;
            
            if (elementBottom > endPoint && elementTop < startPoint) {
                // Calculate how much of the timeline has been scrolled through
                if (elementTop <= endPoint) {
                    // Timeline is fully in view or past it
                    progress = Math.min(1, (startPoint - elementTop) / (startPoint + timelineHeight - endPoint));
                } else {
                    // Timeline is entering view
                    progress = (startPoint - elementTop) / (startPoint - endPoint);
                }
                progress = Math.max(0, Math.min(1, progress));
            } else if (elementTop <= endPoint) {
                // Timeline has scrolled past
                progress = 1;
            }
            
            // Apply smooth progress with consistent glow
            progressLine.style.height = `${progress * 100}%`;
            
            // Ensure glow effect remains visible
            if (progress > 0) {
                progressLine.style.opacity = '1';
            }
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
        <h2>(More...)</h2>
        <div class="timeline" bind:this={timelineElement}>
            <div class="timeline-line">
                <div class="timeline-progress" bind:this={progressLine}></div>
            </div>
            {#each timelineItems as item, index}
                <div class="timeline-item {index % 2 === 0 ? 'right' : 'left'}">
                    <div class="timeline-dot"></div>
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
        color: #e5e5e5;
    }


    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    h2 {
        font-size: 2.5rem;
        color: #ffffff;
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
        width: 2px;
        background: rgba(14, 165, 233, 0.4);
        box-shadow: 0 0 15px rgba(14, 165, 233, 0.6);
        transform: translateX(-50%);
    }

.timeline-progress {
    background: #0ea5e9;
    box-shadow: 0 0 15px rgba(14, 165, 233, 0.9);
}


    .timeline-progress {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 0%;
        background: #0ea5e9;
        transition: height 0.3s ease-out;
        box-shadow: 0 0 15px rgba(14, 165, 233, 0.9);
    }

    .timeline-item {
        position: relative;
        display: flex;
        margin-bottom: 4rem;
        opacity: 1;
        transition: all 0.8s ease-out;
        align-items: center;
    }

    .timeline-item:not(.animate-in) {
        opacity: 0.7;
    }

    .timeline-item.left {
        justify-content: flex-end;
        transform: translateX(-50px);
    }

    .timeline-item.right {
        justify-content: flex-start;
        transform: translateX(50px);
    }

    .timeline-item.animate-in {
        opacity: 1;
        transform: translateX(0);
    }

    .timeline-dot {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 12px;
        height: 12px;
        background: #0ea5e9;
        border-radius: 50%;
        box-shadow: 0 0 20px rgba(14, 165, 233, 0.8);
        transform: translate(-50%, -50%);
        z-index: 2;
    }

    .timeline-item.animate-in .timeline-dot {
        background-color: #06b6d4;
        box-shadow: 0 0 0 4px #0ea5e9, 0 0 25px rgba(14, 165, 233, 0.8);
        transform: translate(-50%, -50%) scale(1.3);
    }

    .timeline-content {
        background: rgba(30, 41, 59, 0.6); /* transparent look */
        backdrop-filter: blur(6px); /* frosted glass effect */
        border: 1px solid rgba(14, 165, 233, 0.2);
        border-radius: 8px;
        padding: 1.2rem;
        width: 35%;
        color: #e5e5e5;
        transition: all 0.3s ease;
        position: relative;
    }

    .timeline-content:hover {
        border-color: rgba(14, 165, 233, 0.6);
        box-shadow: 0 0 25px rgba(14, 165, 233, 0.4);
    }


    
    .timeline-item.left .timeline-content {
        text-align: right;
    }

    .timeline-item.right .timeline-content {
        text-align: left;
    }

    .timeline-item.animate-in .timeline-content {
        transform: translateY(-8px);
        box-shadow: 0 15px 40px rgba(14, 165, 233, 0.15);
        border-color: rgba(14, 165, 233, 0.3);
    }

    .timeline-year {
        position: absolute;
        top: -25px;
        left: 50%;
        transform: translateX(-50%);
        font-size: 0.9rem;
        color: #0ea5e9;
        font-weight: bold;
        letter-spacing: 1px;
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
