<template>
  <div class="d-flex justify-content-center mt-5 mb-5">
    <input type="text" placeholder="Find a character">
  </div>

</template>

<script>
export default {

}
</script>

<style scoped>
input {
    background-color: rgb(100, 87, 158);
    border: none;
    border-radius: 5px;
    color: white;
    font-size: 25px;
    height: 70px;
    width: 1300px;
}

input[type=text] {
  width: 100%;
  padding: 12px 15px;
  margin: 8px 0;
  box-sizing: border-box;
  /* background-image: url(''); */
  /* background-position: 10px 10px; */
  /* padding-left: 40px; */
}

::placeholder {
    color: rgb(228, 228, 228);
}
</style>