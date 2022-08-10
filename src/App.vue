<template>
  <div id="app">
    <button @click="openDialog">click</button>
    <simple-dialog :width="'30%'" title="dialog title" @close="close" @open="onOpen" :visible.sync="visible">
      <div slot="title">new title</div>
      <div>
        <p>dddd</p>
        <p>dddd</p>
        <p>dddd</p>
        <p>dddd</p>
        <p>dddd</p>
        <p>dddd</p>
      </div>
    </simple-dialog>
  </div>
</template>

<script>
import SimpleDialog from './components/SimpleDialog.vue'

export default {
  name: 'App',
  components: {
    SimpleDialog,
  },
  data() {
    return {
      visible: false,
    }
  },

  methods: {
    close() {
      console.log('close')
    },
    onOpen() {
      console.log('open')
    },
    openDialog() {
      this.visible = true
      console.log(111)
    },
  },
}
</script>

<style></style>
