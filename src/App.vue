<template>
  <div>
    <div class="simple-block">
      <button @click="() => modalOpen = true">Открыть модалку</button>

      <ModalComponent title="Заголовок" :close="() => modalOpen = false" v-if="modalOpen" fullscreen>
        <ModalComponent title="Заголовок2" :close="() => modalOpen2 = false" v-if="modalOpen2">
          <ProviderList providers-count="50" v-if="true"/>
          <HelloWorld msg="Привет" v-if="false"/>
        </ModalComponent>

        <ProviderList providers-count="50" v-if="true"/>
        <HelloWorld msg="Привет" v-if="false"/>
        <template v-slot:footer>

          <button @click="() => modalOpen2 = true">Открыть модалку</button>
        </template>
      </ModalComponent>
    </div>
  </div>
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
  },
  data: () => ({
    modalOpen: false,
    modalOpen2: false,
  })
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

.simple-block {
    width: 200px;
    height: 200px;
    background: #42b983;
}
</style>
