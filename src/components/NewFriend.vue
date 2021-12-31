<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name: </label>
      <input type="text" v-model="enteredName" />
    </div>
    <div>
      <label>Phone: </label>
      <input type="tel" v-model="enteredPhone" />
    </div>
    <div>
      <label>Email: </label>
      <input type="email" v-model="enteredEmail" />
    </div>
    <div>
      <button>Add New Friend</button>
    </div>
  </form>
</template>

<script>
export default {
  emit: ["add-contact"],
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
    };
  },
  methods: {
    submitData() {
      if (this.enteredName && this.enteredPhone) {
        this.$emit(
          "add-contact",
          this.enteredName,
          this.enteredPhone,
          this.enteredEmail
        );
      } else {
        alert("Name and Number is required.");
      }
      this.enteredName = "";
      this.enteredPhone = "";
      this.enteredEmail = "";
    },
  },
};
</script>
