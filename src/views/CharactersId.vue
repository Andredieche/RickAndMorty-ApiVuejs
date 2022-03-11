<template>
  <div class="container">
      <h1>Personajes por ID</h1>
      <div class="row">
          <div class="col">
              <div class="card">  
                  <h3>{{ character.name }}</h3>
                  <h3>{{ character.status }}</h3>
                  <h3>{{ character.species }}</h3>
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

<style>
div .container {
    height: 100vh;
}
.card {
  background-color: aliceblue;
  padding: 100px;
}
</style>