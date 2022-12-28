<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/gambar34.jpeg">
    <HelloWorld msg="Muhammaad badri"/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>
<style>
  img{
    width: 220px;
    height: 220px;
    display: inline-block;
  }
</style>
