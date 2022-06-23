<template>

  <div class="container  mt-5 mb-5">
    <div class="row">
      <div class="col-11">

        <!-- <form @submit="findCharacter"> -->
        <input 
        type="text" 
        placeholder="Find a character"
        v-model='name'
        @keyup.enter="findCharacter">
        </div>

        <div class="col-1">
        <i class="fa-solid fa-magnifying-glass" @click="findCharacter"></i>
        </div>
        <!-- </form> -->

        


         <!-- {{characters.results}} -->

            <div class="col-lg-3 col-md-6 col-sm-12 mt-5 mb-5 d-flex justify-content-around" v-for="(filterCharacter, index) of filterCharacters" :key="index">

                
                    <router-link :to="`/characters/${filterCharacter.id}`">
                    <div class="mycard text-center">


                    <img class="imgCard" :src="filterCharacter.image" alt="">
                    <h3 class="character-name">{{filterCharacter.name}}</h3>

                    <span v-if="filterCharacter.species === 'Human'" class="dotgreen"></span>
                    <span v-else class="dotblue"></span>

                    <h3 class="character-species"> {{filterCharacter.species}}</h3>
                    <h3 class="character-origin">{{filterCharacter.origin.name}}</h3>
                    <br>
                

                    </div>
                    </router-link>
                

            </div>

    </div>
  </div>

</template>

<script>
export default {
  components: {

  },
  data() {
    return {
      name: '',
      status: '',
      filterCharacters: []
    };
  },
  methods: {
    async findCharacter() {
      try {
        console.log('llegue');
        const data = await fetch(`https://rickandmortyapi.com/api/character/?name=${this.name}`); //&status=${this.status}
        const searchData = await data.json(); 
        console.log("searchData", searchData);
        this.name = searchData;
        this.status = searchData;
        this.filterCharacters = searchData.results;

      } catch (error) {
        console.log(error);
        throw error;
      }
    } 
  }
}
</script>

<style scoped>
input {
    background-color: rgba(100, 87, 158, 0.698);
    border: none;
    border-radius: 5px;
    color: rgb(238, 238, 238);
    font-size: 25px;
    height: 70px;
    width: 1px;
    position: relative;
}

input[type=text] {
  width: 109%;
  padding: 12px 15px;
  margin: 8px 0;
  box-sizing: border-box;
}

input[type=text]:focus {
   outline: none;
   background-color: rgba(100, 87, 158, 0.842);
}

::placeholder {
    color: rgba(199, 199, 199, 0.265);
}

i {
  font-size: 35px;
  color: rgba(190, 190, 190, 0.579);
  cursor: pointer;
  position: relative;
  top: 25px;
  left: 25px;
  /* right: 325px; */
}

i:hover {
  font-size: 35px;
  color: rgba(190, 190, 190, 0.961);
  cursor: pointer;
  position: relative;
  top: 25px;
  left: 25px;
  /* right: 325px; */
}

h3 {
    color: white;
    font-size: 20px;
}

a {
    color: white;
    text-decoration: none;
}

.search {
  height: ;
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
</style>