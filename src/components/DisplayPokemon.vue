<template>
  <div class="poke_container">
    <article class="poke" v-for="(poke, i) in pokemon" :key="i">
      <h3>{{ poke["name"] }}</h3>
      <img :src="poke['image_url']" :alt="`A picture of ${poke['name']}`" />
      <p>{{ poke["description"] }}</p>
    </article>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      pokemon: [],
    };
  },

  methods: {
    get_pokemon() {
      axios
        .request({
          url: "http://127.0.0.1:5000/api/pokemon",
        })
        .then((response) => {
          this.pokemon = response['data'];
        })
        .catch((error) => {
          error;
        });
    },
  },

  mounted() {
    this.get_pokemon();
    this.$root.$on("new_pokemon", this.get_pokemon);
  },
};
</script>

<style scoped>
.poke_container {
  display: grid;
  place-items: center;
  width: 100%;
  gap: 30px;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

.poke {
  display: grid;
  place-items: center;
}
</style>