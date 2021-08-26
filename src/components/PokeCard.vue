<template>
  <div class="poke-card">
    <slot name="body" />
    <slot name="footer" />
  </div>
</template>
<script>
export default {};
</script>
<style scoped lang="css">
.poke-card {
  background-color: #fff;
  border-radius: 25px;
  width: 115px;
  height: 150px;
  display: flex;
  align-items: center;
}
.poke-card img {
  width: 100%;
}
</style>
