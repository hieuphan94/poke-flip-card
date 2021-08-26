<template>
  <h1>Choose Level To Have Fun!</h1>
  <div class="level-board">
    <level title="Level 1" content="2 x 2"></level>
    <level title="Level 2" content="4 x 4"></level>
    <level title="Level 3" content="6 x 6"></level>
    <level title="Level 4" content="8 x 8"></level>
    <level title="Level 5" content="10 x 10"></level>
  </div>
</template>
<script>
import Level from "./Level.vue";
export default {
  components: { Level },
};
</script>
<style scoped>
h1 {
  padding: 30px;
  font-size: 25px;
}
.level-board {
  margin: 30px;
  display: flex;
  justify-content: space-around;
  padding: 50px;
  border-radius: 25px;
  border: 1px solid #fff;
}
</style>
