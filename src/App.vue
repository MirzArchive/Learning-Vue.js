<template>
  <Navbar
    :pages="pages"
    :active-page="activePage"
    :nav-page-click="(key) => activePage = key"
  ></Navbar>
  <PageViewer
    :page="pages[activePage]"
    v-if="pages != null"
  ></PageViewer>

  <CreatePage :page-created="createPage"></CreatePage>
</template>

<script>
import Navbar from './components/NavBar.vue';
import PageViewer from './components/PageViewer.vue';
import CreatePage from './components/CreatePage.vue';
import '../node_modules/bootstrap/dist/css/bootstrap.css'

export default {
  components: {
    Navbar,
    PageViewer,
    CreatePage
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
    },
    createPage(pageObj) {
      console.log(pageObj);
    }
  }
}
</script>