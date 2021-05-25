<template>
<div class="user-profile">
    <div class="user-profile__user-panel">
    <h1>{{user.username}} - {{fullName}}</h1>
        <div class ="user-profile__follower_count">
        <strong>Followers: </strong> {{followers}}
        </div>
    </div>
</div>
<button @click="followUser">Follow</button>
</template>
<script>
export default {
      name: 'UserProfile',
 data(){
   return {
     followers: 0,
     user: {
       id: 1,
       username: 'cs87',
       firstName: 'Chris',
       lastName: 'Spann',
       email: 'spann.chris@gmail.com',
       isAdmin: false
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
  }
 },
 mounted(){
  this.followUser();
 }
}
</script>