<template>

  <div class="app">
    @_{{user.username}}-{{fullName}}

    <div>
     <strong>followers: </strong> {{ followers}}
    </div>


    <button @click="followUser">Follow</button>

  </div>
 
</template>

<script>


export default {
  name: 'App',

  data(){
    return {
      followers: 0,
      user: {
        id:1,
        username: 'jdoe',
        firstName: 'John',
        lastName: 'Doe',
        email: 'johndoe@gmail.com',
        isAdmin: true
      }
    }
  },

  watch: {
    followers(newFollowerCount, oldFollowerCount){
      if(oldFollowerCount < newFollowerCount){
        console.log(`${this.user.username} has gained a follower!`)
      }
    }
  },

  computed: {
    fullName(){
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },

  methods: {
    followUser(){
      this.followers++
    }
  },

// loaded the app vue
  mounted(){
    this.followUser();
  }
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  display:flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  

}
</style>
