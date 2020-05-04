<template>
    <div class="users-wrap">
        <h1 class="users-header">Our cheerful users</h1>
        <p class="users-context">Attention! Sorting users by registration date</p>
        <div class="users-list">
            <div class="user" v-for="(item, i) in users" :key="i">
                <div class="user-wrap" v-if="i < showUsers">
                    <div class="user-img">
                        <img :src="item.img" alt="">
                    </div>
                    <h2 class="user-name">{{ item.name }}</h2>
                    <p class="user-contact user-position">{{ item.workPosition }}</p>
                    <p class="user-contact user-email">{{ item.email }}</p>
                    <p class="user-contact user-phone">{{ item.phone }}</p>
                </div>
            </div>
        </div>
        <button class="singleBtn" @click="showMore"><p>Show more</p></button>
    </div>
</template>

<script>
  export default {
    name: "Users",
    props: ['users'],
    data () {
      return {
        showUsers: 6
      }
    },
    methods: {
      showMore () {
        if (this.users.length > this.showUsers) {
          this.showUsers += 3
        }
      }
    }
  }
</script>

<style scoped>

</style>
