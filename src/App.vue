<template>
<div class="container">
<the-modal :alert="alert" @closeModal="alert = null"/>
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
import theModal from '@/components/TheModal.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    userList,
    theModal
  },
  data() {
    return {
      name:'',
      user: [],
      alert: null
    }
  },

  created(){
    this.createUser()
  },

  methods:{
    async createUser(){
    if(this.name !== ''){
       const response = await fetch( 'https://crudd-app-hakimov-default-rtdb.firebaseio.com/users.json', {
       method:'POST',
       headers:{'Content-Type': 'application/json'},
       body: JSON.stringify({
         firstName: this.name
       })
     })

     const firebaseData = await response.json()
     this.user.push({
       firstName: this.name,
       id: firebaseData.name
     })
     this.name = ''
    }
    },

   async loadUser(){
      try{
       const {data} = await axios.get('https://crudd-app-hakimov-default-rtdb.firebaseio.com/users.json') 
       
       if(data){
       this.alert = {
           title: "Wonderful!",
           text: "You can see that the data is connected correctly!",
           type: 'primary'
                    }
                }

       const result = Object.keys(data).map( key =>{
        return {
          id: key,
          firstName: data[key].firstName
        }
      })
      this.user = result
      }catch(e){
         this.alert = {
           title: "Error!",
           text: "The data could not be connected because the server is still empty or there is an error on the server, please. Add the first user!",
           type: 'danger'
         }
      }
    
      },

     async remove(id){
       await axios.delete(`https://crudd-app-hakimov-default-rtdb.firebaseio.com/users/${id}.json`)
       this.user = this.user.filter(person => person.id !== id)
      }
  }
}
</script>

