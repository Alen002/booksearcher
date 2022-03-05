<template>
  <div>PAGINATION</div>
  <h3>{{ pageItems }}</h3>
  <div class="pagination-layout">
    <base-button
      buttonTitle="Back"
      @emitBaseButton="paginateCounter('decrease')"
    />
    <h2>{{ counter }}</h2>
    <base-button
      buttonTitle="Forth"
      @emitBaseButton="paginateCounter('increase')"
    />
  </div>
</template>

<script>
import BaseButton from './UI/BaseButton.vue';
export default {
  data() {
    return { counter: 0 };
  },
  components: { BaseButton },
  props: ['pageItems'],
  methods: {
    paginateCounter(clicked) {
      let pages = Number.isInteger(this.pageItems / 10)
        ? this.pageItems / 10
        : Math.trunc(this.pageItems / 10) + 1;

      console.log(pages);
      if (clicked === 'increase' && pages > 0 && this.counter < pages) {
        this.counter += 1;
      } else if (clicked === 'decrease' && this.counter > 0) {
        this.counter -= 1;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.pagination-layout {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  width: 20%;
  background-color: red;
}

h2 {
  background-color: green;
}
</style>
