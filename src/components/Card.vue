<template>
   <div class="card">
       <ul>
                <li>Titolo: {{ title }}</li>
                <li>Titolo Originale: {{ originalTitle }}</li>
                <li>
                    Lingua: 
                    <img 
                    v-if="isFlag" 
                    :src="require(`../assets/${language}.png`)" 
                    :alt="language" 
                    />
                    <span v-else>{{ language }}</span>
                </li>
                <li>voto: {{ vote }} </li>
       </ul>
   </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
      title: String,
      originalTitle: String,
      language: String,
      vote: Number
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
    img {
        width: 30px;
    }
}
</style>