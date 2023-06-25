<template>
  <navbar :pages="pages" :active-page="activePage" :nav-page-click="(key) => activePage = key"></navbar>
  <page-viewer :page="pages[activePage]"></page-viewer>
</template>

<script>
import Navbar from './components/NavBar.vue';
import PageViewer from './components/PageViewer.vue';

export default {
  components: {
    Navbar,
    PageViewer
  },
	data() {
		return {
			activePage: 0,
            pages: [
              {
                link: { name: "Home", url: "home.html" },
                title: "Home Page",
                content: "This is the Home content",
              },
              {
                link: { name: "About", url: "about.html" },
                title: "About Page",
                content: "This is the About content",
              },
              {
                link: { name: "Contact", url: "contact.html" },
                title: "Contact Page",
                content: "This is the Contact content",
              },
            ],
		}
	},		
}
</script>