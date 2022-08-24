<template>
  <main>
    <!-- <main-screen
      v-if="statusMatch === 'default'"
      @onStart="onHandleBeforStart($event)"
    />
    <interact-screen
      v-if="statusMatch === 'match'"
      :cardsContext="setting.cardsContext"
    /> -->
    <h1>hehee</h1>
  </main>
</template>

<script>
// import { shuffled } from '../utils/array';
// import MainScreen from '../components/MainScreen.vue';
// import InteractScreen from '../components/InteractScreen.vue';

// export default {
//   data() {
//     return {
//       setting: {
//         totalOfBlocks: 0,
//         cardsContext: [],
//         startedAt: null,
//       },
//       statusMatch: 'default',
//     };
//   },
//   methods: {
//     onHandleBeforStart(config) {
//       console.log('running handle befor start, ', config);
//       this.setting.totalOfBlocks = config.totalOfBlocks;

//       const firstCards = Array.from(
//         { length: this.setting.totalOfBlocks / 2 },
//         (_, i) => i + 1
//       );
//       const secondCards = [...firstCards];

//       const cards = [...firstCards, ...secondCards];

//       this.setting.cardsContext = shuffled(shuffled(shuffled(shuffled(cards))));

//       this.setting.startedAt = new Date().getTime();
//       console.log(this.setting.cardsContext);

//       // data ready
//       this.statusMatch = 'match';
//     },
//   },
// };
//
</script>
