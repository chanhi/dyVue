<template>
  <div id="app">
    <PageHeader />
    <div class="container">
      <PageMenu/>
      <div class="main">
        <router-view/>
      </div>
    </div>
    <PageFooter/>
  </div>
</template>

<script>
import PageFooter from './components/PageFooter.vue'
import PageHeader from './components/PageHeader.vue'
import PageMenu from './components/PageMenu.vue'
export default {
  components: { PageFooter, PageHeader, PageMenu },
  name: 'App'
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  .container {
    position: relative;
    display: flex;
  }

  .main {
    margin: 0;
    padding: 0;
    width: 100%;
    display: flex;
    justify-content: center;
  }

</style>
