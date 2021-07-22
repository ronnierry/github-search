<template>
  <v-card
    transition="scale-transition"
    :loading="loading"
    :max-width="imgWidth"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="400"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      :height="imgWidth"
      :src="user.avatar_url"
    ></v-img>

     <v-card-title style="font-size:1em" class="text-7"> 用户 ：{{user.login}}</v-card-title>

    <v-card-text >
        github <a :href="user.html_url">{{user.html_url}}</a>
    </v-card-text>
   
  </v-card>
</template>

<script>
export default {
    data(){
        return {
            loading : false,
            imgWidth : 150
        }
    },
    props:['user']
}
</script>

<style>
 .v-card {
       float: left;
       margin: 30px;
}
</style>