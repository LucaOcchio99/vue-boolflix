<template>
  <div id="app">
    <Header @search="performeSearch" />

    <main>
       <CardList  :list="movieList"/>
    </main>
  
  </div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/Header.vue';
import CardList from '@/components/CardList.vue';

export default {
  name: 'App',
  components: {
    Header,
    CardList
  },
  data() {
     return {
       movieList: [],
     }
  },
  methods: {
    performeSearch(searchText) {
       console.log(searchText);

       if(searchText !== '') {
         /**
          * Axios
          * 
          * prendi film da api
          */
         axios.get('https://api.themoviedb.org/3/search/movie' , {
           params: {
             api_key: '41932bfd7e7cbdeda3a0d2c00766f28d',
             query: searchText,
             language: 'it-It'
           }
         })
         .then(result => {
           this.movieList = result.data.results;
         })
       }
    }
  }
}
</script>

<style lang="scss">

</style>
