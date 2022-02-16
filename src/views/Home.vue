<template>
  <div>
    <base-search search-caption="Search" @enteredData="enteredData" />

    <base-button @emitBaseButton="getData" button-title="Get Data" />
    <base-button @emitBaseButton="clearData" button-title="Clear" />
    <pre>{{ results }}</pre>
  </div>
</template>

<script>
import axios from 'axios';
import BaseButton from '../components/UI/BaseButton.vue';
import BaseSearch from '../components/UI/BaseSearch.vue';
export default {
  components: { BaseButton, BaseSearch },
  data() {
    return {
      api: process.env.VUE_APP_api,
      results: '',
      endpoint: 'https://www.googleapis.com/books/v1/volumes',
      queryField: '',
    };
  },
  methods: {
    enteredData(e) {
      this.queryField = e;
    },
    getData() {
      console.log('Start fetching___');
      axios
        .get(
          `${this.endpoint}?q=${this.queryField}&maxResults=1&keyes&key=${this.api}`
        )
        .then((res) => res.data)
        .then((data) => (this.results = data));
    },
    clearData() {
      this.results = '';
    },
  },
};
</script>

<style lang="scss" scoped></style>
