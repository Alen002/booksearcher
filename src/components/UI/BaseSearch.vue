<template>
  {{ searchCaption }}:
  <input class="search-input" type="text" v-model="inputValue" />
  {{ inputValue }}
</template>

<script>
export default {
  props: ['searchCaption'],
  data() {
    return {
      inputValue: '',
    };
  },
  watch: {
    inputValue(e) {
      this.$emit('emitBaseSearch', e);
    },
  },
};
</script>

<style lang="scss" scoped>
.search-input {
  padding: 0.5rem 1.5rem;
  font-family: inherit;
  font-size: 1.2rem;
  color: black;
  border: 1px solid #3a0061;
  cursor: pointer;
  border-radius: 5px;
  margin-right: 20px;
}
</style>
