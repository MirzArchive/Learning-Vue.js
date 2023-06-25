<template>
  <div id="content" class="container">
    <h1 class="emphasize">{{ page.title }}</h1>
    <p>{{ page.content }}</p>
  </div>
</template>

<script>
	export default {
		props: {
			page: {
				type: Object,
				default(rawPost) {
					return {
						title: '',
						content: ''
					}
				}
			}
		}
	}
</script>

<style lang="css" scoped>
.emphasize {
  color: blue;
}
</style>