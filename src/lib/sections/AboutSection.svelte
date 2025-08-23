<script>
    // Add any props or logic here
</script>

<section class="about-section" id="about">
    <div class="container">
        <div class="about-layout">
            <div class="about-title">
                <h2>(About...)</h2>
            </div>
            <div class="about-content">
                <p> Hey, I'm Lishanthan <br>
                    Undergrad with a habit of breaking puzzles—whether in CTFs, code, or games. I build things, break things, and learn by 
                    exploring the gaps in between, sometimes just for fun.</p>
            </div>
        </div>
    </div>
</section>

<style>
    .about-section {
        padding: 4rem 0;
        color: #e5e5e5;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    .about-layout {
        display: flex;
        gap: 3rem;
        align-items: stretch;
    }

    .about-title {
        flex: 0 0 200px;
        display: flex;
        align-items: center;
    }

    .about-title h2 {
        font-size: 2rem;
        color: #e5e5e5;
        margin: 0;
        letter-spacing: 0.2em;
    }

    .about-content {
        flex: 1;
        background-color: #0f172a;
        padding: 2rem;
        border-radius: 8px;
        display: flex;
        align-items: center;
    }

    .about-content p {
        font-size: 1.1rem;
        line-height: 1.6;
        color: #ffffff;
        margin: 0;
    }

    @media (max-width: 768px) {
        .about-section {
            padding: 3rem 0;
        }
        
        .about-layout {
            flex-direction: column;
            gap: 1.5rem;
        }

        .about-title {
            flex: none;
        }

        .about-title h2 {
            font-size: 1.8rem;
            writing-mode: horizontal-tb;
            text-orientation: initial;
            text-align: center;
        }
        
        .about-content p {
            font-size: 1rem;
        }
    }
</style>
