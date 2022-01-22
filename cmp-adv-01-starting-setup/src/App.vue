<template>
  <div>
    <the-header></the-header>
    <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>
    <course-goal>
      <template #default="slotProps">
        <h2>{{slotProps.item}}</h2>
        <h2>{{slotProps.anotherProp}}</h2>
      </template>
    </course-goal>
    <button @click="select('active-goals')">Active goals</button>
    <button @click="select('manage-goals')">Manage goals</button>
    <keep-alive>
      <component :is="selectedComp"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import BadgeList from './components/BadgeList.vue';
import UserInfo from './components/UserInfo.vue';
import CourseGoal from './components/CourseGoal.vue'
import ManageGoals from './components/ManageGoals.vue';
import ActiveGoals from './components/ActiveGoals.vue';

export default {
  components:{
    TheHeader,
    BadgeList,
    UserInfo,
    CourseGoal,
    ManageGoals,
    ActiveGoals,
    },
  data() {
    return {
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
      selectedComp: 'active-goals'
    };
  },
  methods:{
    select(cmp){
      this.selectedComp = cmp
    }
  }
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>