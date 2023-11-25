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
      <Modal theme="sale" @close="toggleModal">
          <h1>{{ header }}</h1>
          <p>{{ text }}</p>
      </Modal>
    </div>
    <button v-show="!showModal" @click.alt="toggleModal">Open modal (alt)</button>
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
        header: "SPA Foundation & Other Donors",
        text: "Grab your monthly free data!",
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
