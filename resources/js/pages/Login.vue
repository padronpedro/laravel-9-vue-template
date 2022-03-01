<template>
  <div>
    <button @click="login()">Login</button>
    <button @click="register()">Register</button>
  </div>
</template>

<script>
export default {
  methods: {
    login() {
      axios.get('/sanctum/csrf-cookie').then(response => {
        console.log('sanctum',response)
        let parameters = {
          email: 'a1@a1.com',
          password: '13910898',
        }
        axios.post('login', parameters)
          .then(response => {
            console.log('login',response)
              if(response.data.status=='ERROR')
              {
                  // this.$showError(this.$t('Error')+': '+response.data.message,'error',this)
              }else{
                  // window.location='/home'
              }
          })
          .catch(error => {
              // this.loading = false
              // var getResponse = error.response.data
              // this.$showError(getResponse.message,'error',this)
          })
      })
    },
    register() {
      axios.get('/sanctum/csrf-cookie').then(response => {
        console.log(response)
        let parameters = {
          email: 'a1@a1.com',
          password: '13910898',
          password_confirmation: '13910898',
          name: 'a1',
        }
        axios.post('register', parameters)
          .then(response => {
            console.log(response)
              if(response.data.status=='ERROR')
              {
                  // this.$showError(this.$t('Error')+': '+response.data.message,'error',this)
              }else{
                  // window.location='/home'
              }
          })
          .catch(error => {
              // this.loading = false
              // var getResponse = error.response.data
              // this.$showError(getResponse.message,'error',this)
          })
      })
    }
  }
}
</script>

<style>

</style>