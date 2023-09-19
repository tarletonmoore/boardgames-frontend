<template>
  <div class="home">
    <h1>All boardgames</h1>
    <div v-for="boardgame in boardgames">
      <h2>{{ boardgame.name }}</h2>
      <!-- <img v-bind:src="photo.url" v-bind:alt="photo.name" /> -->
      <p>Price: {{ boardgame.price }}</p>
      <p>Number of Players: {{ boardgame.player }}</p>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      boardgames: [],
    };
  },
  created: function() {
    this.indexBoardgames();
  },
  methods: {
    indexBoardgames: function() {
      axios.get("/boardgames").then(response => {
        console.log("boardgames index", response);
        this.boardgames = response.data;
      });
    },
  },
};
</script>
