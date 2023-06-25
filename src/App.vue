<template>
  <navbar :pages="pages" :active-page="activePage" :nav-page-click="(key) => activePage = key"></navbar>
  <page-viewer :page="pages[activePage]" v-if="pages != null"></page-viewer>
</template>

<script>
import Navbar from './components/NavBar.vue';
import PageViewer from './components/PageViewer.vue';
import '../node_modules/bootstrap/dist/css/bootstrap.css'

export default {
  components: {
    Navbar,
    PageViewer
  },
  created() {
    this.setPages()
  },
	data() {
		return {
			activePage: 0,
            pages: []
		}
	},
  methods: {
    async setPages () {
      let res = await fetch('pages.json')
      let data = await res.json()

      this.pages = data
    }
  }
}
</script>