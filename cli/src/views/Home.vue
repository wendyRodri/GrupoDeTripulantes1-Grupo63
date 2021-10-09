<template>
  <div class="home">
    <img alt="SISGO" src="../assets/SISO.jpeg">
    <HelloWorld msg="Sistema Industrial de Salud y Seguridad Ocupacional"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
