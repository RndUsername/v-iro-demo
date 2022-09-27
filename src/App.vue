<template>
  <div ref="wrapper"></div>
  <input type="checkbox" name="disablePicker" v-model="disable">
  <label for="disablePicker">Disable</label> <br>
  Color: {{color}}
</template>

<script setup lang="ts">
import { ref, type Ref } from 'vue';
import { useIroColorPicker } from "v-iro.js"
import type { IroColor } from '@irojs/iro-core';

const wrapper = ref()
const color = ref("")
const disable = ref(false)

const options = {
    width: 130
}

useIroColorPicker(wrapper, options, disable).then((colorPicker) => {
  colorPicker.on("color:change", (pickerColor: IroColor) => {
    color.value = pickerColor.hexString
  })
})
</script>

<style scoped>
</style>
