<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";

export default {
  components: {
    AppHeader,
    CardsList,
  },
  data() {
    return {
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
};
</script>

<template>
  <div class="test">
    <AppHeader />
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