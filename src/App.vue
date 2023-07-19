<template>
  <div id="app">
    <InputComponent /> <SignComponent /> <InputComponent /> <SignComponent /> <InputComponent /> <EqualComponent />
    <hr>
    <OutputComponent />
  </div>
</template>

<script>
import InputComponent from "@/components/InputComponent.vue";
import SignComponent from "@/components/SignComponent.vue";
import OutputComponent from "@/components/OutputComponent.vue";
import EqualComponent from "@/components/EqualComponent.vue";

export default {
  name: 'App',
  components: {
    InputComponent,
    SignComponent,
    OutputComponent,
    EqualComponent
  }
}
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
</style>
