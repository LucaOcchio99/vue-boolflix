<template>
  <section>
      <div class="col" v-for="item in list" :key="item.id">
          <div class="card">
             <!-- <ul>
                  <li>Titolo: {{ item.title }}</li>
                  <li>Titolo Originale: {{ item.original_title }}</li>
                  <li>Lingua: {{ item.original_language }}</li>
                  <li>voto: {{ item.voto_average }} </li>
              </ul> -->
          </div> 
          <Card 
             :title="item.title ? item.title : item.name"
             :originalTitle="item.original_title ? item.original_title : item.original_name"
             :language="item.original_language"
             :vote="item.vote_average"
             :poster="item.poster_path"
          />
      </div>
  </section>
</template> 

<script>
import Card from '@/components/Card.vue';

export default { 
  name: 'CardList',
  components : {
     Card
  },
  props: {
    list: Array,
},
};
</script>

<style scoped lang="scss">

</style>