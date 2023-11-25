<template>
  <div>
    <h1>{{ title }}</h1>
    <div>
      <p v-if="!showModal">Welcome...</p>
      <div v-else>
        <input type="text" ref="name">
        <button @click="handleClick">Click Me</button>
      </div>
    </div>
    <div v-show="showModal">
      <Modal :header="header" :text="text" theme="sale" :toggleClose="toggleModal"/>
    </div>
    <button v-show="!showModal" @click="toggleModal">Open modal</button>
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
        text: "Grab your ninja swag for half price!",
        showModal: false,
      }
    },
    methods: {
      handleClick() {
        this.title = this.$refs.name.value;
      },
      toggleModal() {
        this.showModal = !this.showModal;
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
