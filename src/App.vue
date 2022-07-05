<template>
  <h1>{{ title }}</h1>
  <br>
  <Modal v-if="isClick" />
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: "App",
  components:{
    Modal
  },
  data() {
    return {
      title: 'My First Vue App!',
      isClick: false
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
      this.isClick = !this.isClick;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  display: inline-block;
  border-bottom: 3px solid #45a2ff;
  padding-bottom: 5px;
}
</style>
