<script>
    const pages = [
        "/resume/resume_page1.jpg",
        "/resume/resume_page2.jpg"
    ];

    const pdfLink = "/resume/resume.pdf";
    let currentPage = 0;

    function nextPage() {
        currentPage = (currentPage + 1) % pages.length;
    }

    function prevPage() {
        currentPage = (currentPage - 1 + pages.length) % pages.length;
    }
</script>

<h1>Resume</h1>
<p>I still don't have one</p>
<h2> T-T </h2>

<div class="carousel">
    <img src={pages[currentPage]} alt={`Resume Page ${currentPage + 1}`} />
    <div class="carousel-controls">
        <button on:click={prevPage}>⟨</button>
        <span>Page {currentPage + 1} of {pages.length}</span>
        <button on:click={nextPage}>⟩</button>
    </div>
</div>

<a href={pdfLink} class="download-btn" target="_blank" download>
    Don't Click PDF
</a>

<style>
    h1 {
        /* text-align: center; */
        /* color: #0ea5e9; */
        margin-bottom: 1.5rem;
    }

    .carousel {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
    }

    .carousel img {
        width: 100%;
        max-width: 800px;
        border: 1px solid #334155;
        border-radius: 8px;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.4);
    }

    .carousel-controls {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1rem;
        color: #cbd5e1;
    }

    .carousel-controls button {
        background-color: #1e293b;
        color: #e5e5e5;
        border: none;
        border-radius: 4px;
        padding: 0.5rem 1rem;
        font-size: 1.2rem;
        cursor: pointer;
    }

    .carousel-controls button:hover {
        background-color: #334155;
    }

    .download-btn {
        display: block;
        margin: 2rem auto;
        background-color: #0ea5e9;
        color: #fff;
        padding: 0.75rem 1.5rem;
        border-radius: 6px;
        text-decoration: none;
        transition: background 0.2s;
        width: 20%;
        text-align: center;
    }

    .download-btn:hover {
        background-color: #0284c7;
    }
</style>