<template>
  <div>
    <div class="element-box">
      <div class="inbut-border-box">
        <div class="icon__search">
          <img class="icon-search" src="../assets/images/visor.png" alt="" />
        </div>
        <select-option
          v-for="(loca, index) in listSelectItem"
          :key="index"
          :item="loca"
          @handleItemRemove="onRemoveSelect($event)"
        />
        <div class="input__container">
          <!-- oninput="this.size = this.value.length" -->
          <input
            type="text"
            v-model="input"
            placeholder="nhập tên thành phố để tìm kiếm"
          />
        </div>
      </div>
      <list-search-option
        v-if="input !== '' && listItem.length > 0"
        :listItem="listItem"
        @handleItem="onSelectOption($event)"
      />
      <div v-else-if="input !== '' && listItem.length == 0" class="not-found">
        <p>Không có kết quả</p>
      </div>
    </div>
  </div>
</template>

<script>
// import Visor from '@/assets/images/visor.png';
import axios from 'axios';
import SelectOption from './SelectOption.vue';
import ListSearchOption from './ListSearchOption.vue';

const BASE_API_URL = 'https://provinces.open-api.vn/api';
export default {
  name: 'HelloWorld',
  data() {
    return {
      input: '',
      listItem: [],
      listSelectItem: [],
    };
  },
  components: {
    SelectOption,
    ListSearchOption,
  },
  methods: {
    onSelectOption(item) {
      if (this.listSelectItem.includes(item.item)) {
        console.log('not add');
      } else {
        this.listSelectItem.push(item.item);
      }
    },
    onRemoveSelect(config) {
      const newArray = this.listSelectItem.filter(function (ele) {
        console.log(ele, config.item);
        return ele !== config.item;
      });
      this.listSelectItem = newArray;
    },
  },
  watch: {
    input(newValue) {
      axios
        .get(`${BASE_API_URL}/d/search/?q=${newValue}`)
        .then((response) => {
          this.listItem = response.data;
          console.log(this.listItem);
        })
        .catch(function (err) {
          console.log('err', err);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.element-box {
  /* margin: 40px 25px;
  max-width: 400px;
  border: 1px solid black; 
  */
  min-width: 400px;
  margin: 40px 25px;
  position: relative;
  width: max-content;
}

.inbut-border-box {
  padding: 14px 10px;
  display: flex;
  flex-wrap: wrap;
  max-width: 400px;
  border: 1px solid black;
  overflow: hidden;
  column-gap: 5px;
  row-gap: 5px;
}
.inbut-border-box .icon__search {
  display: flex;
  align-items: center;
  padding: 0 10px;
}

.input__container {
  max-width: 400px;
  /* position: relative; */
}

.input__container input {
  font-weight: 400;
  height: 100%;
  font-size: 14px;
  line-height: 20px;
  border: none;
  width: 115%;
}
.input__container input:focus {
  outline: none;
}

.not-found {
  position: absolute;
  top: 110%;
  width: 100%;
  border-radius: 4px;
  filter: drop-shadow(0px 1px 8px rgba(102, 102, 102, 0.25));
}

.not-found p {
  background-color: white;
  padding: 8px 10px;
  font-weight: 400;
  font-size: 16px;
  line-height: 23px;
}
</style>
