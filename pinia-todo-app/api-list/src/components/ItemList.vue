<script>
export default {
  name: 'ItemList',
  props: {
    list: Array
  },
  data() {}
}
</script>

<template>
  <h1>Child</h1>
  <ul class="item" v-for="item in list" :key="item.id">
    <li><img :src="item.avatar" /></li>
    <li>{{ item.id }}</li>
    <li>{{ item.first_name }}</li>
    <li>{{ item.last_name }}</li>
    <li>{{ item.email }}</li>
    <button @click="$emit('removeItem', item)">Remove</button>
  </ul>
</template>

<style scoped>
.item {
  display: flex;
}
.item li {
  display: inline-block;
  padding: 5px;
  border: 1px solid grey;
  width: 187px;
  text-align: center;
}
</style>
