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
    <teleport to=".modals" v-if="showModal">
      <Modal theme="sale" @close="toggleModal">
        <!-- named slot -->
          <template v-slot:links>
            <a href="#">How to Apply</a>
            <a href="#">Apply Now</a>
          </template>
          <!-- normal slot -->
          <h1>{{ header }}</h1>
          <p>{{ text }}</p>
      </Modal>
    </teleport>
    
    <teleport to=".modals" v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <template v-slot:modal_info>
          <h3>How to apply?</h3>
          <p>Join the group through the link displayed on the homepage and then chat in your usage objective(s).</p>
        </template>
        <h1>December Giveaway!</h1>
        <p>For God so loved the world that he gave his only begotten Son...</p>
      </Modal>
    </teleport>
    <button v-show="!showModal" @click.alt="toggleModal">Open modal (alt)</button>
    <button v-show="!showModalTwo" @click="toggleModalTwo">Open modal</button>
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
        showModalTwo: false,
      }
    },
    methods: {
      handleClick() {
        this.title = this.$refs.name.value;
      },
      toggleModal() {
        this.showModal = !this.showModal;
      },
      toggleModalTwo() {
        this.showModalTwo = !this.showModalTwo
      }
    }
  }
  </script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app, .modals {
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
