<template>
<Header/>

<div class="container">
    <div class="row">

        <Finder/>

        <div>
        <h1>List of characters</h1> 
        <hr>
        </div>


            <!-- {{characters.results}} -->

            <div class="col-lg-3 col-md-6 col-sm-12 mt-5 mb-5 d-flex justify-content-around" v-for="(character, index) of characters" :key="index">
                
                    <router-link :to="`/characters/${character.id}`">
                    <div class="mycard text-center">


                    <img class="imgCard" :src="character.image" alt="">
                    <h3 class="character-name">{{character.name}}</h3>

                    <span v-if="character.species === 'Human'" class="dotgreen"></span>
                    <span v-else class="dotblue"></span>

                    <h3 class="character-species"> {{character.species}}</h3>
                    <h3 class="character-origin">{{character.origin.name}}</h3>
                    <br>
                

                    </div>
                    </router-link>
                

            </div>

    </div>

</div>
</template>

<script>
import Header from '../components/Header.vue'
import Finder from '../components/Finder.vue'

export default {
    
    components: {
      Header,
      Finder

    },
    data() {
        return {
            characters: []
        }
    },
    methods: {
        async consumirCharacters() {
            try {
              const data = await fetch('https://rickandmortyapi.com/api/character');
              const charactersData = await data.json();
              this.characters = charactersData.results;
              console.log(this.characters);
            } catch (error) {
                console.log(error);
                throw error;
            }
        }


    },

    computed: {

    },

    created() {
        this.consumirCharacters();
    }

}
</script>

<style scoped>

h1 {
    font-size: 40px;
    font-weight: 800;
    color: rgb(255, 255, 255);
    display: inline;
    position: relative;
    left: 10px;
}

hr {
    color: greenyellow;
    border-top: 4px solid greenyellow;
    width: 67%;
    position: relative;
    top: -35px;
    left: 411px;
}

/* .line {
    display: inline;
    height: 3px;
    background: white;
    width: 400px;
    position: relative;
    top: -100px;
} */

h3 {
    color: white;
    font-size: 20px;
}

a {
    color: white;
    text-decoration: none;
}

.character-name {
    font-weight: 800;
}

.dotgreen {
  height: 17px;
  width: 17px;
  background-color: rgb(6, 192, 6);
  border-radius: 50%;
  display: inline-block;
  position: relative;
  left: -5px;
}

.dotblue {
  height: 17px;
  width: 17px;
  background-color: #00b4d3;
  border-radius: 50%;
  display: inline-block;
  position: relative;
  left: -5px;
}

.character-species {
    display: inline-block;
    font-size: 19px;
    font-weight: light;
}

.character-origin {
    font-size: 19px;
}

.imgCard {
    width: 150px;
    border-radius: 100px;
    position: relative;
    top: -35px;
}

.mycard {
    background-color: #16abc9a1;
    border-color: #D2DA4B;
    /* border-color: rgb(106, 14, 149); */
    border-radius: 10px;
    border-style: solid;
    border-width: 5px;
    box-shadow: 0px 20px 40px rgb(26, 25, 25);
    height: 360px;
    padding: 10px;
    width: 280px;
}

.mycard:hover {
    background-color: #16abc9cb;
}

div .container {
    padding: 20px;
}
</style>