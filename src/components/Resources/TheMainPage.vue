<template>
  <div>
    <h3>TheMainPage.vue {{ api }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      api: process.env.VUE_APP_api,
    };
  },
};
</script>

<style lang="scss" scoped></style>
