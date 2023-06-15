<template>
  <div>
    <h2>New Pokemon</h2>
    <input type="text" placeholder="Name" ref="name_input" />
    <input type="text" placeholder="Image" ref="img_input" />
    <textarea
      ref="description_input"
      cols="30"
      rows="10"
      placeholder="Description"
    ></textarea>
    <button @click="post_pokemon">SUBMIT</button>
    <p>{{ status }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      status: undefined,
    };
  },
  methods: {
    post_pokemon() {
      this.status = "Loading. . .";
      axios
        .request({
          url: "http://127.0.0.1:5000/api/pokemon",
          method: "POST",
          data: {
            name: this.$refs["name_input"].value,
            image_url: this.$refs["img_input"].value,
            description: this.$refs["description_input"].value,
          },
        })
        .then((response) => {
          response;
          this.status = "New Pokemon Inserted";
          this.$root.$emit("new_pokemon");
        })
        .catch((error) => {
          error;
          this.status = "Sorry, something went wrong.";
        });
    },
  },
};
</script>

<style scoped>
</style>