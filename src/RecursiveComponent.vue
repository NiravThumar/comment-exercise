<!-- components/RecursiveComponent.vue -->
<template>
  <!-- <ul> -->
    <div class="main" v-for="comment in comments" :key="comment._id">

      <!-- <details>
        <summary>
          <div> <img v-bind:src="comment.picture" class="profile" v-bind:alt="comment.picture"> <div class="inBlock" :class="{active: comment.isActive, notActive:!comment.isActive}"></div></div>
          {{ comment.auther }}</summary>
        <p>{{ comment.comment }}</p>
      </details> -->

      <div class="display" @click="toggle(comment._id)" >

        <div class="profile-block">
            <div class="profile"><img v-bind:src="comment.picture"  v-bind:alt="comment.picture"></div>
            <div class="inBlock" :class="{active: comment.isActive, notActive:!comment.isActive}"></div>
        </div>

        <div class="content">
          <h2>{{ comment.auther }} </h2>
          <p class="comment">{{ comment.comment }}</p>
        </div>

      </div>



      <div v-if="state_ref[comment._id]">
        <RecursiveComponent v-if="comment.comments" :comments="comment.comments" />
      </div>
    </div>
</template>

<script setup>

import {ref} from 'vue'
let props = defineProps(['comments'])
let state = {};


props.comments.forEach((item)=>{
    state[item._id] = true;

})
const state_ref = ref(state);

function toggle(_id){
    state_ref.value[_id] = !state_ref.value[_id];

}
</script>

<style scoped>
.main{
    margin-left:50px;
    margin-top:20px;
}
.display{
  display: flex;
  flex-direction: row;
  align-items: center;
}
.active{
  width:20px;
  height:20px;
  border-radius:50%;
  background-color: green;
}
.notActive{
  width:20px;
  height:20px;
  border-radius:50%;
  background-color: red;
}
.content{
  background-color:rgba(213, 198, 198, 0.249);
  border-radius:20px;
  padding:10px 20px;
}
.inBlock{
  display: inline-block;
  position: relative;
  left:-20px;
}
.profile img{
  width: 90px;
  height:90px;
  border-radius:50%;
  margin-right:0px;

}
.profile{
  position:relative;
}
.profile-block{
  display: flex;
  padding:10px;
}
.p{
  text-align:justify;
}



</style>