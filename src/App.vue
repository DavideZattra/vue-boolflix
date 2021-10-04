<template>
  <div id="app">
    <Header @keyup="getVideoList" @click="getVideoList"/>
    <Main :movieList='movieList' :tvList='tvList'/>  
  </div>
</template>

<script>
import Header from './components/Searchbar.vue'
import Main from './components/Main-content.vue'
import Axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main, 
  },

  data: function(){
    return{
      movieList: [],
      tvList : [],
    }
  },

  methods: {
    getVideoList(key){

      // this.videoList = [];

      if (key.length > 1){
        Axios.get('https://api.themoviedb.org/3/search/movie?api_key=f6177265d640c21353cbfcd0759d44d7&language=it&query=' + key)
        .then ((answer) => {
            // console.log(answer.data.results)
            this.movieList = [...answer.data.results];

        });

        Axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=' + key)
        .then ((answer) => {
            console.log(answer.data.results)
            this.tvList = [...answer.data.results]
            console.log(this.videoList)
        });
      }

    }
  }
}

</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';


</style>
