<template>
  <div class="book-list">
    <ul v-for="result in results.slice(pageStart, pageEnd)" :key="result">
      <li class="book-list__item">
        <strong>Title:</strong>
        {{ result.title }}
        <strong>Author(s):</strong>
        <p v-for="author in result.authors" :key="author">{{ author }}</p>
        <p>
          <strong>Publisher:</strong>
          {{ result.publisher ? result.publisher : 'not available' }}
        </p>
        <strong>Description:</strong>
        {{ result.description }}<br />
      </li>
    </ul>
  </div>
  <pagination :pageItems="results.length" @emitCounter="counter" />
  COUNTER:{{ pageCounter }}
</template>

<script>
import Pagination from './Pagination.vue';
export default {
  components: { Pagination },
  props: ['results'],
  data() {
    return {
      pageStart: 0,
      pageEnd: 10,
      pageCounter: '',
      count: 0,
    };
  },
  methods: {
    counter(payloadCounter, payloadPages, payloadState) {
      if (
        payloadCounter > 0 &&
        payloadCounter <= payloadPages &&
        payloadState === 'increase'
      ) {
        this.pageStart += 10;
        this.pageEnd += 10;
        //
      } else if (
        payloadCounter > 0 &&
        payloadCounter <= payloadPages &&
        payloadState === 'decrease'
      ) {
        this.pageStart -= 10;
        this.pageEnd -= 10;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.book-list {
  &__item {
    padding: 10px 10px;
    border: solid lightgrey 1px;
    border-radius: 10px;
    background-color: white;
  }
  ul {
    list-style: none;
  }
}
</style>
