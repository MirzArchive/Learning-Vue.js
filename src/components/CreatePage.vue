<template>
	<div class="container mb-3">
		<form action="">
			<div class="mb-3">
				<div class="form-label">Page Title</div>
				<input
					type="text"
					name=""
					id=""
					class="form-control"
					v-model="pageTitle"
				>
			</div>
			<div class="mb-3">
				<label
					for=""
					class="form-label"
				>Content</label>
				<textarea
					type="text"
					class="form-control"
					name=""
					id=""
					cols="30"
					rows="10"
					v-model="pageContent"
				></textarea>
			</div>
			<div class="mb-3">
				<button
					class="btn btn-primary"
					@click.prevent="pageCreated({pageTitle, pageContent})"
				>Create Page</button>
			</div>
		</form>
	</div>
</template>

<script>
	export default {
		props: ['pageCreated'],
		data() {
			return {
				pageTitle: '',
				pageContent: ''
			}
		}		
	}
</script>

<style scoped></style>