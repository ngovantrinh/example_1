<template>
  <div class="list-selected">
    <div class="select__item">
      <span>{{ item }}</span>
      <img
        src="../assets/images/X.png"
        class="remove-item"
        @click="handleItemRemove(item)"
      />
    </div>
  </div>
</template>

<script>
// console.log(item);
export default {
  name: 'SelectOption',
  props: {
    item: {
      type: [String, Number, Array, Object],
    },
  },
  methods: {
    handleItemRemove(item) {
      this.$emit('handleItemRemove', { item });
    },
  },
};
</script>

<style scoped>
.remove-item {
  cursor: pointer;
  margin-left: 5px;
}

.list-selected {
  display: flex;
  align-items: center;
}

.select__item {
  background: #f0f4f8;
  border: 1px solid #dcdcdc;
  border-radius: 4px;
  padding: 4px 8px;
}
</style>
