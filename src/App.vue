<template>
<div class="flex">
<Hits /> 
<HrStats />
</div>
</template>

<script>
import HrStats from './components/HrStats.vue'
import Hits from './components/Hits.vue'

export default {
  name: 'App',
    components: {
      HrStats,
      Hits
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.flex{
  display:flex;
  width: 960px;
  margin-left:auto;
  margin-right:auto;
}
</style>
