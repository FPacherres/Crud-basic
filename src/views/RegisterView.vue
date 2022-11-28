<template>
  <div class="register">
    <input type="text" placeholder="Buscar">
    <list />
  </div>
</template>

<script>
// @ is an alias to /src
import list from '@/components/list.vue'

export default {
  name: 'RegisterView',
  components: {
    list
  }
}
</script>

<style scoped>
.register {
    background-color: #E6EBE0;
    height: calc(100vh - 80px);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
}
</style>
