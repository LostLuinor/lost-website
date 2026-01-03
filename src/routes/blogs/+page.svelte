<script>
	import BlogCard from '$lib/components/blog/BlogCard.svelte';

	const blogs = [
		{
			title: 'Getting Started with Svelte and SvelteKit',
			description:
				'A comprehensive guide to building modern web applications with Svelte and SvelteKit framework.',
			fullContent: `
				<h2>Introduction</h2>
				<p>Svelte is a radical new approach to building user interfaces. Whereas traditional frameworks like React and Vue do the bulk of their work in the browser, Svelte shifts that work into a compile step that happens when you build your app.</p>
				
				<h2>Why Svelte?</h2>
				<p>Instead of using techniques like virtual DOM diffing, Svelte writes code that surgically updates the DOM when the state of your app changes. This results in faster applications with less code.</p>
				
				<h3>Key Benefits</h3>
				<ul>
					<li>Write less code</li>
					<li>No virtual DOM</li>
					<li>Truly reactive</li>
					<li>Built-in state management</li>
				</ul>
				
				<h2>Getting Started</h2>
				<p>To create a new SvelteKit project, run:</p>
				<pre><code>npm create svelte@latest my-app
cd my-app
npm install
npm run dev</code></pre>
				
				<p>This will scaffold a new project with all the necessary files and dependencies. You can then start building your application by editing the files in the <code>src/routes</code> directory.</p>
				
				<h2>Conclusion</h2>
				<p>Svelte and SvelteKit offer a fresh, efficient approach to web development that's both powerful and enjoyable to use. Give it a try on your next project!</p>
			`,
			imageUrl: '/images/Frame 3.png',
			tags: ['Svelte', 'Web Development', 'Tutorial'],
			date: 'Jan 2, 2026',
			readTime: '5 min read'
		},
		{
			title: 'Building Responsive Web Applications',
			description:
				'Learn the best practices for creating responsive designs that work seamlessly across all devices.',
			fullContent: `
				<h2>The Importance of Responsive Design</h2>
				<p>In today's multi-device world, responsive design is no longer optional—it's essential. Users access websites from smartphones, tablets, laptops, and desktops, each with different screen sizes and capabilities.</p>
				
				<h2>Mobile-First Approach</h2>
				<p>Starting with mobile designs and progressively enhancing for larger screens ensures that your core content and functionality work everywhere.</p>
				
				<h3>Key Techniques</h3>
				<ul>
					<li>Flexible grid layouts</li>
					<li>CSS media queries</li>
					<li>Responsive images</li>
					<li>Touch-friendly interfaces</li>
				</ul>
				
				<h2>CSS Grid and Flexbox</h2>
				<p>Modern CSS layout tools like Grid and Flexbox make it easier than ever to create responsive layouts without relying on frameworks.</p>
				
				<pre><code>.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1rem;
}</code></pre>
				
				<h2>Testing Across Devices</h2>
				<p>Always test your responsive designs on real devices, not just browser emulators. Real-world testing helps you catch issues with touch interactions, performance, and rendering.</p>
			`,
			imageUrl: '/images/LostLogo.png',
			tags: ['CSS', 'Responsive Design', 'UI/UX'],
			date: 'Dec 28, 2025',
			readTime: '7 min read'
		},
		{
			title: 'Introduction to Machine Learning with Python',
			description:
				'Explore the fundamentals of machine learning and how to implement basic algorithms using Python and scikit-learn.',
			fullContent: `
				<h2>What is Machine Learning?</h2>
				<p>Machine Learning is a subset of artificial intelligence that enables computers to learn from data without being explicitly programmed. It's the technology behind recommendation systems, voice assistants, and autonomous vehicles.</p>
				
				<h2>Types of Machine Learning</h2>
				<p>There are three main types of machine learning:</p>
				
				<h3>Supervised Learning</h3>
				<p>The algorithm learns from labeled training data and makes predictions based on that data.</p>
				
				<h3>Unsupervised Learning</h3>
				<p>The algorithm finds patterns in data without predefined labels.</p>
				
				<h3>Reinforcement Learning</h3>
				<p>The algorithm learns by interacting with an environment and receiving rewards or penalties.</p>
				
				<h2>Getting Started with scikit-learn</h2>
				<pre><code>from sklearn.linear_model import LinearRegression
import numpy as np

# Create sample data
X = np.array([[1], [2], [3], [4], [5]])
y = np.array([2, 4, 6, 8, 10])

# Train the model
model = LinearRegression()
model.fit(X, y)

# Make predictions
print(model.predict([[6]]))  # Output: [12.]</code></pre>
				
				<h2>Next Steps</h2>
				<p>Start with simple datasets and algorithms, then gradually work your way up to more complex problems. Practice is key to mastering machine learning!</p>
			`,
			imageUrl: '/images/maze.png',
			tags: ['Python', 'Machine Learning', 'AI'],
			date: 'Dec 20, 2025',
			readTime: '10 min read'
		},
		{
			title: 'Modern JavaScript: ES6+ Features',
			description:
				'Discover the powerful features introduced in ES6 and later versions of JavaScript that make coding more efficient.',
			fullContent: `
				<h2>Arrow Functions</h2>
				<p>Arrow functions provide a more concise syntax for writing function expressions:</p>
				<pre><code>// Traditional function
function add(a, b) {
  return a + b;
}

// Arrow function
const add = (a, b) => a + b;</code></pre>
				
				<h2>Destructuring</h2>
				<p>Destructuring allows you to unpack values from arrays or properties from objects into distinct variables:</p>
				<pre><code>const person = { name: 'John', age: 30 };
const { name, age } = person;

const numbers = [1, 2, 3];
const [first, second] = numbers;</code></pre>
				
				<h2>Template Literals</h2>
				<p>Template literals make string interpolation and multi-line strings much easier:</p>
				<pre><code>const name = 'Alice';
const greeting = \`Hello, \${name}!
Welcome to our site.\`;</code></pre>
				
				<h2>Async/Await</h2>
				<p>Async/await makes asynchronous code look and behave more like synchronous code:</p>
				<pre><code>async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}</code></pre>
				
				<h2>Conclusion</h2>
				<p>These ES6+ features are now widely supported and should be part of every JavaScript developer's toolkit.</p>
			`,
			imageUrl: '/images/emotion.jpg',
			tags: ['JavaScript', 'ES6', 'Programming'],
			date: 'Dec 15, 2025',
			readTime: '6 min read'
		}
	];
</script>

<div class="blogs-container">
	<h1>Blog Posts</h1>
	<p class="subtitle">Thoughts, tutorials, and insights on web development and technology</p>

	<div class="blog-list">
		{#each blogs as blog}
			<BlogCard
				title={blog.title}
				description={blog.description}
				fullContent={blog.fullContent}
				imageUrl={blog.imageUrl}
				tags={blog.tags}
				date={blog.date}
				readTime={blog.readTime}
			/>
		{/each}
	</div>
</div>

<style>
	.blogs-container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 2rem 0;
	}

	h1 {
		color: #0ea5e9;
		margin-bottom: 0.5rem;
		font-size: 2.5rem;
	}

	.subtitle {
		color: #94a3b8;
		font-size: 1.1rem;
		margin-bottom: 3rem;
	}

	.blog-list {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	@media (max-width: 768px) {
		h1 {
			font-size: 2rem;
		}

		.subtitle {
			font-size: 1rem;
		}
	}
</style>

