<template>
<div class="user-profile">
    <div class="user-profile__user-panel">
    <h1>{{user.username}} - {{fullName}}</h1>
        <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
        <div class ="user-profile__follower_count">
        <strong>Followers: </strong> {{followers}}
        <form class="user-profile__create-twoot">
          <label for="newTwoot">Create Twoot</label>
          <textarea id="newTwoot" rows="4"/></form>
        </div>
    </div>
    <div class="user-profile__twoots-wrapper">
     <TwootItem v-for="twoot in user.twoots" 
     :key="twoot.id" 
     :username="user.username" 
     :twoot="twoot" 
     @favourite="toggleFavourite"/>
    
     </div>
</div> 
</template>

<script> 
import TwootItem from "./TwootItem"

export default { 
      name: 'UserProfile',
      components:{ TwootItem },
 data(){
   return {
     followers: 0,
     user: {
       id: 1,
       username: 'cs87',
       firstName: 'Chris',
       lastName: 'Spann',
       email: 'fakeemail@email.com',
       isAdmin: true,
       twoots: [
         {id:1, content:"hello"},
         {id:2, content:"how are you"}
       ]
     }
   }
 },
 watch:{
 followers(newFollowerCount, oldFollowerCount){
   if (oldFollowerCount < newFollowerCount) {
     console.log(`${this.user.username} has gained a follower!`)
   }
 }
 },
 computed: {
   fullName() {
    return `${this.user.firstName} ${this.user.lastName}`;
   }
 },
 
 methods: {
  followUser() {
    this.followers++
  },

  toggleFavourite(id){
    console.log(`Favourited ${id}`)
  },

  mounted(){
    this.followUser();
  }

 }

}
</script>
