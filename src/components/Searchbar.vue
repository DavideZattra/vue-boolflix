<template>
    <header class="">

        <section class="container">

            <div class="row">
                <div id="ms_main-logo" class="col-4">
                    <img src="../assets/boolflix-logo.png" alt="Boolflix-logo">
                </div>

                <div id="ms_searchbar" class="col-8 d-flex justify-content-end align-items-center">

                    <input type="text" v-model="searchKey" @keyup.enter="getVideo(), $emit('keyup.enter', searchKey)">
                    <button class="btn btn-light" @click="getVideo(), $emit('click', searchKey)">click</button>
                    
                </div>

                <!-- <div class="col-2 border ms_movie" v-for="(element,index) in movieList" :key="index"  >

                    <ol  >
                        <li>{{ element.title }}</li>
                        <li>{{ element.original_title }}</li>
                        <li v-if="element.original_language === 'it'"><img src="../assets/Flag_of_Italy.svg.png" alt=""></li>
                        <li  v-else-if="element.original_language === 'en'"><img src="../assets/ukFlag.svg.png" alt=""></li>
                        <li  v-else><img src="../assets/LGBT.svg.png" alt=""></li>
                        <li>{{ element.vote_average }}</li>

                    </ol>

                </div>
                <div class="col-2 border ms_tvserie" v-for="(element,index) in tvList" :key="index"  >

                    <ol  >
                        <li>{{ element.name }}</li>
                        <li>{{ element.original_name }}</li>
                        <li v-if="element.original_language === 'it'"><img src="../assets/Flag_of_Italy.svg.png" alt=""></li>
                        <li v-else-if="element.original_language === 'en'"><img src="../assets/ukFlag.svg.png" alt=""></li>
                        <li  v-else><img src="../assets/LGBT.svg.png" alt=""></li>
                        <li>{{ element.vote_average }}</li>

                    </ol>

                </div> -->

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
            movieList : [],
            tvList : [],

        }
    },
    methods : {
        getVideo(){
            if (this.searchKey.length > 0){

                axios.get('https://api.themoviedb.org/3/search/movie?api_key=f6177265d640c21353cbfcd0759d44d7&language=it&query=' + this.searchKey)
                .then ((answer) => {
                    // console.log(answer.data.results)
                    this.movieList = [...answer.data.results];
    
                });

                axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=' + this.searchKey)
                .then ((answer) => {
                    // console.log(answer.data.results)
                    this.tvList = [...answer.data.results]
                })
            }
        }
    }


}
</script>

<style lang='scss' scoped>
@import '../style/variables.scss';

header{
    background-color: $headerBgColor;
    img{
        height : 75px;
    }

    .ms_tvserie,
    .ms_movie{
        img{
            height: 10px;
        }
    }
}
</style>