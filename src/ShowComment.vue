<template>
<details>
  <summary>{{comment.auther}}</summary>
  <p>{{comment.comment}}</p>
</details>
</template>

<script setup>

 import {ref,reactive,computed} from 'vue'

    let props = defineProps(['comment'])
</script>

<style scoped>

</style>