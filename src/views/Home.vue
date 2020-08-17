<template>
  <div class="home">
   <h1>Adopt a new best friend</h1>
   <h5>there are {{getAllCats.length}} cats in store</h5>
   <h5>there are {{animalsCount}} animals in store</h5>
   <button @click="togglePetForm" class="btn btn-primary">Add New Pet</button>
  <b-form @submit="handleSubmit" v-if="showPetForm">
    <b-form-group id="exampleInputGroup2" label="Your Name:" label-for="exampleInput">
      <b-form-input
      id="pet name"
      type="text"
      v-model="formData.name"
      placeholder="Enter name"
      >
      </b-form-input>
    </b-form-group>
    <b-form-group id="exampleInputGroup3" label="Species:" label-for="exampleInput">
      <b-form-select
      id="species"
      :options="['cats', 'dogs']"
      v-model="formData.name"
      placeholder="Enter name"
      >
      </b-form-select>
    </b-form-group>
  </b-form>
  </div>
</template>

<script>
import {mapActions, mapGetters} from 'vuex'

export default {
  
  name: "Home",
  data(){
    return{
      showPetForm:false,
      formData:{
        name:'',
        age:0,
        species:null
      }
    }
  },
  computed:{
    ...mapGetters([
      'animalsCount',
      'getAllCats'
    ])
  },
  methods:{
    ...mapActions([
      'addPet'
    ]),
    togglePetForm(){
      this.showPetForm = !this.showPetForm
    },
    handleSubmit(){
      const {species, age, name} = this.formData
      const payload={
        species,
        pet:{
          name,
          age
        }
      }
      this.addPet(payload)

  //reset Form Data
  this.formData ={
     name:'',
        age:0,
        species:null
  }
    }
  }

};
</script>
