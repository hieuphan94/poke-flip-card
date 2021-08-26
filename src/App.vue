<template>
  <div class="container">
    <h1 class="heading">Pokemon Flip Card</h1>
    <game-level></game-level>
  </div>
</template>
<script>
import GameLevel from "./components/GameLevel.vue";
export default {
  name: "App",
  components: { GameLevel },
  data() {
    return {
      pokeList: [
        "1.png",
        "2.png",
        "3.png",
        "4.png",
        "5.png",
        "6.png",
        "7.png",
        "8.png",
        "9.png",
        "10.png",
      ],
    };
  },
  methods: {
    random_item(items) {
      return items[Math.floor(Math.random() * items.length)];
    },
    removedPokes(pokes, item) {
      return pokes.filter((poke) => poke !== item);
    },
    randomPokeList(number) {
      const newPokes = [];
      let pokes = [...this.pokeList];
      for (let i = 0; i < number; i++) {
        var item = this.random_item(pokes);
        pokes = this.removedPokes(pokes, item);
        newPokes.push(item);
      }
      return newPokes;
    },
  },
  mounted() {},
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
}
.heading {
  font-size: 50px;
  padding: 25px;
}
</style>
