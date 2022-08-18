<template>
  <custom>
    <p>when button is clicked , the elements of list will be appended to listRef</p>
    <button @click="doTest">Component Test</button>
    <div :key="index" v-for="(item, index) in list" :ref="listRef.set">{{item}}</div>
  </custom>
</template>

<script lang="ts" setup>
import {useTemplateRefsList} from "@vueuse/core"
import {nextTick, ref} from "vue"
import Custom from "@/components/Custom.vue"
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