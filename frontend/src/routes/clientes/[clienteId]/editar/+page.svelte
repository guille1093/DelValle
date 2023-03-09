<script>
	import { enhance } from '$app/forms';
	import { invalidateAll } from '$app/navigation';
	import { Icon, Trash } from 'svelte-hero-icons';
	import { Input, TextArea } from '$lib/components';
	import { getImageURL } from '$lib/utils';
	export let data;
	export let form;

	let loading = false;

	const submitUpdateProject = () => {
		loading = true;
		return async ({ result, update }) => {
			switch (result.type) {
				case 'success':
					await invalidateAll();
					break;
				case 'error':
					break;
				default:
					await update();
			}

			loading = false;
		};
	};
</script>

<div class="flex flex-col w-full h-full p-2">
	<div class="w-full">
		<form
			method="POST"
			action="?/updateCliente"
			class="flex flex-col space-y-2 w-full items-center"
			enctype="multipart/form-data"
			use:enhance={submitUpdateProject}
		>
			<h3 class="text-3xl font-bold">Editar {data.cliente.nombre}</h3>
			<Input
				id="nombre"
				label="Nombre"
				value={form?.data?.nombre ?? data.cliente.nombre}
				errors={form?.errors?.nombre}
			/>
			<Input
				id="apellido"
				label="Apellido"
				value={form?.data?.apellido ?? data.cliente.apellido}
				errors={form?.errors?.apellido}
			/>
			<Input
				id="email"
				label="Email"
				value={form?.data?.email ?? data.cliente.email}
				errors={form?.errors?.email}
			/>
			<Input
				id="telefono"
				label="Telefono"
				value={form?.data?.telefono ?? data.cliente.telefono}
				errors={form?.errors?.telefono}
			/>
			<Input
				id="domicilio"
				label="Domicilio"
				value={form?.data?.domicilio ?? data.cliente.domicilio}
				errors={form?.errors?.domicilio}
			/>
<!--nacionalidad-->
			<Input
				id="nacionalidad"
				label="Nacionalidad"
				value={form?.data?.nacionalidad ?? data.cliente.nacionalidad}
				errors={form?.errors?.nacionalidad}
			/>
<!--			fecha nacimiento-->
			<Input
				id="fechanacimiento"
				label="Fecha de nacimiento"
				value={form?.data?.fechanacimiento ?? data.cliente.fechanacimiento}
				errors={form?.errors?.fechanacimiento}
			/>
<!--ocupacion -->
			<Input
				id="ocupacion"
				label="Ocupacion"
				value={form?.data?.ocupacion ?? data.cliente.ocupacion}
				errors={form?.errors?.ocupacion}
			/>
<!--			sexo-->
			<Input
				id="sexo"
				label="Sexo"
				value={form?.data?.sexo ?? data.cliente.sexo}
				errors={form?.errors?.sexo}
			/>
<!--			nombremadre-->
			<Input
				id="nombremadre"
				label="Nombre de la madre"
				value={form?.data?.nombremadre ?? data.cliente.nombremadre}
				errors={form?.errors?.nombremadre}
			/>
<!--			apellido madre-->
			<Input
				id="apellidomadre"
				label="Apellido de la madre"
				value={form?.data?.apellidomadre ?? data.cliente.apellidomadre}
				errors={form?.errors?.apellidomadre}
			/>
			<div class="w-full max-w-lg pt-3">
				<button type="submit" class="btn btn-primary w-full max-w-lg">Guardar cambios</button>
			</div>
		</form>
	</div>
</div>
