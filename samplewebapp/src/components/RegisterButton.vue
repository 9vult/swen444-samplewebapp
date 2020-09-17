<template>
  <div id="regbtn">
    <input type="submit" value="Register" class="btn" @click="$emit('reg-show')">
  </div>
</template>

<script>
export default {
  name: 'RegisterButton'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.btn {
  display: inline-block;
  border: none;
  background: #42b983;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #174625;
}
</style>
