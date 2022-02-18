<template>
  <div class="test">
    <base-search search-caption="Search" @emitBaseSearch="enteredData" />
    <base-button @emitBaseButton="getData" button-title="Get Data" />
    <base-button @emitBaseButton="clearData" button-title="Clear" />
    <list-resource :results="results" />
  </div>
</template>

<script>
import testObject from '../assets/test.js';

import axios from 'axios';
import BaseButton from '../components/UI/BaseButton.vue';
import BaseSearch from '../components/UI/BaseSearch.vue';
import ListResource from '../components/ListResource.vue';
export default {
  components: { BaseButton, BaseSearch, ListResource },
  data() {
    return {
      api: process.env.VUE_APP_api,
      results: '',
      endpoint: 'https://www.googleapis.com/books/v1/volumes',
      queryField: '',
      jsonFile: testObject,
    };
  },
  methods: {
    enteredData(e) {
      this.queryField = e;
    },
    destructureData(payload) {
      const { items } = payload;
      this.results = items.map(
        ({ volumeInfo: { title, authors, publisher, description } }) => ({
          title,
          authors,
          publisher,
          description,
        })
      );
      console.log('thisresults___', this.results);
    },

    getData() {
      axios
        .get(
          `${this.endpoint}?q=${this.queryField}&maxResults=30&keyes&key=${this.api}`
        )
        .then((res) => res.data)
        .then((data) => {
          this.destructureData(data);
        });
    },
    clearData() {
      this.results = '';
    },
  },
};
</script>

<style lang="scss" scoped>
.test {
  background-color: red;
  min-width: 300px;
  /* width: 50%; */
}
</style>
