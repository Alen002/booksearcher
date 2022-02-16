<template>
  <div>
    <h3>Home</h3>
    <button>AXIOS</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      api: process.env.VUE_APP_api,
    };
  },
  methods: {
    getData() {},
  },
};
</script>

<style lang="scss" scoped></style>
