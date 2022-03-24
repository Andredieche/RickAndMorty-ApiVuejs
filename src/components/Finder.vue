<template>

  <div class="container  mt-5 mb-5">
    <div class="row">
      <div class="col-11">
        <input 
        type="text" 
        placeholder="Find a character"
        v-model="nameCharacter"
        @keyup.enter="findCharacter">
        </div>
        <div class="col-1">
        <i class="fa-solid fa-magnifying-glass"></i>
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
      nameCharacter: ''
    };
  },
  methods: {
    async findCharacter() {
      try {
        console.log(llegue);
        const data = await fetch();
        const characterData = await data.json(); //arreglar esto
        this.nameCharacter = characterData;
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
    color: white;
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
  background: '../assets/fondo2.png';
  /* background-position: 10px 10px; */
  /* padding-left: 40px; */
}

::placeholder {
    color: rgb(228, 228, 228);
}

i {
  font-size: 35px;
  color: rgba(190, 190, 190, 0.685);
  position: relative;
  top: 25px;
  left: 25px;
  /* right: 325px; */
}

.search {
  height: ;
}
</style>