<template>
  <ModalComponent title="Заголовок" fullscreen>
    <ProviderList providers-count="50" v-if="true"/>
    <HelloWorld msg="Привет" v-if="false"/>
  </ModalComponent>
</template>

<script>
import ModalComponent from "@/components/ModalComponent";
import ProviderList from "@/components/ProviderList";
import HelloWorld from "@/components/HelloWorld";

export default {
  name: 'App',
  components: {
    ProviderList,
    ModalComponent,
    HelloWorld,
  }
}
</script>

<style>
body {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    padding: 0;
    margin: 0;
}
#app {
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
