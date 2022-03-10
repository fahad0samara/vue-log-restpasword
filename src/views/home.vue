<template>
    <div>this home

    </div>
    <button @click="switchthem">dark mode</button>
</template>
<script setup>
import { useColorMode } from '@vueuse/core'

const mode = useColorMode()
const switchthem = () => {
    mode.value=mode.value=== 'dark' ? 'light' : 'dark'
}


</script>
<style >
.dark{
    background-color:rgb(10, 10, 10);
    color:#fff;
}
</style>