<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
  <h1>{{ title }}</h1>

  <Teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#">More info</a>
      </template>
      <h1>{{ title }}</h1>
      <p>{{ text }}</p>
    </Modal>
  </Teleport>

  <Teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:inputFields>
        <input type="text" ref="bookTitle" placeholder="Book Title">
        <input type="text" ref="bookAuthor" placeholder="Author of book">
        <button>Submit</button>
      </template>
      <h1>Create Book</h1>
      <!-- <p>{{ text }}</p> -->
    </Modal>
  </Teleport>
  <button @click="toggleModal">Open Modal</button>
  <button @click="toggleModalTwo">Open Modal Two</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
  import Modal from './components/Modal.vue'

  export default defineComponent({
    name: "App",
    components: {Modal},
    data() {
      return {
        title: "My First Vue App",
        header: "Sign up for the giveaway",
        text: "Grab your ninja swag half price!",
        showModal: false,
        showModalTwo: false,
      }
    },
    methods: {
      toggleModal() {
        this.showModal = !this.showModal
      },
      toggleModalTwo() {
        this.showModalTwo = !this.showModalTwo
      }
    },
  })
</script>

<style lang="scss">
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
