<template>

 <div class="container">
    <router-link :to="`/`"><div class="trapecio"><i class="returnicon fa-solid fa-angle-left"></i><h3 class="return">Back</h3></div></router-link>
      <div class="row">
          <div class="col-12">
              <div class="mycard"> 

                <div class="row">
                  <div class="col-6">

                  <h3 class="character-name mb-4">{{ character.name }}</h3>
                  <hr>

                  <div class="features-div">
                    <h3>Species: {{ character.species }}</h3>
                  </div>

                  <div class="features-div">
                    <h3>Gender: {{ character.gender }}</h3>
                  </div>

                  <div v-if="character.status === 'Alive'" class="features-div"> 
                      <h3>Status: {{ character.status }} <i class="fa-solid fa-heart-pulse"></i> </h3> 
                  </div>
                  <div v-if="character.status === 'Dead'" class="features-div"> 
                      <h3>Status: {{ character.status }} <i class="fa-solid fa-skull-crossbones"></i> </h3> 
                  </div>
                  <div v-if="character.status === 'unknown'" class="features-div"> 
                      <h3>Status: {{ character.status }} <i class="fa-solid fa-circle-question"></i> </h3> 
                  </div>

                  <div class="features-div">
                    <h3 class="location-font">Actual location: {{ character.location.name }}</h3> 
                  </div>

                  </div>

                  <div class="col-6">

                    <div class="text-center">
                        <img class="img-card" :src="character.image" alt="">
                    </div>

                  </div>
                </div>

              </div>
          </div>
     </div>
 </div>


</template>

<script>
export default {
    data() {
        return {
            character: {}
        }
    },
    methods: {
        async showCharacter() {
            try {
                const data = await fetch(`https://rickandmortyapi.com/api/character/${this.$route.params.id}`);
                const characterData = await data.json();
                this.character = characterData;
            } catch (error) {
                console.log(error);
                throw error;
            }
        }
    },
    created() {
        this.showCharacter();
    }
}
</script>

<style scoped>

.return {
    position: relative;
    top: -2px;
    left: 65px;
    font-size: 20px;
}

.returnicon {
    position: relative;
    top: 24px;
    left: 48px;
}

hr {
    color: greenyellow;
    border-top: 4px solid greenyellow;
    width: 500px;
    position: relative;
    top: -30px;
    left: 0px;
}

.container {
    height: 100vh;
}

.mycard {
  /* background-color: aliceblue; */
  background-color: #16abc9ca;
  border-color: #D2DA4B;
  border-radius: 10px;
  border-style: solid;
  border-width: 5px;
  box-shadow: 0px 20px 40px rgb(26, 25, 25);
  padding: 100px;
  position: relative;
  top: 100px;
  height: 600px;
  
}

.character-name {
  font-size: 50px;
  font-weight: 800;
  color: white;
  position: relative;
  top: -20px;
  
}

.features-div {
    background-color: #d3da4bd0;
    width: 500px;
    padding: 8px;
    border-radius: 10px;
    margin-top: 5px;
}

.img-card {
    border-radius: 250px;
    height: 400px;
}

.location-font {
    font-size: 25px;
}

.trapecio {
    width: 250px;
    height: 0px;
    border-color: #D2DA4B;
    border-right: 40px solid transparent;
    border-left: 40px solid transparent;
    border-bottom: 60px solid #D2DA4B;
    position:relative;
    top: 100px;
    left: 20px;
}

</style>