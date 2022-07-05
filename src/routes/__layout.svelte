<script>
	import '@softengy/components/src/app.css';
	import '../app.css';
	import { setClient } from '@softengy/components';
	/**
	 * @type {RequestInfo | URL}
	 * @const
	 */
	const endpoint = 'http://localhost:3000';
	setClient({
		endpoint: endpoint,
		config: {
			headers: {
				'Content-Type': 'application/json'
			},
			credentials: 'include'
		}
	});
</script>

<slot />
