<template>
<div class="container">
  <form class="card" @submit.prevent="createUser">
   <h2>CRUD application </h2>
   <div class="form-control">
     <label for="name">Enter your name</label>
     <input type="text" id="name" placeholder="Your name" v-model.trim="name">
   </div>

   <button :disabled="name.length === 0" class="btn">Create user</button>
  </form>
  <user-list :user="user" @loadUser="loadUser" @remove="remove"/>
</div>
</template>

<script>
import userList from '@/components/userList.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    userList
  },
  data() {
    return {
      name:'',
      user: []
    }
  },
  methods:{
    async createUser(){
    
    const response = await fetch( 'https://crudd-app-hakimov-default-rtdb.firebaseio.com/users.json', {
       method:'POST',
       headers:{'Content-Type': 'application/json'},
       body: JSON.stringify({
         firstName: this.name
       })
     })

     const firebaseData = await response.json()
     this.name = ''
    },

   async loadUser(){
      const {data} = await axios.get('https://crudd-app-hakimov-default-rtdb.firebaseio.com/users.json')
      const result = Object.keys(data).map( index =>{
        return {
          id: index,
          firstName: data[index].firstName
        }
      })
      this.user = result
      },

     async remove(id){
       await 
      }
  }
}
</script>

