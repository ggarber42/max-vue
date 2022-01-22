<template>
  <form @submit.prevent="submitData" >
       <div>
            <label >Name</label>
            <input type="text" v-model="inName">
       </div>
       <div>
            <label >Phone</label>
            <input type="tel" v-model="inPhone">
       </div>
       <div>
            <label >Email</label>
            <input type="email" v-model="inEmail">
       </div>
       <div>
            <button>Add Contact</button>
       </div>
  </form>
</template>

<script>
export default {
     emits:['add-contact'],
     data(){
          return{
               inName:'',
               inPhone:'',
               inEmail:'',
          }
     },
     methods:{
          submitData(){
          this.$emit('add-contact',this.inName, this.inPhone, this.inEmail) 
          }
     }
}
</script>
