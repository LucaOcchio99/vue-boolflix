<template>
  <header>

    <div class="left">
      <img src="@/assets/boolflix.png" alt="">
       <ul>
         <li><a href="">Home</a></li>
         <li><a href="">Serie TV</a></li>
         <li><a href="">Film</a></li>
         <li><a href="">Originali</a></li>
         <li><a href="">Aggiunti di recente</a></li>
         <li><a href="">La mia lista</a></li>
       </ul>
    </div>

    <div class="right">
      <input 
      type="text" placeholder="Search a movie"
      v-model.trim="searchText"
      @keyup.enter="$emit('search' , searchText)"  
        />
      <button @click="$emit('search' , searchText)">Search</button>
    </div>  
  </header>
</template>

<script>
export default {
   name: 'Header',
   data() {
       return {
          searchText: '',
       }
   }
}
</script>

<style scoped lang='scss'>
 header {
   height: 100px;
   background: black;
   padding: 1rem;

   display: flex;
   justify-content: space-between; 

    .left {
       display: flex;
       align-items: center;

      ul {
      display: flex;
      list-style: none;
      
    li {
      padding: 1rem;

      a {
        color: white;   
        text-decoration: none;       
      }
    }

     }
   }
   
    .right {
      display: flex;
      align-items: center;

      button,
      input {
        padding: 1rem;
        margin-left: 1rem;
        border: none;
        border-radius: 2rem;
      }

      button {
        cursor: pointer;
        background: lightcoral;
        color: white;
      }
    } 
 }
</style>