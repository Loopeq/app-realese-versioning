<script setup lang="ts">
import { ref, onMounted } from 'vue'

const version = ref<string>('')

const getVersion = async() => { 
  const res = await fetch('http://localhost:8000/v1/version')
  version.value = await res.json()
}

onMounted(async () => { 
  await getVersion()
})

</script>

<template>
  <div class="container">
    <div class="containter__version">
      <div>{{ version }}</div>
      <button @click="getVersion">Get version</button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container{
  width: 100%;
  height: 100%;

  &__version{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}



</style>
