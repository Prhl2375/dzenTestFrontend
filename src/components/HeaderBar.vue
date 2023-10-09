<script setup lang="ts">

const emit = defineEmits([
    'changeSortingFilterParams'
]);

const props:object = defineProps({
  page: {type: Number, required: true},
  dropdownMenus: {type: Array, required: true},
});
</script>

<template>
  <div class="bar">
    <div class="left">
      <h3>
        ThreadBlog
      </h3>
      <h5>
        pg: {{page}}
      </h5>
    </div>
    <div class="right">
      <div v-for="dropdownMenu in dropdownMenus" :key="dropdownMenu.id" class="dropdown">
        <button class="dropbtn">{{dropdownMenu.name}} &#9662;</button>
        <div class="dropdown-content">
          <a v-for="sortingFilterMethod in dropdownMenu.sorting_filter_methods" @click="emit('changeSortingFilterParams',
          [dropdownMenu.query_name, sortingFilterMethod.id])" href="#">{{sortingFilterMethod.name}}</a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.left{
  display: flex;
  flex-direction: row;
}
.right{
  display: flex;
  flex-direction: row;
  margin-right: 25px;
}
.bar h3{
  color: rgba(235,235,255);
  font-size: 19px;
  font-weight: bolder;
  margin: 0 0 0 13px;
}
.bar h5{
  color: rgba(125,125,145);
  font-size: 15px;
  font-weight: bold;
  margin: 0 0 0 5px;
}
.bar{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 13px 0 13px;
  width: 100%;
  background-color: rgba(35,35,35);
  position: fixed;
  top: 0;
  z-index: 5;
}
/* Style the dropdown container */
.dropdown {
  position: relative;
  display: inline-block;
}

/* Style the dropdown button */
.dropbtn {
  color: rgba(235,235,255);
  font-size: 15px;
  font-weight: bold;
  background-color: transparent;
  border: none;
  cursor: pointer;
}

/* Style the dropdown content (hidden by default) */
.dropdown-content {
  display: none;
  position: absolute;
  background-color: rgba(35,35,35);
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  max-height: 500px;
  overflow: auto;
}

/* Style the dropdown links */
.dropdown-content a {
  border-top: 1px solid rgba(75,75,75);
  display: block;
  padding: 10px 17px 10px 17px;
  text-decoration: none;
  font-weight: bold;
  color: rgba(235,235,255);
  font-size: 13px;
  word-wrap: break-word;
  width: 95px;
}

.dropdown-content a:hover{
  background: black;
}

/* On hover, display the dropdown content */
.dropdown:hover .dropdown-content {
  display: block;
}
</style>