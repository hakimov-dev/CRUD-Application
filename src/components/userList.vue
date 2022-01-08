<template>
  <div class="card">
      <h3></h3>
  </div>
    <div class="card center">
    <h4>There are no user yet</h4>
    <button class="btn primary">Load people</button>
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