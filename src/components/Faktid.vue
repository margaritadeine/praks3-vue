<template>
  <div>
   <h1>Numbri faktid</h1>
    <p>Huvitavad faktid iga numbri kohta</p>
   <input type="number" min="0" v-model="number">
   <input type="number" min="0" v-model="incriment">
   <p v-for=''>{{ data }}</p>
    </div>
</template>

<script>
    const axios = require('axios')
    
export default {
  name: 'Faktid',
  data() {
      return {
         data: '',
          number: 0, 
          incriment: 0
        }
    },
    methods: {
        getFact () {
            if (this.number !== '' && this.incriment !== '') {
                 let baseUrl = 'http://numbersapi.com/'
              let url = `${baseUrl}${this.number}..${parseInt(this.number) + parseInt(this.incriment)}`;
             
            
            axios.get(url)
            .then(response => {
               this.data = response.data
            })
            .catch(error => {
                console.log(error)  
            
            })
        }
        }
    },
    watch: {
        number () {
            this.getFact()
        },
        incriment () {
            this.getFact()
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
