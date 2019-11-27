<template lang="html">
  <div class=""  v-if="munroToShow">
    <h3>{{ munroToShow.name }}</h3>
    <p>Height: {{munroToShow.height}}</p>
    <p>Region: {{munroToShow.region}}</p>
    <p>Meaning: {{munroToShow.meaning}}</p>
  </div>
</template>

<script>
export default {
  name: 'munro-detail',
  props: ['munroToShow']
}
</script>

<style lang="css" scoped>
</style>
