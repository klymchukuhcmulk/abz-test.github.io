<template>
  <div id="app">
    <div class="nav">
      <div class="logo">
        <img src="./assets/logo.svg" alt="">
      </div>
      <div class="navMenu">
        <a href="#reg">About me</a>
        <a href="#reg">Relationship</a>
        <a href="#reg">Requirements</a>
        <a href="#reg">Users</a>
        <a href="#reg">Sign up</a>
      </div>
      <div class="navBtn" @click="sidebarOn = !sidebarOn">
        <img src="./assets/menu-icon.svg" alt="">
      </div>
    </div>
    <div class="menuSidebarBack" @click="sidebarOn = false" v-if="sidebarOn"></div>
    <div class="menuSidebar" v-if="sidebarOn">
      <div class="logo">
        <img src="./assets/logo.svg" alt="">
      </div>
      <div class="navSidebar">
        <div class="hr"></div>
        <a href="#reg">About me</a>
        <a href="#reg">Relationship</a>
        <a href="#reg">Users</a>
        <a href="#reg">Sign up</a>
        <a href="#reg">Terms and Conditions</a>
        <div class="hr"></div>
        <a href="#reg">How it works</a>
        <a href="#reg">Partnership</a>
        <a href="#reg">Help</a>
        <a href="#reg">Leave testimonial</a>
        <a href="#reg">Contact us</a>
        <div class="hr"></div>
        <a href="#reg">Articles</a>
        <a href="#reg">Our news</a>
        <a href="#reg">Testimonials</a>
        <a href="#reg">Licenses</a>
        <a href="#reg">Privacy Policy</a>
      </div>
    </div>
    <intro/>
    <users :users="users"/>
    <registration id="reg" @add="addUser"/>
    <footer>
      <a href="#reg">&copy; abz.agency specially for the test task</a>
    </footer>
  </div>
</template>

<script>
  import Intro from './components/Intro'
  import Users from './components/Users'
  import Registration from './components/Registration'

  export default {
    data () {
      return {
        sidebarOn: false,
        users: [
          {name: 'Maximillian', email: 'controldepartment@gmail.com', phone: '+380 50 678 03 24', workPosition: 'Leading specialist of the Control Department', img: require('@/assets/photo-cover.svg')},
          {name: 'Adolph Blaine Charles David Earl Matthew Matthew', email: 'adolph.blainecharles@gmail.com', phone: '+380 50 678 03 24', workPosition: 'Contextual advertising specialist', img: require('@/assets/photo-cover.svg')},
          {name: 'Elizabeth', email: 'elisabet.front@gmail.com', phone: '+380 50 678 03 24', workPosition: 'Frontend developer', img: require('@/assets/photo-cover.svg')},
          {name: 'Alexander Jayden', email: 'alexander.back@gmail.com', phone: '+380 50 678 03 24', workPosition: 'Backend developer', img: require('@/assets/photo-cover.svg')},
          {name: 'Noah', email: 'noah1998@gmail.com', phone: '+380 50 678 03 24', workPosition: 'QA', img: require('@/assets/photo-cover.svg')},
          {name: 'Liamgrievescasey Smith Wiam', email: 'iamgrievescasey.smith@gmail.com', phone: '380 50 678 03 24', workPosition: 'Lead designer', img: require('@/assets/photo-cover.svg')}
        ]
      }
    },
    components: {
      Intro,
      Users,
      Registration,
    },
    methods: {
      addUser (user) {
        this.users.push(user)
      }
    }
  }
</script>

<style lang="scss">
  @import "scss/main.scss";
</style>
