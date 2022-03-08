<template lang="">
    <div>
      
        <!-- <div>
             {{ user }}  
        </div>
        <div>
            {{ logged }}
        </div>
        <div>
            {{ user.name }}
        </div> -->
       <form>
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <input type="email" v-model='login.email' class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <input type="password" v-model='login.password' class="form-control" id="exampleInputPassword1">
  </div>
  <button type="submit" @click.prevent='userLogin' class="btn btn-primary">Войти</button>
</form>
    </div>
</template>
<script>
export default {
    name:'login',
    middleware: 'authtoken',
    data(){
        return {
            login:{
              email: '',
              password: '', 
            }
        }
    },
    computed:{
        // user(){
        //     return this.$auth.user;
        // },
        // logged(){
        //     return this.$store.state.auth.loggedIn;
        // }
    },
    methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        // console.log(response.data)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
<style lang="">
    
</style>