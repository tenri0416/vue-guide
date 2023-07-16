<script setup lang="ts">
import {ref} from 'vue'
const tweets = ref([{ id: 0, description: 'hell' }, { id: 1, description: 'no' }]);
const inputtingDescription=ref<string>('');

const postTweet=()=>{

  const tweet={id:Math.random(),description:inputtingDescription.value};
  tweets.value.push(tweet);
 
}

const deleteTweet=(id:number)=>{
  tweets.value=tweets.value.filter(t=>t.id !==id)
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
      <input v-model="inputtingDescription" />
      <button class="save-button" @click="postTweet">post</button>
    </div>
    <div  class="tweet-container">
      <p v-show="tweets.length <= 0">No twwets have been added</p>
      <ul>
        <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
          <span class="tweet-list">{{ tweet.description }}</span>
          <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
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
  color:fff;
  font-weight:bold;
  background-color:#68c9c9;
  border-radius:2px;
  border:none;
  width:60px;
  height:22px;
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
.save-button:hover{
  background-color:#37bdbd;
}
.delete-button:hover{
  background-color:#ac783f;
}


.container{
  display: flex;
  flex-direction: column;
   align-items: center;
}

.tweet-list{
  list-style:none;
  margin-bottom:12px;
  border-radius:4px;
  font-size:20px;
  display:flex;
  background-color:rgb(204,219,233);
  padding: 8px 20px;

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
