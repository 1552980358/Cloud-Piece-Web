<template>
  <div id="app">
    <!--component v-bind:is="page"></component-->
    <Initial></Initial>
  </div>
</template>

<script>
import Initial from "@/components/initial/Initial";

export default {
  name: 'App',
  components: {
    Initial,
  },
  methods: {
    changePage(page) {
      this.page = page;
    },
  },
  mounted() {
  },
}
</script>

<style>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 !important;
  padding: 0 !important;
}
html, body {
  margin: 0 !important;
  padding: 0 !important;
}
component {
  width: 100vw;
  max-width: 100%;
}

</style>
