<template>
    <form class="modal card" @submit.prevent="">
   <div class="form-control">
     <label for="name">Edit your name</label>
     <input type="text" id="name" placeholder="Edit name" v-model.trim="name">
   </div>

   <button class="btn">Edit</button>
  </form>
</template>