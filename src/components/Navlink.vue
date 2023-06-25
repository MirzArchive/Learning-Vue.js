<template>
  <a :href="page.link.url" class="nav-link" :class="activeClasses" aria-current="page"
    :title="`This nav-button goes to ${page.link.name} page.`">{{ page.link.name }}
  </a>
</template>

<script>
export default {
		props: ['page', 'isActive'],
    computed: {
      activeClasses() {
        return {
          active: this.isActive,
          emphasize: this.isActive
        };
      }
    }
	}
</script>

<style lang="css" scoped>
  .emphasize {
    text-decoration: underline;
  }
</style>
