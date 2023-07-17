<script setup lang="ts">
import { ref,defineEmits } from 'vue'

const inputtingDescription=ref<string>('')
//resでリアクティブな値を指定する

const sampleInput=ref<string>('');

const emit=defineEmits(['post-tweet','sample-post']);
//emitで親コンポーネントから関数を取得するために定義する


//ぽたんを押した時にemitで親のコンポーネントの関数の処理がされるように記述する
const postTweet=()=>{
  emit('post-tweet', inputtingDescription.value)
}


const postSample=()=>{
emit('sample-post',sampleInput.value);
}

</script>

<template>
  <div class="form-container">
    <!-- インプットタグに値が入った時にrefの変数に値が入るようにする -->
    <input v-model="inputtingDescription" />
      <!-- ボタンが押された時にpostTweet関数の処理がされるように定義をする -->
      <button class="save-button" @click="postTweet">post</button>
  </div>
  <input v-model="sampleInput"/>
  <button @click="postSample">ボタン</button>
</template>

<style>
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
.save-button{

  color:fff;
  font-weight:bold;
  background-color:#68c9c9;
  border-radius:2px;
  border:none;
  width:60px;
  height:22px;
  margin-top:12px;
}

.save-button:hover{
  background-color:#37bdbd;
}
</style>
