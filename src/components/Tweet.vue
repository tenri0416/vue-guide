<script setup lang="ts">
import {ref} from 'vue'
import TweetPostForm from './TweetPostForm.vue';
import TweetList from './TweetList.vue';


const tweets = ref([{ id: 0, description: 'hell' }, { id: 1, description: 'no' }]);
const inputtingDescription=ref<string>('');

const postTweet = (description:string) => {
  const tweet={id:Math.random(),description}
  tweets.value.push(tweet);
}

const consolePost=(sample:string)=>{
  console.log(sample);
}

const deleteTweet=(id:number)=>{
  tweets.value=tweets.value.filter(t=>t.id !==id)
}
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
                  <!-- @post-tweetは子コンポーネントのemitで定義した名前 -->
                  <!-- 子コンポーネントで定義したemit名を＠emit名で記述して子コンポーネントに渡したい関数をかく -->
      <TweetPostForm @post-tweet="postTweet" @sample-post="consolePost"/>
    <div  class="tweet-container">
      <p v-show="tweets.length <= 0">No twwets have been added</p>
      <ul>
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet"/>
      </ul>
    </div>
  </div>
</template>

<style >




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


</style>
