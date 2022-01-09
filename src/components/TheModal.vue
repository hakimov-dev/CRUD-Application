<template>
  <div class="alert" v-if="alert" :class="alert.type">
   <h2>{{alert.title}}</h2>
   <p>{{alert.text}}</p>
   <button class="btn" :class="alert.type">Close</button>
  </div>
</template>

<script>
export default {
  name:"TheModal"
}
</script>

<style scoped>

</style>