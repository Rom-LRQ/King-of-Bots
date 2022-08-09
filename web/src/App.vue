<template>
  <div class="fontc" >Bot昵称：{{bot_name}}</div>
  <div class="fontc" >Bot战力：{{bot_rating}}</div>
  <router-view/>
</template>

<script>
import $ from 'jquery';
import { ref } from 'vue';

export default {
  name: "app",
  setup: () => {
    let bot_name = ref("");
    let bot_rating = ref("");
    $.ajax({
      url: "http://127.0.0.1:3000/pk/getinfo/",
      type: "get",
      success: resp => {
        bot_name.value = resp.name;
        bot_rating.value = resp.rating;
      }
    })
    return {
      bot_name,
      bot_rating
    }
  }
}
</script>

<style>
  body {
    background-image: url(https://img.zcool.cn/community/01274855f7a84832f875a132a15b65.jpg?x-oss-process=image/auto-orient,1);
    background-size: cover;
  }
  .fontc {
    color: aqua;
  }
</style>
