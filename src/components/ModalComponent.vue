<template>
  <Teleport to="#app">
    <div class="modal-block" :style="styleProp" :class="{'fullscreen': fullscreen}">
      <div v-if="title" class="modal-header">
        {{ title }}
        <button @click="close">X</button>
      </div>
      <div v-if="$slots.default" class="modal-body">
        <slot name="default"></slot>
      </div>
      <div v-if="$slots.footer" class="modal-footer">
        <slot name="footer"/>
      </div>
    </div>
  </Teleport>

</template>

<script>
export default {
  name: "ModalComponent",
  props: {
    title: {
      type: String,
    },
    maxHeight: {
      type: String,
      default: () => "70vh",
    },
    maxWidth: {
      type: String,
      default: () => "70vw",
    },
    minHeight: {
      type: String,
      default: () => "30vh",
    },
    minWidth: {
      type: String,
      default: () => "30vw",
    },
    fullscreen: Boolean,
    close: Function
  },
  computed: {
    styleProp() {
      return this.fullscreen ? {} : {
        maxHeight: this.maxHeight,
        maxWidth: this.maxWidth,
        minHeight: this.minHeight,
        minWidth: this.minWidth,
        height: "100%",
        width: "100%",
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
:root {
    --border-settings: black solid thin;
}

.modal-block {
    display: flex;
    flex-direction: column;
    position: absolute;
    background: orange;
    border-radius: 10px;
    border: var(--border-settings);
    border-width: medium;
    color: black;

}

.modal-block.fullscreen {
    border-radius: 0;
    height: 99%;
    width: 99%;
    max-height: 99vh;
    max-width: 99vw;
}

.modal-header, .modal-body, .modal-footer {
    padding: 0.3rem;
}

.modal-header {
    background: red;
    border-bottom: var(--border-settings);
    position: relative;
}
.modal-footer {
    background: green;
    border-top: var(--border-settings);
}

.modal-body {
    flex: 1 1 auto;
    overflow-y: auto;
    min-height: 0;
}
</style>
