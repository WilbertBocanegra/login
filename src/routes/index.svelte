<script lang="ts">
	/**
	 * @type {any}
	 */
	let dialog: any;

	const handleSubmit = async () => {
		console.log('working');
		const res = await fetch('http://localhost:3000/auth/login', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			credentials: 'include',
			body: JSON.stringify({ email: 'wilbertbocanegra@gmail.com', password: 'bocanegra' })
		});

		const data = await res.json();
		console.log(data);
	};

	const setCookie = () => {
		document.cookie = 'isAuth=true';
		document.cookie = 'auth=adasdasdasd12312hgcdvas';
	};
</script>
<button on:click={setCookie} class="btn btn-primary" on:click={setCookie}>set cookie</button>
