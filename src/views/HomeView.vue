<template>
  <div class="home">
    <div>
      <input type="text" ref="name">
      <button type="submit" @click="handleClick">click me</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HomeView',
  data() {
    return {}
  },
  methods: {
    handleClick() {
      let inputField = this.$refs.name as HTMLInputElement
      console.log(inputField.value);
      inputField.classList.add("active")
      inputField.value = " "
      inputField.focus()
      
    }
  }
});
</script>

<style scoped lang="scss">
  h1 {
    border-bottom: 1px solid #ddd;
    display: inline-block;
    padding-bottom: 10px;
  }
</style>