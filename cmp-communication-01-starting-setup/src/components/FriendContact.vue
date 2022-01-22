<template>
  <li>
    <h2>{{ name}} {{ isFavourite === true ? '(Favourite)' : '' }}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavourite">toogleFavourite</button>
    <button @click="$emit('delete',id)">delete</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    id:{
      type: String,
      required: true
    },
    name:{
      type: String,
      required: true
    },
    phoneNumber:{
      type: String,
      required: true
    },
    emailAddress:{
      type: String,
      required: true
    },
    isFavourite: {
      type: Boolean,
      required: true,
      default: false,
    }
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite(){
      this.$emit('toggle-favourite',this.id);
    }
  }
};
</script>