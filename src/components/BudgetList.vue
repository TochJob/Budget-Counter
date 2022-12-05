<template>
    <div class="budget__list-wrap">
        <ElCard :header="header">
            <template v-if="isEmpty">
                <div class="list-item" v-for="(item, index) in list"  :key="index">
                    <p class="budget__comment">{{item.comment}}</p>
                    <p class="budget__value">{{item.value}}</p>
                    <el-button type="danger" size="mini" @click="deleteItem(item.id)">Delete</el-button>
                </div>
            </template>
            <el-alert type="info" :title="error" v-else :closable="false"></el-alert>
        </ElCard>
        
 
    </div>
</template>

<script>
export default {
    name: "BudgetList",
    data() {
        return {
            header:'Budget list',
            error: 'List is empty'
        }
    },
    props:{
        list:{
            type: Object,
            default: ()=>({})
        }
    },
    computed: {
        isEmpty(){
            return Object.keys(this.list).length
        }
    },
    methods: {
        deleteItem(id){
            this.$emit('deleteItem', id)
        }
    },
}
</script>

<style>

</style>