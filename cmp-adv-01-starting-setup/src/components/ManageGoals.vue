<template>
<div>
     <h2>Manage Goals</h2>
     <input type="text" ref="goal"/>
     <button @click="setGoal">Set Goal</button>
     <teleport to="body">
          <error-alert v-if="inputIsinvalid">
               <h2>Input is invalid</h2>
               <p>Please enter at leat a few characters...</p>
               <button @click="confirmError"> Try again </button>
          </error-alert>
     </teleport>
</div>
</template>

<script>
import ErrorAlert from './ErrorAlert.vue';
export default {
     components:{
          ErrorAlert
     },
     data(){
          return { 
               inputIsinvalid: false
          };
     },
     methods: {
          setGoal(){
               const value = this.$refs.goal.value
               console.log(value)
               if(value.length === 0){
                    this.inputIsinvalid = true
               }
          },
          confirmError(){
               this.inputIsinvalid = false
          }
     }
}
</script>