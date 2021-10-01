<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from './components/Searchbar.vue'
import Main from './components/Main-content.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
    
  }
}

</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';

</style>
