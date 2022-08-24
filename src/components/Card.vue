<template>
  <div class="card">
    <div
      class="card__inner"
      :class="{ 'is-flipped': isFlipped }"
      @click="onToggleFlipCard"
    >
      <div class="card__face card__face--front">
        <div class="card-content"></div>
      </div>
      <div class="card__face card__face--back">
        <div
          class="card-content"
          :style="{
            background: `url(${
              'src/assets/' + imgBackFaceUrl
            }) no-repeat center center`,
            backgroundSize: 'contain',
          }"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name="Card",
    props: {
        card: {
            type: [String, Number, Array, Object]
        },
        imgBackFaceUrl:{
            type: String,
            // required: true,
        }
    },
    data(){
        return{
            isFlipped: false,
        };
    },
    methods:{
        onToggleFlipCard(){
            this.isFlipped = !this.isFlipped;
            if(this.isFlipped) this.$emit("onFlip", this.card);
        },
        onFilipBackCard() {
            this.isFlipped = false;
        }
    }
}
</script>

<style lang="css" scoped>
.card {
  height: 120px;
  width: 90px;
  display: inline-block;
  margin: 0 1rem 1rem 0;
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
  box-shadow: 0 3px 10px 3px rgba(0, 0, 0, 0.3);
}

.card__face--front .card-content {
  background: url('../assets/images/icon_back.png') no-repeat center center;
  background-size: 40px 40px;

  height: 100%;
  width: 100%;
}

.card__face--back {
  background-color: var(--light);
  transform: rotateY(-180deg);
}
.card__face--back .card-content {
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  width: 100%;
  height: 100%;
}
</style>
>
