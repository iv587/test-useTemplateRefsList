<template>
  <div>
    <p>click the Html Test button, the listRef always keep changeless </p>
    <button @click="doTest">Html Test</button>
    <div :key="index"
         v-for="(item, index) in list"
         :ref="listRef.set">{{item}}</div>
  </div>
</template>

<script lang="ts" setup>
import {useTemplateRefsList} from "@vueuse/core"
import {computed, nextTick, ref} from "vue"
const listRef = useTemplateRefsList<HTMLDivElement>()
const list = ref([1,3,4,5,6])
const doTest = () => {
  list.value[2] = new Date().getTime()
  nextTick(() => {
    console.log(listRef.value)
  })
}
</script>

<style scoped>

</style>