<script>
	const githubUrl = "https://github.com/LostLuinor";
	const linkedinUrl = "https://www.linkedin.com/in/lishanthan-ayyanar-10475629b/";
</script>

<footer>
	<span class="footer-text">© 2025 LOST</span>

	<div class="social-icons">
		<a href={githubUrl} target="_blank" aria-label="GitHub">
			<!-- GitHub Icon -->
			<svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24">
				<path
					d="M12 0C5.37 0 0 5.373 0 12c0 5.303 3.438 9.8 8.205 
					11.385.6.113.82-.258.82-.577v-2.234c-3.338.727-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.729.083-.729 
					1.205.084 1.84 1.236 1.84 1.236 1.07 1.835 2.809 1.305 3.495.998.107-.776.418-1.305.76-1.605-2.665-.304-5.466-1.332-5.466-5.93 
					0-1.31.467-2.38 1.235-3.22-.135-.303-.54-1.524.105-3.176 0 0 1.005-.322 3.3 1.23a11.49 11.49 0 0 1 3.005-.404c1.02.005 
					2.045.138 3.005.404 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.874.12 3.176.765.84 1.23 1.91 
					1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.435.375.81 1.102.81 
					2.222v3.293c0 .315.21.69.825.57C20.565 21.795 24 17.295 
					24 12c0-6.627-5.373-12-12-12z"
				/>
			</svg>
		</a>
		<a href={linkedinUrl} target="_blank" aria-label="LinkedIn">
			<!-- LinkedIn Icon -->
			<svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24">
				<path
					d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.039-1.852-3.039-1.853 
					0-2.136 1.445-2.136 2.939v5.669H9.351V9h3.413v1.561h.049c.476-.9 
					1.637-1.852 3.368-1.852 3.6 0 4.268 2.368 4.268 
					5.451v6.292zM5.337 7.433c-1.144 0-2.067-.926-2.067-2.066 
					0-1.143.923-2.066 2.067-2.066 1.143 0 2.066.923 
					2.066 2.066 0 1.14-.923 2.066-2.066 
					2.066zM6.814 20.452H3.861V9h2.953v11.452zM22.225 
					0H1.771C.792 0 0 .771 0 1.723v20.555C0 23.23.792 24 
					1.771 24h20.451C23.2 24 24 23.23 
					24 22.278V1.723C24 .771 23.2 0 22.225 0z"
				/>
			</svg>
		</a>
	</div>
</footer>

<style>
	footer {
    /* Remove position: fixed, bottom, left, right, height */
    background-color: #0d0d0d;
    /* border-top: 1px solid #334155; */
	height: 50px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 1rem;
    color: #e5e5e5;
    z-index: 999;
}

	.footer-text {
		font-size: 0.875rem;
	}

	.social-icons {
		display: flex;
		gap: 1rem;
	}

	a {
		color: inherit;
		transition: color 0.2s ease;
		display: flex;
		align-items: center;
	}

	a:hover {
		color: #0ea5e9;
	}

	svg {
		width: 20px;
		height: 20px;
	}

	@media (max-width: 600px) {
		footer {
			flex-direction: column;
			align-items: center;
			justify-content: center;
			height: auto;
			padding: 0.5rem;
			text-align: center;
		}

		.social-icons {
			margin-top: 0.3rem;
		}
	}
</style>
