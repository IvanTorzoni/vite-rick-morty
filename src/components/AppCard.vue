<script>
export default {
  props: {
    cardObj: Object,
  },
};
</script>

<template>

    <img :src="cardObj.image" alt="" class="rounded-circle p-2"/>
    <div class="infos">
      <h4>{{ cardObj.name }}</h4>
      <p>{{ cardObj.species }}</p>
      <p> {{ cardObj.status }}</p>
    </div>

</template>

<style lang="scss" scoped>
.infos {
  & h4{
    font-size: 30px;
  }

  & p {
    font-size: 20px;
  }
}

</style>