<template>
  <div class="catalog">
    <Header/>
    <div class="title_catalog">
      <br>
      <h1 align="center">Каталог</h1>
      <br>
    </div>
    <div class="catalog_list">
      <food
          v-for="furniture in FURNITURE"
          :key="furniture.id"
          :fur_data="furniture"
      />
    </div>
  </div>
</template>

<script>
import Food from "./Food";
import {mapActions, mapGetters} from 'vuex'
import Header from "../Header";
export default {
  name: "Catalog",
  components: {Header, Food},
  computed: {
    ...mapGetters([
      'FURNITURES',
      'BASKET',
    ]),
  },
  methods: {
    ...mapActions([
      "GET_FURNITURES_FROM_API",
      "ADD_FURNITURE_TO_BASKET"
    ]),
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API();
  }
}
</script>

<style scoped>
.title_catalog{
  background-color: #110505;
  color: white;
}
.catalog_list{
  background-image: url("../../assets/фон.jpg");
  background-repeat: no-repeat;
  width: 100%;
  background-size: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
</style>