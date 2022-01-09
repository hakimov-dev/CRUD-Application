<template>
    <form class="modal card" @submit.prevent="">
   <div class="form-control">
     <h2>Edit user</h2>
     <label for="name">Edit your name</label>
     <input type="text" id="name" placeholder="Edit name" v-model="user">
   </div>

   <button class="btn primary" @click="">Edit</button>
  </form>
</template>

<script>
export default {
    name:"EditModal",
    props:['user'],
}
</script>