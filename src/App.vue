<template>
  <div id="app">
    <Form @submitForm="onFormSubmit"/>
    <budget-list :list="list" @deleteItem="onDeletItem"/>
    <total-balnce :total="this.totalBalance" />
  </div>
</template>

<script>
import BudgetList from './components/BudgetList.vue'
import Form from './components/form.vue'
import TotalBalnce from './components/totalBalnce.vue'

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalnce,
    Form
  },
  data() {
    return {
      list:{
        1: {
          type: 'INCOME',
          value: 123,
          comment: 'Some comment',
          id:1
        },
        2: {
          type: 'OUTCOME',
          value: 123,
          comment: 'Some outcome comment',
          id:2
        }
      }
    }
  },
  methods: {
    onDeletItem(id){
      this.$delete(this.list, id)
    },
    onFormSubmit(data){
      let newObj = {
        ...data,
        id: String(Math.random()) 
      };

      this.$set(this.list, newObj.id, newObj)
    }
  },
  computed: {
    totalBalance(){
      return Object.values(this.list).reduce((acc, item) => acc + item.value, 0)
    }
  }
}
</script>

<style lang="scss">
  @import '@/assets/scss/main.scss'



</style>
