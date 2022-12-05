<template>
    <el-card>
        <el-form ref="addItemForm" :model="formData" :rules="rules">
          <el-form-item label="Type" prop="type">
            <el-select class="choice-element" v-model="formData.type" placeholder="Choose type" required>
              <el-option label="Income" value="INCOME"/>
              <el-option label="Outcome" value="OUTCOME"/>
            </el-select>
          </el-form-item>
          <el-form-item label="Comment" prop="comment">
            <el-input v-model="formData.comment" placeholder=""/>
          </el-form-item>
          <el-form-item label="Value" prop="value">
            <el-input v-model.number="formData.value" placeholder=""/>
          </el-form-item>
          <el-button @click="onSubmit" type="primary">Submit</el-button>
        </el-form>
    </el-card>
</template>

<script>
export default {
    name:"BudgetForm",
    data() {
        return {
            formData:{
                type: 'INCOME',
                comment: '',
                value: 0
            },
            rules:{
                type: [{required: true, message:'Please, select the type', trigger: 'blur'}],
                comment: [{required: true, message:'Please, input the comment!', trigger: 'change'}],
                value:[
                    {required: true, message:'Please, input value', trigger: 'blur'},
                    {type: 'number', message:'Value must be a number', trigger: 'blur'},
    
                ]
            }
        }
    },
    methods: {
        onSubmit(){
            this.$refs.addItemForm.validate(valid=>{
                if(valid){
                    this.$emit('submitForm', {...this.formData})
                    this.$refs.addItemForm.resetFields();
                }
            });
        }
    },
}
</script>

<style>

</style>