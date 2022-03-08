<template lang="">
    <div>
       <form>
  <div class="mb-3">
    <label for="exampleInput" class="form-label">Name</label>
    <input type="text" v-model='register.name' class="form-control" id="exampleInput">
  </div>
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <input type="email" v-model='register.email' class="form-control" id="exampleInputEmail1">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <input type="password" v-model='register.password' class="form-control" id="exampleInputPassword1">
  </div>
  <button type="submit" @click.prevent='userRegister' class="btn btn-primary">Регистрация</button>
        </form>
    </div>
</template>
<script>
export default {
     name:'registration',
       middleware: 'authtoken',
       data(){
        return {
            register:{
                  name: '',
              email: '',
              password: '', 
            }
        }
    },
    methods:{
      async userRegister() {
      try {
        let data = await this.$axios.$post('/auth/register', this.register)
          await this.$auth.setUserToken(data.access_token);
      } catch (err) {
        console.log(err);
      }
    }
    }
}
</script>
<style lang="">
    
</style>