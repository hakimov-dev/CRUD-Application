<template>
  <div class="card" :v-for="peson in user" :key="person">
      <h3>{{person}}</h3>
  </div>
    <div class="card center">
    <h4>There are no user yet</h4>
    <button @click="load" class="btn primary">Load people</button>
  </div>
</template>

<script>
export default {
  name:"userList",
  data() {
      return {
          
      }
  },
  methods:{},
  props:{
      user:{
          type: Array,
          required: true
      }
  },
  emits:{}
}
</script>