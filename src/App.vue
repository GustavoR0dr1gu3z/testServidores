<template>

  <div id="navv">
    <Navbarr/>
    <HelloWorld/>
  </div>

</template>


<script>
// 1er Paso: Importar el componente
import Navbarr from './components/Navbarr.vue'
import HelloWorld from './components/HelloWorld.vue'

// 2do Paso: Exportar el componente
export default {
  components: {
    Navbarr,
    HelloWorld
  },
}
</script>
