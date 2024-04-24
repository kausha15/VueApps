<script>
import axios from 'axios'
import ItemList from './components/ItemList.vue'
import { useCounterStore } from './store/useCounterStore'

export default {
  components: { ItemList },
  name: 'App',
  data() {
    return {
      list: [],
      useCounter: useCounterStore()
    }
  },
  async mounted() {
    let result = await axios.get('https://reqres.in/api/users?page=1')
    this.list = result.data.data
  },
  methods: {
    removeItem(item) {
      console.log(' I am here', item)
      const arr = this.list.filter(function (a) {
        console.log(a.id + ' ' + item.id)
        return a.id !== item.id
      })
      this.list = arr
    }
  }
}
</script>

<template>
  <h1>Parent</h1>
  <h2>Count : {{ useCounter.count }} -- {{ useCounter.double }}</h2>
  <button @click="useCounter.increment">Click Me</button>
  <item-list :list="list" @remove-item="removeItem"></item-list>
</template>

<style scoped></style>
