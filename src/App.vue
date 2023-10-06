<script>
import Navbar from './components/Navbar.vue';
export default{
  components:{ Navbar },
}
</script>

<template>
  <div>
  <Navbar></Navbar>
  <RouterView />
  </div>

</template>

<style scoped>


</style>
