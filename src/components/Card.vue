<template>
<div class="card_container">
   <div class="card">
      <div class="card_front">
       <img
         class="movie_image"
         v-if="poster"
         :src="`https://image.tmdb.org/t/p/w342${poster}`" 
         :alt="title"
         />
        
         <img
            class="movie_image"
            v-else   
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ_6OlH2tebRRaJ0shk0sKiGlsk_fXM5RpL9s18JTHQDQ1tlbau0zQADbbGwuKhkljMg0s&usqp=CAU"
            alt="title">
        </div> 

        <div class="card_back">    
       <ul>
                <li> <p><strong>Titolo:</strong> {{ title }}</p> </li>
                <li> <p><strong>Titolo Originale:</strong> {{ originalTitle }}</p> </li>
                <li>
                  <p> <strong>Lingua:</strong> 
                    <img class="flag" 
                    v-if="isFlag" 
                    :src="require(`../assets/${language}.png`)" 
                    :alt="language" 
                    />
                    <span v-else>{{ language }}</span>
                  </p>
                </li>
                <li>
                   <p> <strong>Voto: </strong>
                    <i class="fas fa-star" v-for="item in Math.round(vote)" :key="item" ></i>
                    <i class="far fa-star" v-for="item in (5 - vote)" :key="item"></i>
                    </p>
                </li>
       </ul>
       </div>
   </div>
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
  },
  
};
</script>

<style scope lang="scss">
    .card_container {
    
    width: 100%;
	padding: 50px 0;
	text-align: center;
	-webkit-perspective: 800px;
	-moz-perspective: 800px;
	-o-perspective: 800px;
	-ms-perspective: 800px;
	perspective: 800px;
 
 .card {

    position: relative;
	width: 250px;
	height: 350px;
	display: inline-block;
	margin: 0 10px 20px 10px;
	cursor: default;
	-webkit-transition: all 0.8s ease-in-out;
	-moz-transition: all 0.8s ease-in-out;
	-o-transition: all 0.8s ease-in-out;
	-ms-transition: all 0.8s ease-in-out;
	transition: all 0.8s ease-in-out;
	-webkit-transform-style: preserve-3d;
	-moz-transform-style: preserve-3d;
	-o-transform-style: preserve-3d;
	-ms-transform-style: preserve-3d;
	transform-style: preserve-3d;

    ul li {
        list-style: none;
    }

    .flag {
          width: 30px;
     }

     .movie_image {
         height: 350px;
         width: 250px;
     }
 }
}
 
.card:hover {
	-webkit-transform: rotate3d(0,1,0,-180deg);
	-moz-transform: rotate3d(0,1,0,-180deg);
	-o-transform: rotate3d(0,1,0,-180deg);
	-ms-transform: rotate3d(0,1,0,-180deg);
	transform: rotate3d(0,1,0,-180deg);
}

.card_front {
	position: absolute;
	width: 100%;
	height: 100%;
}

.card_back {
	
    background-color: #fcfcfc;
	width: 100%;
	height: 100%;
	-webkit-transform: rotate3d(0,1,0,180deg);
	-moz-transform: rotate3d(0,1,0,180deg);
	-o-transform: rotate3d(0,1,0,180deg);
	-ms-transform: rotate3d(0,1,0,180deg);
	transform: rotate3d(0,1,0,180deg);
	-webkit-backface-visibility: hidden;
	-moz-backface-visibility: hidden;
	-o-backface-visibility: hidden;
	-ms-backface-visibility: hidden;
	backface-visibility: hidden;

    p {
    color: #555;
	margin: 0 10px;
	padding: 10px 5px;
	border-top: 1px solid #000;
	font-size: 14px;
	font-style: italic;
    }

}


</style>