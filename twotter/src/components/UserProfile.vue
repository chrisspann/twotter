<template>
<div class="user-profile">
    <div class="user-profile__user-panel">
    <h1>{{user.username}} - {{fullName}}</h1>
        <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
        <div class ="user-profile__follower_count">
        <strong>Followers: </strong> {{followers}}
        </div>
    </div>
    <div class="user-profile__twoots-wrapper">
     <div class="user-profile__twoot" v-for="twoot in user.twoots" :key=twoot.id>
       {{twoot.content}}
     </div>
</div>
</div>

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
  }
 },
 mounted(){
  this.followUser();
 }
}
</script>