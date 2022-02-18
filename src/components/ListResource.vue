<template>
  <div>
    <ul v-for="result in results" :key="result">
      <li>
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
</template>

<script>
export default { props: ['results'] };
</script>

<style lang="scss" scoped></style>
