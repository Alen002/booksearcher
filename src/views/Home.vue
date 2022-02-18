<template>
  <div>
    <base-search search-caption="Search" @emitBaseSearch="enteredData" />
    <base-button @emitBaseButton="getData" button-title="Get Data" />
    <base-button @emitBaseButton="clearData" button-title="Clear" />

    <ul v-for="result in results" :key="result">
      <li>
        <h3>Title:{{ resulttitle }}</h3>
        Authors:{{ result.authors }}<br />
        <p>Publisher {{ result.publisher }}</p>
        Description:{{ result.description }}<br />
      </li>
    </ul>
  </div>
</template>

<script>
import testObject from '../assets/test.js';

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
      console.log(this.results);
    },

    getData() {
      axios
        .get(
          `${this.endpoint}?q=${this.queryField}&maxResults=3&keyes&key=${this.api}`
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

<style lang="scss" scoped></style>
