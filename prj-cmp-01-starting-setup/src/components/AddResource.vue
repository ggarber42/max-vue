<template>
     <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
     <template #default>
          <p>
               Errouuuu
          </p>
     </template>
     <template #actions>
          <base-button @click="confirmError">Okay</base-button>
     </template>
     </base-dialog>
     <base-card>
          <form @submit.prevent="handleSubmit">
               <div class="form-control">
                    <label for="title">Title</label> 
                    <input id="title" name="title" type="text" ref="title"/>
               </div> 
               <div class="form-control">
                    <label for="description">Description</label> 
                    <input id="description" name="description" type="text" rows="3" ref="description"/>
               </div> 
               <div class="form-control">
                    <label for="link">Link</label> 
                    <input id="link" name="link" type="url" ref="link"/>
               </div> 
               <div>
                    <base-button type="submit">
                         Add Resource
                    </base-button>
               </div> 
          </form>
     </base-card>
</template>

<script>
import BaseButton from './UI/BaseButton.vue'

export default {
  components: { BaseButton },
     inject: ['addResource'],
     data(){
          return{
               inputIsInvalid: false
          }
     },
     methods:{
          handleSubmit(){
               const id = this.$refs.title.value.toLowerCase()
               const title = this.$refs.title.value
               const description = this.$refs.description.value
               const link = this.$refs.link.value
               if(id.trim() === '' || title === '' || description === '' || link === '') {
                    this.inputIsInvalid = true
                    return
               }
               this.addResource({
                    id,
                    title,
                    description,
                    link
               })
          },
          confirmError(){
               this.inputIsInvalid = false
          }
     }
}
</script>

<style scoped>
     label {
     font-weight: bold;
     display: block;
     margin-bottom: 0.5rem;
     }

     input,
     textarea {
     display: block;
     width: 100%;
     font: inherit;
     padding: 0.15rem;
     border: 1px solid #ccc;
     }

     input:focus,
     textarea:focus {
     outline: none;
     border-color: #3a0061;
     background-color: #f7ebff;
     }

     .form-control {
     margin: 1rem 0;
     }
</style>