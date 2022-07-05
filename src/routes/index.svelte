<script lang="ts">
	/**
	 * @type {any}
	 */
	let dialog: any;
	import {
		Card,
		CardContent,
		Page,
		Input,
		InputGroup,
		Button,
		CardTitle,
		Modal,
		ModalContent
	} from '@softengy/components';

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

<Page class="grid place-content-center bg-slate-200">
	<Card class="w-96 bg-base-100">
		<CardContent>
			<CardTitle class="uppercase place-content-center">iniciar sesión</CardTitle>

			<button on:click={setCookie} class="btn btn-primary" on:click={setCookie}>set cookie</button>
			<InputGroup>
				<span slot="label" class="label-text">Correo</span>
				<Input placeholder="Tu correo" />
			</InputGroup>
			<InputGroup>
				<span slot="label" class="label-text">Contraseña</span>
				<Input placeholder="Tu contraseña" type="password" on:input={(e) => console.log(e)} />
			</InputGroup>
			<div class="flex mt-2">
				<div class="flex-2 px-2">
					<Button color="primary" full animation on:click={dialog.open}>crear</Button>
				</div>
				<div class="flex-1 px-2">
					<Button full color="success" on:click={handleSubmit} loading={false} disable={false}
						>iniciar sesión</Button
					>
				</div>
			</div>
		</CardContent>
	</Card>
</Page>

<!-- Modal Sign In-->
<Modal bind:this={dialog}>
	<ModalContent close={dialog.close}>
		<h3 class="text-[1.5rem] font-bold text-center uppercase mb-5">Crear cuenta</h3>

		<InputGroup>
			<span slot="label" class="label-text">Nombre</span>
			<Input placeholder="Tu nombre completo" />
		</InputGroup>
		<InputGroup>
			<span slot="label" class="label-text">Correo</span>
			<Input placeholder="Tu correo" />
		</InputGroup>
		<InputGroup>
			<span slot="label" class="label-text">Contraseña</span>
			<Input placeholder="Tu contraseña" />
		</InputGroup>
		<div class="flex mt-10">
			<div class="flex-2 px-2">
				<Button color="error" full animation on:click={dialog.close}>cancelar</Button>
			</div>
			<div class="flex-1 px-2">
				<Button color="success" on:click={handleSubmit} full>aceptar</Button>
			</div>
		</div>
	</ModalContent>
</Modal>
