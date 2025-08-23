<script>
    // Add contact form logic here
    let name = '';
    let email = '';
    let message = '';

    function handleSubmit() {
        // Add your form submission logic here
        alert("LMAO....the button doesn't work");
        console.log('Form submitted:', { name, email, message });
        // You can integrate with a backend service or email service
    }
</script>

<section class="contact-section" id="contact">
    <div class="container">
        <h2>(Contact...)</h2>
        <div class="contact-content">
            <div class="contact-info">
                <h3>Get in Touch</h3>
                <p>Feel free to reach out if you have any questions or would like to collaborate on a project.</p>
                
                <div class="contact-item">
                    <strong>Email:</strong>
                    <a href="mailto:lishanthansriayyanar@gmail.com">lishanthansriayyanar@gmail.com</a>
                </div>
                
                <div class="contact-item">
                    <strong>GitHub:</strong>
                    <a href="https://github.com/LostLuinor" target="_blank" rel="noopener noreferrer">
                        github.com/LostLuinor
                    </a>
                </div>
                
                <div class="contact-item">
                    <strong>LinkedIn:</strong>
                    <a href="https://www.linkedin.com/in/lishanthan-ayyanar-10475629b/" target="_blank" rel="noopener noreferrer">
                        linkedin.com/in/lishanthansriayyanar
                    </a>
                </div>
            </div>
            
            <form class="contact-form" on:submit|preventDefault={handleSubmit}>
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" id="name" bind:value={name} required />
                </div>
                
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" bind:value={email} required />
                </div>
                
                <div class="form-group">
                    <label for="message">Message</label>
                    <textarea id="message" bind:value={message} rows="5" required></textarea>
                </div>
                
                <button type="submit" class="submit-btn">Send Message</button>
            </form>
        </div>
    </div>
</section>

<style>
    .contact-section {
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
        color: #ffffff;
        margin-bottom: 3rem;
        /* text-align: center; */
    }

    .contact-content {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 4rem;
        align-items: start;
    }

    .contact-info h3 {
        color: #e5e5e5;
        margin-bottom: 1rem;
        font-size: 1.5rem;
    }

    .contact-info p {
        color: #cbd5e1;
        line-height: 1.6;
        margin-bottom: 2rem;
    }

    .contact-item {
        margin-bottom: 1rem;
        color: #cbd5e1;
    }

    .contact-item a {
        color: #0ea5e9;
        text-decoration: none;
        margin-left: 0.5rem;
    }

    .contact-item a:hover {
        text-decoration: underline;
    }

    .contact-form {
        background-color: #1e293b;
        padding: 2rem;
        border-radius: 8px;
        border: 1px solid #334155;
    }

    .form-group {
        margin-bottom: 1.5rem;
    }

    .form-group label {
        display: block;
        margin-bottom: 0.5rem;
        color: #e5e5e5;
        font-weight: 500;
    }

    .form-group input,
    .form-group textarea {
        width: 100%;
        padding: 0.75rem;
        background-color: #0f172a;
        border: 1px solid #334155;
        border-radius: 4px;
        color: #e5e5e5;
        font-family: inherit;
        box-sizing: border-box;
    }

    .form-group input:focus,
    .form-group textarea:focus {
        outline: none;
        border-color: #0ea5e9;
    }

    .submit-btn {
        background-color: #0ea5e9;
        color: #fff;
        border: none;
        padding: 0.75rem 2rem;
        border-radius: 4px;
        cursor: pointer;
        font-size: 1rem;
        transition: background-color 0.2s ease;
    }

    .submit-btn:hover {
        background-color: #0284c7;
    }

    @media (max-width: 768px) {
        .contact-section {
            padding: 3rem 0;
        }
        
        h2 {
            font-size: 2rem;
        }
        
        .contact-content {
            grid-template-columns: 1fr;
            gap: 2rem;
        }
        
        .contact-form {
            padding: 1.5rem;
        }
    }
</style>
