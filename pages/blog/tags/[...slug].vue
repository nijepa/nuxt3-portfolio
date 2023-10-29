<script setup>
const { path } = useRoute()

const { data } = await useAsyncData(`content-${path}`, () => {
  return queryContent()
    .where({ _path: path })
    .findOne()
})
console.log(9, path)
</script>

<template>
  <ContentRenderer :value="data" class="prose my-10 mx-auto max-w-7xl">
    <template #empty>
        <p>No content found.</p>
      </template>
  </ContentRenderer>
</template>