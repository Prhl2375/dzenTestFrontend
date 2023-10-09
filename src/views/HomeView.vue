<template>
  <div class="home">
    <MainPostsBlog/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MainPostsBlog from "@/components/MainPostsBlog.vue"; // @ is an alias to /src

export default defineComponent({
  name: 'HomeView',
  components: {
    MainPostsBlog
  },
});
</script>
