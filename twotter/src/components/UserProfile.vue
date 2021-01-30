/* eslint-disable */
<template>
  
  <div class="user-profile">
    <div class="user-profile_user-panel">
        <h1 class = "user-profile_username">@{{ user.username }}</h1>          
        <div class= "user-profile__admin-badge" v-if="user.isAdmin">
          Admin
        </div>
        <div class= "user-profile_follower-count">
          <strong> Followers: </strong> {{ followers }}
        </div>
    </div>     
    <div class= "user-profile_twoots-wrapper">
      <TwootItem v-for="twoot in user.twoots" :key="twoot.id" :username="user.username" :twoot="twoot"/>
    </div>
  </div>   
</template>

<script>

import TwootItem from "./TwootItem";


export default {
  name: 'UserProfile',
  components: { TwootItem },
  data(){
    return {

      followers: 0,
      user: {
        id : 1,
        username: 'aalebottini',
        firstName: 'ale',
        lastName: 'B',
        email: 'alebottini002@gmail.com',
        isAdmin: true,
        twoots: [
          {id: 1, content: "wlcome to twotter"},
          {id: 2, content: "Dont be afraid"}
        ]
      }
    }
   },
   watch: {
     followers (newFollowerCount, oldFolloweCount){
       if (oldFolloweCount < newFollowerCount) {
         console.log (`${this.user.username} has gained a follower`)
       }
     }

   },
    computed: {
      fullName() {
        return `${this.user.firstName} ${this.user.lastName}`;

      }
  },
  methods: {
    followUser(){
      this.followers++
    }
    //toggleFavourite(id) {
      //console.log(`favourited Tweet #${id}`)
    //}
  },
  mounted (){
    this.followUser()
  }
}

</script>

<style>
.user-profile{
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100%;
    padding: 50px 5%;
}

.user-profile_user-panel{
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #0FE3E8;
  
}

.user-profile__admin-badge{
  background: rebeccapurple;
  color: white;
  padding:0 10px;
  border-radius: 5px;
  margin-right: auto;
  font-weight: bold;

}

.user-profile_username{
  margin: 5px;
}

.user-profile_follower-count{
  margin-right:auto;
}
</style>
