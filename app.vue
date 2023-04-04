<script setup>
const user = useSupabaseUser()

onMounted(()=>{
  console.log(user)
})
</script>
<template>
  <div>
    <NuxtPage />
  </div>
</template>
