<template>
  <li>
    <h2>
      {{ favorite ? "❤" : "" }} {{ name }} {{ blockContact ? "(Blocked)" : "" }}
    </h2>
    <button @click="toggleFavorite">Favorite</button>
    <button @click="toggleBlock">Block</button>
    <button @click="toggleDetails">Show Details</button>
    <button @click="$emit('delete', id)">x</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li v-if="emailAddress"><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  emit: ["toggle-block", "delete"],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: false,
    },
    blockContact: {
      type: Boolean,
      required: false,
      default: false,
    },
    favorite: {
      type: Boolean,
      required: false,
      default: false,
    },
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
    toggleBlock() {
      this.$emit("toggle-block", this.id);
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
  },
};
</script>
