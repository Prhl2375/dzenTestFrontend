<script setup lang="ts">

</script>

<template>
  <div class="single-comment">
    <div class="comment-line"></div>
    <div class="tweet-wrap">
      <div class="tweet-header">
        <img src="https://pbs.twimg.com/profile_images/1012717264108318722/9lP-d2yM_400x400.jpg" alt="" class="avatar">
        <div class="tweet-header-info">
          Steve Schoger <span>@Steve Schoger</span><span>. Jun 27
</span>
          <p>🔥 If you're tired of using outline styles for secondary buttons, a soft solid background based on the text color can be a great alternative.</p>

        </div>

      </div>
      <div class="tweet-img-wrap">
        <img src="https://pbs.twimg.com/media/Dgti2h0WkAEUPmT.png" alt="" class="tweet-img">
      </div>
    </div>
  </div>
</template>

<style scoped>
.single-comment{
  display: flex;
  flex-direction: row;
}

.comment-line{
  border-left: 1px solid #000;
  margin: 0 10px;
}

img {
  max-width:50%;
}
.avatar {
  border-radius:100px;
  width:48px;
  margin-right: 15px;
}


.tweet-wrap {
  background: rgba(235, 235, 235, 1);
  margin: 0 auto 0;
  border-radius:3px;
  border-bottom: 1px solid rgba(200, 200, 200);
  padding: 30px;
  font-family: 'Roboto', sans-serif;
}

.tweet-header {
  display: flex;
  align-items:flex-start;
  font-size:14px;
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