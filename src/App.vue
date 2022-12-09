<script setup></script>

<template>
<h1>{{title}}</h1>
<h2>Your name is: {{current_user}}</h2>
<input v-model="current_user" placeholder="your name here">
<button @click="add_prev()">Update</button>

<div class="container">
  <div class="emoji"><img class="Icon" :src="image" alt="Emoji icon" @click="emojiNumber++"></div>
  <div class="heart"><img class="Icon" :src="image2" alt="Heart icon" @click="heartNumber++"></div>
  <div class="uparrow"><img class="Icon" :src="image3" alt="Arrow up icon" @click="uparrowNumber++"></div>
  <div class="downarrow"><img class="Icon" :src="image4" alt="Arrow down icon" @click="downarrowNumber++"></div>
  <div class="empty"></div>
  <div class="emojiNumber" @click="(emojiNumber = 0)"><p>{{emojiNumber}}</p></div>
  <div class="heartNumber" @click="(heartNumber = 0)"><p>{{heartNumber}}</p></div>
  <div class="uparrowNumber" @click="(uparrowNumber = 0)"><p>{{uparrowNumber}}</p></div>    
  <div class="downarrowNumber" @click="(downarrowNumber = 0)"><p>{{downarrowNumber}}</p></div>
</div>

<ul class="rooms">
  <li><a class="active" href="#room1">Room 1</a></li>
  <li><a href="#room2">Room 2</a></li>
  <li><a href="#room3">Room 3</a></li>
  <li><a href="#room4">Room 4</a></li>
  <li><a class="addRoom" href="#+room">+ Room</a></li>
</ul>

<h2 class="lastReactions">{{lastReactions}}</h2>

<p v-for="user in users" :key="user.id">
  {{user.name}}
</p>

</template>

<script>
import userData from './assets/users.json'

export default {
  data: function(){
    return {
      users: userData,
      title: 'Please leave a reaction:',

      image: 'src/assets/images/happy.png',
      image2: 'src/assets/images/heart.png',
      image3: 'src/assets/images/up-arrow.png',
      image4: 'src/assets/images/down-arrow.png',

      emojiNumber: 0,
      heartNumber: 0,
      uparrowNumber: 0,
      downarrowNumber: 0,

      lastReactions: 'Last reactions:',

      current_user: ''
      
    }
  },
  methods: {
    add_prev(){
      console.log(this.current_user)
      console.log(userData[0].name)
      console.log(userData[1].name)
      console.log(userData[2].name)

      const user0 = userData[0].name
      const user1 = userData[1].name
      const user2 = userData[2].name
      
      userData[0].name = this.current_user
      userData[1].name = user0
      userData[2].name = user1
      userData[3].name = user2

      this.current_user = ' '
    }
  }

}
</script>

<style scoped>

</style>
