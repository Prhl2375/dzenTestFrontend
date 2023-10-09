<script setup lang="ts">
import SinglePost from "@/components/SinglePost.vue";
import {onMounted, ref} from "vue";
import axios from "axios";
import {useRoute} from "vue-router";
import PaginationBar from "@/components/PaginationBar.vue";
import HeaderBar from "@/components/HeaderBar.vue";
const apiPath:string = process.env.VUE_APP_ROOT_API;
const posts:object = ref([]);
const dropdownMenus:object = ref([]);
const route:object = useRoute();
const numOfPages:object = ref(0);
const page:object = ref(route.query.page ? route.query.page : 1);
const SF:object = ref({});


function getSortingFilterFromUrl():void {
  for(let i: Number = 0; i<dropdownMenus.value.lenght; i++){
    if(route.query[dropdownMenus.value[i].query_name] != undefined){
      SF.value[dropdownMenus.value[i].query_name] = route.query[dropdownMenus.value[i].query_name];
    }
  }
}
function changeSortingFilterParams(data): void{
  SF.value[data[0]] = data[1];
  const url = new URL(window.location.href);
  url.searchParams.set(data[0], data[1]);
  history.pushState({}, "", url);
  console.log(SF.value);
  getThread();
}
function getThread(): void{
  const sortingFilter = {};
  if (Object.keys(SF.value).length != 0){
    Object.assign(sortingFilter, SF.value);
  }else{
    Object.assign(sortingFilter, route.query);
  }
  const data = {page: page.value,
  sortingFilter: sortingFilter};
  axios.post(apiPath + '/posts', data).then(response => {
    posts.value = response.data.posts;
    numOfPages.value = Math.ceil(posts.value.total/posts.value.per_page);
    dropdownMenus.value = response.data.dropdownMenus;
    getSortingFilterFromUrl();
  })
}

onMounted(() => {
  getThread();
});
function changePage(num:number):void{
  page.value = num;
  const url = new URL(window.location.href);
  url.searchParams.set("page", String(num));
  history.pushState({}, "", url);
  getThread();
}
</script>

<template>
  <HeaderBar :page="page" :dropdownMenus="dropdownMenus" @change-sorting-filter-params="changeSortingFilterParams"/>
  <div class="posts">
    <SinglePost v-for="post in posts.data" :key="post.id" :post-data="post"/>
  </div>
  <pagination-bar :current_page="posts.current_page" :num-of-pages="numOfPages" @change-page="changePage"/>
  {{dropdownMenus}}
</template>

<style scoped lang="scss">
.posts{
  margin-top: 43px;
}


</style>