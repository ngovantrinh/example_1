<template>
  <div>
    <h1>Interact Component</h1>
    <card-flip
      v-for="(card, index) in cardsContext"
      :key="index"
      :imgBackFaceUrl="`images/${card}.png`"
      :ref="`card-${index}`"
      :card="{ index, value: card }"
      @onFlip="checkRule($event)"
    />
  </div>
</template>

<script>
import CardFlip from './Card.vue';
export default {
  props: {
    cardsContext: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  components: {
    CardFlip,
  },
  data() {
    return {
      rules: [],
    };
  },
  methods: {
    checkRule(card) {
      if (this.rules.length === 2) return false;
      this.rules.push(card);
      console.log(this.rules);

      if (
        this.rules.length === 2 &&
        this.rules[0].value === this.rules[1].value
      ) {
        console.log('Right...');
      } else if (
        this.rules.length === 2 &&
        this.rules[0].value !== this.rules[1].value
      ) {
        console.log('Wrong...');
        // close two card
        // console.log(this.$$refs[`card-1`]);
        this.$refs[`card-${this.rules[0].index}`].onFilipBackCard();
        this.$refs[`card-${this.rules[1].index}`].onFilipBackCard();
        // reset rulse to []
        this.rules = [];
      } else return false;
    },
  },
};
</script>
