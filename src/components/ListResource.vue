<template>
  <div class="book-list">
    <ul v-for="result in results" :key="result">
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
  <pagination :pageItems="results.length" />
</template>

<script>
import Pagination from './Pagination.vue';
export default {
  components: { Pagination },
  props: ['results'],
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
