<template>
  <button @click="$emit('emitBaseButton')">{{ buttonTitle }}</button>
</template>

<script>
export default {
  props: ['buttonTitle'],
};
</script>

<style lang="scss" scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #3a0061;
  border: 1px solid #3a0061;
  cursor: pointer;
  border-radius: 5px;
  margin-right: 20px;
  color: white;
}
button:hover,
button:active {
  background-color: #270041;
  border-color: #270041;
}
.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}
.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
