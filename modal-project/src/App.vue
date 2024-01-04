<template>
  <h1>{{ msg }}</h1>
  <br />
  <!-- <input type="text" ref="name" />
  <button @click="handleClick">Click me</button> -->
  <!-- <div v-if="showModal">
    <Modal theme="sale" :header="header" :newName="msg" @close="toggleModal" />
  </div>
  <button @click="toggleModal">Show Modal</button> -->
  <!-- <button @click.right="toggleModal">Show Modal</button> -->

  <!-- <div v-if="showModal"> -->
  <teleport to=".modals" div v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:myLinks>
        <a href="https://google.com"> Google</a>
        <a href="https://facebook.com"> Facebook</a>
      </template>
      <h1>Hello</h1>
      <p>text</p>
    </Modal>
  </teleport>

  <div v-if="showModal2">
    <Modal @close="toggleModal2">
      <h1>Hello 2</h1>
      <p>text 2</p>
    </Modal>
  </div>

  <button @click="toggleModal">Show Modal</button>
  <button @click="toggleModal2">Show Modal2</button>
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
      header: "Hello World",
      msg: "Hello World ok msg",
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value);
      this.msg = this.$refs.name.value;
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
