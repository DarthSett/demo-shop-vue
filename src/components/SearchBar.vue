<template>
  <div class="SearchInput">
    <label for="search" > </label> <!--small gets turned to red when exceeded class is activated (check style)-->
    <input id="search" placeholder="  Type to search products">
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}

input {
  width: 100%;
  border-radius: 5px;
  border: 0 teal;
  height: 25px;
}

li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
