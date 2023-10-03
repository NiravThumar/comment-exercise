<template>
<!-- main exercise -->
  <!-- <RecursiveComponent :comments='comments' /> -->

  <!-- props exercise -->
  <h1>hello</h1>
  <PropsCheck :name="name" />

  <!-- watcher exercise -->
  <Watcher />
</template>

<script setup>

import { reactive ,ref} from 'vue'
import RecursiveComponent from './RecursiveComponent.vue'
import PropsCheck from './PropsCheck.vue'
import Watcher from './Watcher.vue'
import data from '../comments.json'

let comments = reactive(data);

let name = ref('ajay');


</script>

