<template>
  <div>
    <h1>Dogs for Adoption</h1>
    <b-table  striped hover :items="dogs">
      <template slot="name" slot-scope="data">
      <a :href="`#${data.value.replace(/[^a-z]+/i,'-').toLowerCase()}`">
  {{data.value}}
      </a>
      </template>
    </b-table>
    
  </div>
</template>

<script>
import {mapState} from 'vuex'
  export default {
    data() {
      return{        
      }

    },

      computed:{
    ...mapState([
      'dogs'
    ])
  }
  };
</script>

<style scoped></style>
