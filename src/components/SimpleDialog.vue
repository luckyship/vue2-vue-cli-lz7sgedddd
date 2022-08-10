<template>
  <div class="shade" v-if="visible" @click="clickShade()">
    <div :style="{ width: width }" class="dialog" @click.stop>
      <div class="title">
        <slot name="title">{{ title }}</slot>

        <span class="close" @click="close">X</span>
      </div>
      <div class="content">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SimpleDialog',
  props: {
    width: {
      type: String,
      default: '50%',
    },
    title: {
      type: String,
      default: '',
    },
    visible: {
      type: Boolean,
      default: false,
    },
  },
  watch: {
    visible(newVal, oldVa) {
      if (oldVa === false && newVal === true) {
        // this.$emit('update:visible', true)
        this.$emit('open')
      }
    },
  },
  methods: {
    close() {
      this.$emit('update:visible', false)
      this.$emit('close')
    },
    clickShade() {
      this.close()
    },
  },
}
</script>

<style scoped>
.shade {
  left: 0;
  top: 0;
  background: rgba(0, 0, 0, 0.2);
  width: 100%;
  height: 100%;
  position: absolute;
  display: flex;
  justify-content: center;
}

.dialog {
  align-self: center;
  position: relative;
  border: 1px solid black;
  display: inline-block;
}

.title {
  border: 1px solid black;
}

.close {
  position: absolute;
  top: 0;
  right: 5px;
  cursor: pointer;
}
</style>
