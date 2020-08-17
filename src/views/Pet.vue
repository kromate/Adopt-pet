<template>
  <div>
 <h1>{{animal.name}} </h1> 
 <p>Age: {{animal.age}} years old</p>
 <p>Breed: {{animal.breed}} </p>
 <p></p>
 
  </div>
</template>

<script>
import {mapState} from 'vuex'
  export default {
    data() {
      return{  
        animal:{}      
      }

    },

      computed:{
    ...mapState([
      'cats',
      'dogs'
    ])
  },
  mounted(){  
      const animal = this[this.$route.params.species][this.$route.params.id]
      this.animal = animal
    
  }
  };
</script>

<style scoped>

</style>