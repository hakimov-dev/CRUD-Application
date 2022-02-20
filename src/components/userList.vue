<template>
      <div v-if="user.length !== 0">
      <div 
      class="card flex" 
      v-for="person in user" 
      :key="person.id"
      :id="person.id"
      >
      <h3>{{person.firstName}}</h3>
      <div>
      <button class="btn warning" @click="$emit('edit', person)">Edit</button>
      <button class="btn danger" @click="$emit('remove', person.id)">Delete</button>
      </div>
      </div>
      </div>

    <div class="card center" v-else>
    <h4>There are no user yet</h4>
    <button @click="$emit('loadUser')" class="btn primary">Load people</button>
    </div>
</template>

<script>
export default {
  name:"userList",
  data() {
      return {}
  },
  props:[ 
      'user'
      ],
  emits:['loadUser', 'remove', 'edit']
}
</script>

<style scoped>

.flex{
 display:flex;
 align-items:center;
 justify-content: space-between;    
}
   /* // Created by hakimov-dev; my website hakimov.netlify.app */
</style>