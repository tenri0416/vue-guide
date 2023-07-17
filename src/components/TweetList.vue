<script setup lang="ts">
import {ref,defineEmits} from 'vue'
import { defineProps } from 'vue';

type Tweet={
 id:number,
 description:string,
}

type Props={
  tweets:Tweet[]
}

const emit=defineEmits(['delete-tweet']);
const deleteTweet=(id:number)=>{
 emit('delete-tweet',id)
}

defineProps<Props>()
</script>
<template>
 
          <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
            <span class="tweet-list">{{ tweet.description }}</span>
            <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
          </li>
       
</template>
<style>
.tweet-list{
  list-style:none;
  margin-bottom:12px;
  border-radius:4px;
  font-size:20px;
  display:flex;
  background-color:rgb(204,219,233);
  padding: 8px 20px;

}
.delete-button{
  color:fff;
  font-weight:bold;
  background-color:#c99a68;
  border-radius:2px;
  border:none;
  width:60px;
  height:22px;
}
.delete-button:hover{
  background-color:#ac783f;
}
</style>
