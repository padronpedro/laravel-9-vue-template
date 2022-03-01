<template>
  <v-app>
    <v-main>
      <v-container>
        <v-btn @click="login()">Login</v-btn>
        <v-btn @click="register()">Register</v-btn>
        <v-btn @click="test()">Test</v-btn>
        {{ jsonResponse}}
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      jsonResponse: ''
    }
  },
  methods: {
    test () {
        axios.get('api/test')
          .then(response => {
            console.log('test',response)
            this.jsonResponse = response.data
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

    },
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