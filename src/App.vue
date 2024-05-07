<script>
import { store } from "./store";
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";
import AppSearch from "./components/AppSearch.vue";

export default {
  components: {
    AppHeader,
    CardsList,
    AppSearch
  },
  data() {
    return {
      store,
      cardsArray: [],
    };
  },
  created() {
    axios
      .get("https://rickandmortyapi.com/api/character")
      .then((resp) => {
        console.log(resp);
        this.cardsArray = resp.data.results;
      });
  },
  methods: {
    getStatus() {
      console.log("Get Status", this.store.selectedStatus);

      if (this.store.selectedStatus !== "All") {
        axios
        .get("https://rickandmortyapi.com/api/character", {
          params: {
            status: this.store.selectedStatus
          }
        })
        .then((resp) => {
          this.cardsArray = resp.data.results;
        })
      } else {
        axios
        .get("https://rickandmortyapi.com/api/character")
        .then((resp) => {
          this.cardsArray = resp.data.results;
        })
      }
    }
  }
};
</script>

<template>
  <div class="test">
    <AppHeader />
    <AppSearch @filter="getStatus" />
    <CardsList :cardsArray="cardsArray" />
  </div>
</template>

<style lang="scss" scoped>
.test {
  background-image: url("https://upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Rick_and_Morty.svg/2560px-Rick_and_Morty.svg.png");
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
}
</style>