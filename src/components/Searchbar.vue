<template>
    <header class="">

        <section class="container">

            <div class="row">
                <div id="ms_main-logo" class="col-4">
                    <img src="../assets/boolflix-logo.png" alt="Boolflix-logo">
                </div>

                <div id="ms_searchbar" class="col-8 d-flex justify-content-end align-items-center">

                    <input type="text" v-model="searchKey" @keyup=" $emit('keyup', searchKey)">
                    <button class="btn btn-light" @click=" $emit('click', searchKey)">click</button>
                    
                </div>

                
            </div>

        </section>

    </header>

</template>

<script>

export default {
    name : 'Searchbar',
    data: function(){
        return{
            searchKey : '',
            movieList : [],
            tvList : [],

        }
    },
    


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