<script>
    // Add any props or logic here
</script>

<section class="main-section">
    <div class="container">
        <h1>Welcome to LOST</h1>
        <p>This is the main hero section of your website.</p>
        <!-- Add your main content here -->
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

    h1 {
        font-size: 3rem;
        color: #0ea5e9;
        margin-bottom: 1rem;
    }

    p {
        font-size: 1.2rem;
        color: #cbd5e1;
    }

    @media (max-width: 768px) {
        h1 {
            font-size: 2rem;
        }
        p {
            font-size: 1rem;
        }
    }
</style>
