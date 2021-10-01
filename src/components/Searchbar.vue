<template>
    <header class="">

        <section class="container">

            <div class="row">
                <div id="ms_main-logo" class="col-4">
                    <img src="../assets/boolflix-logo.png" alt="Boolflix-logo">
                </div>

                <div id="ms_searchbar" class="col-8 d-flex justify-content-end align-items-center">

                    <input type="text" v-model="searchKey" @keyup.enter="$emit('getsearchkey', searchKey)">
                    <button class="btn btn-light" @click="getMovies()">click</button>
                    
                </div>

                <div v-for="(element,index) in movieArray" :key="index">

                    <ol>
                        <li>{{ element.title }}</li>
                        <li>{{ element.original_title }}</li>
                        <li v-if="element.original_language === 'it'"><img src="../assets/Flag_of_Italy.svg.png" alt=""></li>
                        <li  v-else-if="element.original_language === 'en'"><img src="../assets/ukFlag.svg.png" alt=""></li>
                        <li>{{ element.vote_average }}</li>
                        <li>{{ element.original_language }}</li>

                    </ol>

                </div>

            </div>

        </section>

    </header>

</template>

<script>
import axios from 'axios';
export default {
    name : 'Searchbar',
    data: function(){
        return{
            searchKey : '',
            movieArray : [],
        }
    },
    methods : {
        getMovies(){
            if (this.searchKey.length > 0){

                axios.get('https://api.themoviedb.org/3/search/movie?api_key=f6177265d640c21353cbfcd0759d44d7&language=it&query=' + this.searchKey)
    
                .then ((answer) => {
    
                    console.log(answer.data.results)
                this.movieArray = [...answer.data.results];
    
                });
            }
        }
    }


}
</script>

<style lang='scss' scoped>
@import '../style/variables.scss';

header{
    // background-color: $headerBgColor;
    img{
        height : 40px;
    }
}
</style>