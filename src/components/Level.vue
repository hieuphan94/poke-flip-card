<template>
  <button class="level" @click="onClickLevelHandle">
    <h3>{{ title }}</h3>
    <br />
    <p>{{ content }}</p>
  </button>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      require: true,
    },
    content: {
      type: String,
      require: true,
    },
  },
  methods: {
    onClickLevelHandle() {
      this.$emit("lvclick");
    },
  },
};
</script>
<style scoped>
.level {
  padding: 30px;
  width: 200px;
  height: 200px;
  border-radius: 25px;
  border: 1px solid #fff;
  cursor: pointer;
  background-color: transparent;
  margin: 0 20px;
}
.level h3 {
  font-size: 32px;
  color: #fff;
}
.level p {
  color: #fff;
  font-size: 20px;
}
.level:hover {
  background-color: green;
}
</style>
