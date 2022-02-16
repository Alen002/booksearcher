<template>
  <div>
    <h3>Home</h3>
    <button @click="getData">AXIOS</button>
    <base-button />
    <pre>{{ results }}</pre>
  </div>
</template>

<script>
import axios from 'axios';
import BaseButton from '../components/UI/BaseButton.vue';
export default {
  components: { BaseButton },
  data() {
    return {
      api: process.env.VUE_APP_api,
      results: null,
    };
  },
  methods: {
    getData() {
      console.log('Start fetching___');
      axios
        .get(
          `https://www.googleapis.com/books/v1/volumes?q=bradbury+inauthor:keyes&key=${this.api}`
        )
        .then((res) => res.data)
        .then((data) => (this.results = data));
    },
  },
};
</script>

<style lang="scss" scoped></style>
