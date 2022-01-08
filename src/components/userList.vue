<template>
      <div v-if="user.length !== 0">
      <div 
      class="card" 
      v-for="person in user" 
      :key="person.id"
      >
      <h3>{{person.firstName}}</h3>
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
  emits:['loadUser']
}
</script>