<script setup lang="ts">
const props:object = defineProps({
  numOfPages: {required: true},
  current_page: {required: true},
});
const emit = defineEmits(['changePage']);
</script>

<template>
  <div class="pagination">
    <span @click="emit('changePage', current_page-1)">&laquo;</span>
    <span v-for="i in numOfPages" :key="i" :class="i==current_page ? 'active' : ''" @click="emit('changePage', i)">{{i}}</span>
    <span @click="emit('changePage', current_page+1)">&raquo;</span>
  </div>
</template>

<style scoped lang="scss">
.pagination {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 13px;
  margin-bottom: 13px;
  user-select: none;
}

.pagination span {
  color: black;
  float: left;
  padding: 8px 16px;
  text-decoration: none;
  font-weight: bold;
}

.pagination span.active {
  background-color: rgba(35,35,35);
  color: white;
}

.pagination span:hover:not(.active) {background-color: #ddd;}
</style>