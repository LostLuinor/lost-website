<script>
    // Add any props or logic here
</script>

<section class="main-section">
    <div class="container">
        <div class="hero-title">
            <h1>Welcome to</h1>
            <img src="/images/LostLogo.png" alt="LOST Logo" />
        </div>
        <p>Coo coo coolie POWER HOSUE-EH</p>
    </div>
</section>

<style>
    .main-section {
        min-height: 80vh;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #0d0d0d;
        color: #e5e5e5;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
        text-align: center;
    }

    .hero-title {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1rem;
        margin-bottom: 1rem;
    }

    h1 {
        font-size: 3rem;
        color: #0ea5e9;
        margin: 0;
    }

    .hero-title img {
        height: 3rem;
        width: auto;
        object-fit: contain;
    }

    p {
        font-size: 1.2rem;
        color: #cbd5e1;
    }

    @media (max-width: 768px) {
        .hero-title {
            flex-direction: column;
            gap: 0.5rem;
        }
        
        h1 {
            font-size: 2rem;
        }
        
        .hero-title img {
            height: 2rem;
        }
        
        p {
            font-size: 1rem;
        }
    }
</style>
