<template>
  <ul class="list-search-box">
    <li
      class="option"
      @click="handleItem(item.name)"
      v-for="(item, index) in listItem"
      :key="index"
    >
      <span>{{ item.name }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'ReslutSearch',
  props: {
    listItem: {
      type: [Array, Object],
    },
  },
  methods: {
    handleItem(item) {
      this.$emit('handleItem', { item });
    },
  },
};
</script>

<style scoped>
.list-search-box {
  position: absolute;
  top: 110%;
  left: 0;
  filter: drop-shadow(0px 1px 8px rgba(102, 102, 102, 0.25));
  border-radius: 4px;
  width: 100%;
  list-style: none;
}
.list-search-box .option {
  background-color: white;
  padding: 8px 10px;
  cursor: pointer;
}
.list-search-box .option span {
  font-weight: 400;
  font-size: 16px;
  line-height: 23px;
}
.list-search-box .option:hover {
  background: #617d98;
}
.list-search-box .option:hover span {
  color: white;
}
</style>
