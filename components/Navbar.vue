<template lang="">
    <div>
        <nuxt-link to="/">Home page</nuxt-link>
        <nuxt-link v-if='!logged' to="/login">login</nuxt-link>
        <nuxt-link v-if='!logged' to="/registration">registration</nuxt-link>
        <nuxt-link to="/profile">profile</nuxt-link>
        <a href='#' @click.prevent='logout'>logout</a>

    </div>
</template>
<script>
export default {
      computed:{
        logged(){
            return this.$store.state.auth.loggedIn;
        }
    },
    methods: {
        async logout(){
           await this.$auth.logout();
        }
    },
}
</script>
<style lang="">
    
</style>