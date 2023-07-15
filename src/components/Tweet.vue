<script setup lang="ts">
import {ref} from 'vue'
const tweets=ref([{id:'0',discription:'hell'},{id:1, discription:'no'}]);
const inputtingDescription=ref<string>();

const postTweet=()=>{

  console.log(inputtingDescription.value);
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
      <input v-model="inputtingDescription"/>
      <button class="save-button" @click="postTweet">post</button>
    </div>
    <div  class="tweet-container">
      <ul>
        <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
          <span class="tweet-list">{{ tweet.discription }}</span>
        </li>

      </ul>
    </div>
  </div>
</template>

<style >
.ok{
  color:red;
}
.save-button{
  color:blue;
width:70px;
}
.container{
  display: flex;
  flex-direction: column;
   align-items: center;
}

.tweet-list{
  list-style:none;
}
.form-container{
    display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

</style>
