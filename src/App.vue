<template>
  <div id="app">
    <Header @search="performeSearch" />

    <main>
       <CardList  :list="movieList"/>

       <CardList  :list="tvList"/>

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
       tvList: [],
     }
  },
  methods: {
    performeSearch(searchText) {
       console.log(searchText);

       if(searchText !== '') {
         const apiParams = {
           api_key: '41932bfd7e7cbdeda3a0d2c00766f28d',
           query: searchText,
           language: 'it-IT'
         };
         /**
          * Axios
          * 
          * prendi film da api
          */
         axios.get('https://api.themoviedb.org/3/search/movie' , {
           params: apiParams,
         })
         .then(result => {
           this.movieList = result.data.results;
         })
         .catch(err => console.log(err));

          /**
          * Axios
          * 
          * prendi serie da api
          */
         axios.get('https://api.themoviedb.org/3/search/tv' , {
           params: apiParams,
         })
         .then(result => {
           this.tvList = result.data.results;
       })
       .catch(err => console.log(err));
     }
    },
  },
};
</script>

<style lang="scss">

</style>
