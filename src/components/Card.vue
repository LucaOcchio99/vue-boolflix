<template>
   <div class="card">
       <img
         v-if="poster"
         :src="`https://image.tmdb.org/t/p/w342${poster}`" 
         :alt="title"
         />
        
         <img
            v-else   
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ_6OlH2tebRRaJ0shk0sKiGlsk_fXM5RpL9s18JTHQDQ1tlbau0zQADbbGwuKhkljMg0s&usqp=CAU"
            alt="title">
       <ul>
                <li>Titolo: {{ title }}</li>
                <li>Titolo Originale: {{ originalTitle }}</li>
                <li>
                    Lingua: 
                    <img class="flag" 
                    v-if="isFlag" 
                    :src="require(`../assets/${language}.png`)" 
                    :alt="language" 
                    />
                    <span v-else>{{ language }}</span>
                </li>
                <li><i class="fas fa-star" v-for="item in vote" :key="item" ></i></li>
                
       </ul>
   </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
      poster: String,
      title: String,
      originalTitle: String,
      language: String,
      vote: Number,
  },
  data() {
      return {
          availableFlags: ['it', 'en'],
      }
  },
  computed: {
      isFlag() {
          return this.availableFlags.includes(this.language);
      }
  }
};
</script>

<style scope lang="scss">
 .card {
    .flag {
          width: 30px;
     }
 }
</style>