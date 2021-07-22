<template>
  <div>
       <v-text-field v-model="value" label="输入搜索(按回车搜索)" @keyup.enter="serach"></v-text-field>
  </div>
</template>

<script>
export default {
    data(){
        return {
            value:""
        }
    },
    methods:{
        serach(){
            this.$bus.$emit("fetchUserListEvent",this.value)
        }
    }
}
</script>

<style>

</style>