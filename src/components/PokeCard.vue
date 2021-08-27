<template>
  <div class="poke-card">
    <div
      class="card__inner"
      :class="{ 'is-flipped': isFlipped }"
      @click="onToggleFlipCard"
    >
      <div class="card__face card__face--front">
        <div class="card__content"></div>
      </div>
      <div class="card__face card__face--back">
        <div
          class="card__content"
          :style="{
            backgroundImage: `url('${require('../assets/images/' + imgUrl)}')`,
          }"
        ></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    imgUrl: {
      type: String,
      require: true,
    },
    content: {
      type: String,
      require: true,
    },
  },
  data() {
    return {
      isFlipped: false,
    };
  },
  methods: {
    onToggleFlipCard() {
      this.isFlipped = !this.isFlipped;
    },
    onFlipBackCard() {
      this.isFlipped = false;
    },
  },
};
</script>
<style scoped lang="css">
.poke-card {
  border-radius: 20px;
  width: calc(calc(100% / var(--columns)) - var(--spacing));
  height: var(--height-for-card);
  margin-left: var(--spacing);
  margin-bottom: var(--spacing);
  display: flex;
}
.card__inner {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}
.card__inner.is-flipped {
  transform: rotateY(-180deg);
}
.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 1rem;
  padding: 1rem;
  box-shadow: 0 3px 18px 3px rgba(0, 0, 0, 0.2);
}
.card__face--front .card__content {
  background: url("../assets/images/icon_back.png") no-repeat center center;
  height: 100%;
  width: 100%;
  background-size: cover;
}
.card__face--back {
  background-color: #fff;
  transform: rotateY(-180deg);
  margin-left: -2.2rem;
}
.card__face--back .card__content {
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  height: 100%;
  width: 100%;
}

.poke-card img {
  width: 100%;
}
</style>
