<template>
  <div class="search-bar">
    <div class="buttonWrapper">
      <CustomButton text="Add new card" color="#ffcccc" @buttonClick="AddButtonClick"/>
    </div>
    <div class="searchInputWrapper">
      <input type="text" placeholder="search" class="searchInput" v-model="searchInput"/>
      <CustomButton text="SEARCH" @buttonClick="searchButtonClick"/>
    </div>
  </div>
</template>

<script>
import CustomButton from "./CustomButton";
export default {
  data() {
    return {
      searchInput:'',
    }
  },
  components: {CustomButton},
  methods: {
    AddButtonClick() {
      this.$emit('AddButtonClick')
    },
    searchButtonClick() {
      this.$emit('searchButtonClick', this.searchInput)
    }
  }
}
</script>

<style scoped>
.search-bar {
  background: #a2a2a2;
  border-radius: 5px;
  padding: 10px 5px;
  display: flex;
  justify-content: space-between;
  margin-bottom:30px;
}
.buttonWrapper {
  margin-right: 20px;
}
.searchInput {
  height: 25px;
  padding: 5px;
  border-radius: 5px;
  outline: none;
  font-size: 16px;
  background: #7dc1da;
}
.searchInputWrapper {
  display: flex;

}
</style>
