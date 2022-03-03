<template>
  <div>PAGINATION</div>
  <h3>{{ pageItems }}</h3>
  <div>
    <base-button buttonTitle="Back" />
    <base-button buttonTitle="Forth" />
  </div>
</template>

<script>
import BaseButton from './UI/BaseButton.vue';
export default {
  components: { BaseButton },
  props: ['pageItems'],
  methods: {
    paginationCounter() {},
  },
};
</script>

<style lang="scss" scoped></style>
