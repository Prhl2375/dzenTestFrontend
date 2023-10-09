<script setup lang="ts">
import SingleComment from "@/components/SingleComment.vue";
const props:object = defineProps({
    postData: {type: Object, required: false},
});
</script>

<template>
  <div class="tweet-wrap">
    <div class="tweet-header">
      <img :src="postData.avatar" alt="" class="avatar">
      <div class="tweet-header-info">
        {{postData.name}} <span>{{postData.email}}</span><span>{{postData.created_at}}
</span>
        <p>{{postData.text}}</p>
      </div>

    </div>

  </div>
  <SingleComment/>
</template>

<style scoped>
img {
  max-width:50%;
}
.avatar {
  border-radius:100px;
  width:48px;
  margin-right: 15px;
}


.tweet-wrap {

  margin: 0 auto 0;
  border-radius:3px;
  padding: 30px;
  border-bottom: 1px solid #e6ecf0;
  border-top: 1px solid #e6ecf0;
  font-family: 'Roboto', sans-serif;
}

.tweet-header {
  display: flex;
  align-items:flex-start;
  font-size:14px;
  text-align: left;
}
.tweet-header-info {
  font-weight:bold;
}
.tweet-header-info span {
  color:#657786;
  font-weight:normal;
  margin-left: 5px;
}
.tweet-header-info p {
  font-weight:normal;
  margin-top: 5px;

}
.tweet-img-wrap {
  padding-left: 60px;
}

.tweet-info-counts {
  display: flex;
  margin-left: 60px;
  margin-top: 10px;
}
.tweet-info-counts div {
  display: flex;
  margin-right: 20px;
}
.tweet-info-counts div svg {
  color:#657786;
  margin-right: 10px;
}
@media screen and (max-width:430px){
  body {
    padding-left: 20px;
    padding-right: 20px;
  }
  .tweet-header {
    flex-direction:column;
  }
  .tweet-header img {
    margin-bottom: 20px;
  }
  .tweet-header-info p {
    margin-bottom: 30px;
  }
  .tweet-img-wrap {
    padding-left: 0;
  }
  .tweet-info-counts {
    display: flex;
    margin-left: 0;
  }
  .tweet-info-counts div {
    margin-right: 10px;
  }
}
</style>