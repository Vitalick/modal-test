<template>
  <div class="provider-wrapper">
    <div class="provider-list">
      <div class="provider-item" v-for="i in range" :key="i">Провайдер {{i}}
        <select>
          <option v-for="n in 100" :key="n">{{ n }}</option>
        </select>
      </div>
    </div>
    <div class="provider-buttons">
      <button>Применить</button>
      <button>Сбросить</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProviderList",
  props: {
    providersCount: {
      type: Number,
      default: () => 10
    }
  },
  computed: {
    range() {
      let range = [];
      for (let i = 1; i <= this.providersCount; i++) {
        range.push(i)
      }
      return range
    }
  }
}
</script>

<style>
.provider-wrapper {
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 100%;
}

.provider-list {
    background: blue;
    padding: 0.3rem;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    grid-auto-rows: 100px;
    white-space: nowrap;
    flex: 1 1 auto;
    overflow-y: auto;
    min-height: 0px;
}

.provider-item {
    background: black;
    color: white;
    border-radius: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0.2rem;
}

.provider-buttons {
    flex-shrink: 1;
    background: aqua;
    display: flex;
    padding: 0.3rem;
    justify-content: center;
    align-items: center;
}

.provider-buttons > button {
    margin: 0.3rem;
}
</style>
