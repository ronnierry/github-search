<template>
  <v-app>
    <!-- 必须有app属性 -->
    <v-app-bar app>github 搜索用户 <span style="font-size : 4px">( api.github.com/search/users )</span></v-app-bar>
    <v-container>
      <v-main>
      <top/>
      <user-list/>
    </v-main>
    </v-container>
  </v-app>
</template>

<script>
import Top from './components/Top.vue';
import UserList from './components/UserList.vue';

export default {
  name: 'App',

  components: {
    Top,
    UserList
  },

  data: () => ({
    //
  }),
};
</script>
