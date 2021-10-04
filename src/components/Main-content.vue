<template>

  <main>

    <section class="container">

      <div class="row justify-content-center">
        <div v-if="movieList.length > 0" class="col-12 text-white">
          <h2>Ecco i risultati per i film: </h2>
        </div>
        <div class="col-3 text-white ms_video-card m-4" v-for="(element, index) in movieList" :key='index'>

          <div class="ms_cover-image">
            <img :src="imgBaseUrl + element.poster_path" :alt="element.title">
          </div>
          
          <ul class="p-5 " >
            <li><span class="fw-bold">Titolo:</span> {{ element.title }}</li>
            <li><span class="fw-bold">Titolo originale:</span> {{ element.original_title }}</li>
            <li><span class="fw-bold">Voto:</span> {{ element.vote_average }}</li>
            <li><span class="fw-bold">Overview:</span> {{ element.overview}}</li>
          </ul>

        </div>

        <div v-if="tvList.length > 0" class="col-12 text-white">
          <h2>Ecco i risultati per le serie tv :</h2>
        </div>

        <div class="col-3 text-white ms_video-card m-4" v-for="(element, index) in tvList" :key='index'>

          <div class="ms_cover-image">
            <img :src="imgBaseUrl + element.poster_path" :alt="element.name">
          </div>
          
          <ul class="p-5 " >
            <li><span class="fw-bold">Titolo:</span> {{ element.name }}</li>
            <li><span class="fw-bold">Titolo originale:</span> {{ element.original_name }}</li>
            <li><span class="fw-bold">Voto:</span> {{ element.vote_average }}</li>
            <li><span class="fw-bold">Overview:</span> {{ element.overview}}</li>
          </ul>

        </div>

      </div>

    </section>

  </main>

</template>

<script>
export default {
  name : 'Main',
  props: ['movieList', 'tvList'],
  data: function(){
    return{
      imgBaseUrl : 'https://image.tmdb.org/t/p/w342/'
    }
  }
}
</script>

<style lang='scss' scoped>
@import '../style/variables.scss';

ul{
  list-style: none;
}

main{
  min-height: calc(100vh - 75px);
  background-color: $mainBgColor;

  .ms_video-card{
    background-color: $headerBgColor;
    overflow: scroll;
    height: 375px;

    .ms_cover-image{
      height: 100%;
      overflow: hidden;
      img{
        height: 100%;
        width: 100%;
        object-fit: cover;
      }

    }

    ul{
      display: none;
      

      li{
        font-size: 0.8rem;
      }
    }

    &:hover ul{
      display: block;
    }

    &:hover .ms_cover-image{
      display: none;
    }
  }
}
</style>