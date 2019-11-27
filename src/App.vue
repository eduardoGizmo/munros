<template>
  <div>
    <h1>Munros</h1>
    <div class="main-container">
      <munros-list :munros='allMunros'></munros-list>
      <munro-detail :munroToShow='selectedMunro'></munro-detail>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import MunrosList from './components/MunrosList.vue';
import MunroDetail from './components/MunroDetail.vue'

export default {
  name: 'app',
  data(){
    return {
      allMunros: [],
      selectedMunro: null
    };
  },
  mounted(){
    fetch('https://munroapi.herokuapp.com/munros')
    .then(res => res.json())
    .then(munros => this.allMunros = munros)

    eventBus.$on('munro-selected', (munro) => {
      // console.log('within $on', munro);
      this.selectedMunro = munro;
    })
  },
  components: {
    "munros-list": MunrosList,
    "munro-detail": MunroDetail
  }
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
