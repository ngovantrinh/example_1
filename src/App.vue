<template>
  <div id="app">
    <HelloWorld @getLocationByText="getLocation($event)" />
  </div>
</template>

<script>
// import axios from 'axios';
// import  from './constants/constant'
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
};
</script>
