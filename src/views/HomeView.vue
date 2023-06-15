<template>
  <div >
    <create-pokemon></create-pokemon>
    <display-pokemon></display-pokemon>
  </div>
</template>

<script>
import DisplayPokemon from "@/components/DisplayPokemon.vue";
import CreatePokemon from "@/components/CreatePokemon.vue";
export default {
  components: {
    DisplayPokemon,
    CreatePokemon
  },
}
</script>
