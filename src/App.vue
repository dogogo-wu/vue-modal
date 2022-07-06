<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <div v-if="showModal">
    <!-- Using Props -->
    <!-- <Modal :mtitle="header" :text="text" theme="sale" @close="toggleModal" /> -->

    <!-- Using Slot -->
    <Modal theme="" @close="toggleModal">
      <h1>Modal Title</h1>
      <p>My content</p>
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#">More info</a>
      </template>
    </Modal>
  </div>

  <teleport to=".modals" v-if="showModal2">
    <Modal theme="sale" @close="toggleModal2">
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#">More info</a>
      </template>
    </Modal>
  </teleport>
  <button @click="toggleModal">Open Modal</button>
  <button @click="toggleModal2">Open Modal2</button>
  <br /><br />
  <input type="text" ref="name" />
  <button @click="handleClick">Click me</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App!",
      showModal: false,
      showModal2: false,
      header: "Modal Title",
      text: "My content",
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
};
</script>

<style>
#app, .modals{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  display: inline-block;
  border-bottom: 3px solid #45a2ff;
  padding-bottom: 5px;
}
</style>
