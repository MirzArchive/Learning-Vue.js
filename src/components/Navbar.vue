<template>
  <nav :class="[`navbar-${this.theme}`, `bg-${this.theme}`, 'navbar', 'navbar-expand-lg']">
    <div class="container-fluid">
      <a href="#" class="navbar-brand">My Vue</a>
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li v-for="(page, key) in publishedPages" class="nav-item" :key="key">
          <navlink :page="page" :is-active="activePage == key" @click.prevent="navPageClick(key)"></navlink>
        </li>
      </ul>
      <form class="d-flex">
        <button class="btn btn-primary" @click.prevent="swapTheme()">Toggle</button>
      </form>
    </div>
  </nav>
</template>

<script>
import Navlink from './Navlink.vue';

export default {
  computed: {
    publishedPages() {
      return this.pages.filter(p => p.published)
    }
  },
  components: {Navlink},
  props: ["pages", "activePage", "navPageClick"],
  created() {
    this.getThemeSetting()
  },
  data() {
    return {
      theme: "light",
    };
  },
  methods: {
    swapTheme() {
      this.theme = this.theme == 'dark' ? 'light' : 'dark'
      this.storeThemeSetting()
    },
    storeThemeSetting() {
      localStorage.setItem('theme', this.theme)
    },
    getThemeSetting() {
      let theme = localStorage.getItem('theme')

      // Check if theme is not empty or null
      if (theme) this.theme = theme;
    }
  },
};
</script>
