<template>
  <HeaderComponent></HeaderComponent>
  <component :is="currentView"/>
  <FooterComponent></FooterComponent>
</template>

<script>

import Home from "@/pages/Home";
import Contact from "@/pages/Contact";
import Gallery from "@/pages/Gallery";
import HeaderComponent from "@/components/HeaderComponent";
import FooterComponent from "@/components/FooterComponent";

const routes = {
  '/': Home,
  '/contact': Contact,
  '/gallery': Gallery
}

export default {
  name: 'App',
  components: {
    HeaderComponent,
    FooterComponent
  },
  data() {
    return {
      currentPath: window.location.hash
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/']
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  }
}
</script>

<style>

</style>
