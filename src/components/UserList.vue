<template>
    <div>
    <v-container v-if="progressLinear" style="height: 200px;">
      <v-row
        class="fill-height"
        align-content="center"
        justify="center"
      >
        <v-col
          class="text-subtitle-1 text-center"
          cols="12"
        >
          正在搜索{{keyword}}
        </v-col>
        <v-col cols="6">
          <v-progress-linear
            color="deep-purple accent-4"
            indeterminate
            rounded
            height="6"
          ></v-progress-linear>
        </v-col>
      </v-row>
    </v-container>
    <v-container v-else>
    <user-card v-for="user in users" :key="user.id" :user="user"/>
    </v-container>
   
    </div>
</template>

<script>
import UserCard from './UserCard.vue'
import axios from 'axios'
export default {
    data(){
        return{
            users:[],
            keyword:'',
            progressLinear : false
        }
    },
  components: { UserCard },
  mounted(){
      // 绑定总线事件
      this.$bus.$on('fetchUserListEvent',(value)=>{
          // 搜索key
          this.keyword = value
          // 进度条
          this.progressLinear =true
          setTimeout(() => {
               axios
           .get(`https://api.github.com/search/users?q=${value}`)
           .then((res)=>{
               // 获取数据处理状态
                this.users = res.data.items;
                this.progressLinear =false
            }).catch( (error)=> {
                console.log(error);
            });
          }, 3000);
          
        //   this.users = apiUserList(value)
      })
  },
  destroyed(){
        // 删除绑定总线事件
       this.$bus.$off('fetchUserListEvent')
  }

}
</script>

<style>

</style>