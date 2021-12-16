<template>
  <div class="container">
    <div class="cards">
      <Card v-for="(song, i) in card" :key="i" :card="song" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "../commons/Card.vue";
export default {
  name: "Cards",
  components: {
    Card,
  },
  data() {
    return {
      card: null,
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        // handle success
        this.card = response.data.response;
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scoped>
.container {
  width: 70%;
  margin: auto;
  .cards {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
}
</style>