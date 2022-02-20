<template>
  <div class="card alert" v-if="alert" :class="alert.type">
    <h2>{{ alert.title }}</h2>
    <p>{{ alert.text }}</p>
    <button class="btn" :class="alert.type" @click="$emit('closeModal')">
      Close
    </button>
  </div>
</template>

<script>
export default {
  name: "TheModal",
  props: ["alert"],
  emits: ["closeModal"],
};
</script>

<style scoped>
.alert {
  position: fixed;
  width: 73%;
  height: 200px;
  margin: 0 auto;
  z-index: 999;
  transition: 0.6s linear;
  animation-name: modal;
  animation-timing-function: linear;
  animation-duration: 0.6s;
}

@keyframes modal {
  0% {
    top: -300px;
    opacity: 0;
  }
  25% {
    top: -250px;
    opacity: 0.2;
  }
  50% {
    top: -200px;
    opacity: 0.5;
  }
  75% {
    top: -100px;
    opacity: 0.7;
  }
  100% {
    top: 0px;
    opacity: 1;
  }
}
</style>