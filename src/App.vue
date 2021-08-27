<template>
  <div class="container">
    <h1 class="heading">Pokemon Flip Card</h1>
    <h3>Choose Level To Have Fun!</h3>
    <div class="level-board">
      <level title="Level 1" content="2 x 2" @lvclick="onClickLevel(2)"></level>
      <level title="Level 2" content="4 x 4" @lvclick="onClickLevel(8)"></level>
      <level
        title="Level 3"
        content="6 x 6"
        @lvclick="onClickLevel(18)"
      ></level>
      <level
        title="Level 4"
        content="8 x 8"
        @lvclick="onClickLevel(32)"
      ></level>
      <level
        title="Level 5"
        content="10 x 10"
        @lvclick="onClickLevel(50)"
      ></level>
    </div>
    <div v-if="numberOfCards > 0" class="pokes" :style="cssVars">
      <poke-card
        :imgUrl="poke.img"
        v-for="poke in doublePokeList"
        :key="poke"
      ></poke-card>
    </div>
  </div>
</template>
<script>
import Level from "./components/Level.vue";
import PokeCard from "./components/PokeCard.vue";
export default {
  name: "App",
  components: { Level, PokeCard },
  data() {
    return {
      pokeList: [],
      pokeListLevel: [],
      doublePokeList: [],
      numberOfCards: 0,
      numberOfColumns: 0,
      spacing: 0,
      heightForCard: 0,
    };
  },
  methods: {
    setUpPokeList() {
      for (let i = 1; i <= 64; i++) {
        this.pokeList.push({ img: i + ".png" });
      }
    },
    randomItem(items) {
      return items[Math.floor(Math.random() * items.length)];
    },
    randomItemIndex(items) {
      return Math.floor(Math.random() * items.length);
    },
    removeItem(pokes, item) {
      return pokes.filter((poke) => poke.img !== item.img);
    },
    randomPokeList(number) {
      this.setUpPokeList();
      const newPokes = [];
      let pokes = [...this.pokeList];
      for (let i = 0; i < number; i++) {
        var item = this.randomItem(pokes);
        pokes = this.removeItem(pokes, item);
        newPokes.push(item);
        newPokes.push(item);
      }
      return newPokes;
    },
    doubleRandomPokeList() {
      let doublePokes = [...this.pokeListLevel];
      const newDouble = [];
      while (doublePokes.length > 0) {
        let itemIndex = this.randomItemIndex(doublePokes);
        newDouble.push(doublePokes[itemIndex]);
        doublePokes.splice(itemIndex, 1);
      }
      return newDouble;
    },
    onClickLevel(cards) {
      this.numberOfCards = cards;
      this.pokeListLevel = this.randomPokeList(this.numberOfCards);
      this.doublePokeList = this.doubleRandomPokeList();
    },
  },
  computed: {
    cssVars() {
      switch (this.numberOfCards) {
        case 2:
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.numberOfColumns = 2;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.spacing = 100;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.heightForCard = 100;
          break;
        case 8:
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.numberOfColumns = 4;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.spacing = 60;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.heightForCard = 187;
          break;
        case 18:
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.numberOfColumns = 6;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.spacing = 60;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.heightForCard = 132;
          break;
        case 32:
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.numberOfColumns = 8;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.spacing = 42;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.heightForCard = 97;
          break;
        case 50:
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.numberOfColumns = 10;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.spacing = 34;
          // eslint-disable-next-line vue/no-side-effects-in-computed-properties
          this.heightForCard = 78;
          break;
      }
      return {
        "--columns": this.numberOfColumns,
        "--spacing": this.spacing + "px",
        "--height-for-card": this.heightForCard + "px",
      };
    },
  },
};
</script>
<style lang="css">
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 15%;
}
.heading {
  font-size: 50px;
  padding: 25px;
}
.pokes {
  --spacing: 40px;
  --columns: 4;
  --height-for-card: 20px;
  display: flex;
  flex-wrap: wrap;
  margin-left: calc(-1 * var(--spacing));
}
h3 {
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
