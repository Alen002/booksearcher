<template>
  <div>
    <base-search search-caption="Search" @emitBaseSearch="enteredData" />
    <base-button @emitBaseButton="getData" button-title="Get Data" />
    <base-button @emitBaseButton="clearData" button-title="Clear" />

    <ul v-for="result in results" :key="result">
      <li>
        <h3>Title:{{ result.volumeInfo.title }}</h3>
        Authors:{{ result.volumeInfo.authors }}<br />
        <p>Publisher {{ result.volumeInfo.publisher }}</p>
        Description:{{ result.volumeInfo.description }}<br />
      </li>
    </ul>
    <h1>Check Results</h1>
    <button @click="testing">TESTING</button>
    <!--  <pre>{{ testingResults }}</pre> -->
    <h3>REST</h3>
    <pre>{{ rest }}</pre>
    <h3>ITEMS</h3>
    <pre>{{ items }}</pre>
  </div>
</template>

<script>
import test from '../assets/test.js';
import axios from 'axios';
import BaseButton from '../components/UI/BaseButton.vue';
import BaseSearch from '../components/UI/BaseSearch.vue';
export default {
  components: { BaseButton, BaseSearch },
  data() {
    return {
      api: process.env.VUE_APP_api,
      /* results: [{ test: 121 }, { test: 45454545454 }], */
      results: '',
      endpoint: 'https://www.googleapis.com/books/v1/volumes',
      queryField: '',
      jsonFile: test,
      testingResults: '',
      items: '',
      rest: '',
    };
  },
  methods: {
    testing() {
      /* this.testingResults = this.jsonFile.test.items.map((e) => e); */
      const { items } = this.jsonFile.test;
      this.testingResults = { ...this.jsonFile.test };
      // How to manipulate data
      this.items = items;
    },
    enteredData(e) {
      this.queryField = e;
    },
    getData() {
      console.log('Start fetching___');
      axios
        .get(
          `${this.endpoint}?q=${this.queryField}&maxResults=30&keyes&key=${this.api}`
        )
        .then((res) => res.data)
        /* .then((data) => (this.results = data)); */
        .then((data) => {
          this.results = data.items;
        });
    },
    clearData() {
      this.results = '';
    },
  },
};
</script>

<style lang="scss" scoped></style>
