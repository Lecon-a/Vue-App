<template>
  <div>
    <h1>{{ title }}</h1>
    <input type="text" ref="name">
    <button @click="handleClick">Click Me</button>
    <Modal :header="header" :text="text" />
  </div>
</template>

  <script>

  import Modal from "./components/Modal.vue"
  
  export default {
    name: 'App',
    components: { Modal },
    data(){
      return {
        title: "My First Vue App :)",
        header: "Sign up for the Giveaway",
        text: "Grab your ninja swag for half price!"
      }
    },
    methods: {
      handleClick() {
        this.title = this.$refs.name.value
      }
    }
  }
  </script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.modal h1 {
  padding: 0 0 .5rem;
  color: #aaf;
}
</style>
