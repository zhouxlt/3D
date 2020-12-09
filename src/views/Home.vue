<template>
  <div class="home">
    <ThreeExample msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import ThreeExample from '@/components/ThreeExample.vue'

export default {
  name: 'Home',
  components: {
    ThreeExample
  }
}
</script>
