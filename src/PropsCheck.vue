<template>
    {{name}}
</template>

<script setup>

 import {ref,reactive,computed} from 'vue'

const props = defineProps(['name']);

// let name = 'sagar'
let name = ref('vivek')

console.log(props.name);
</script>

<style scoped>

</style>