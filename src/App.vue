<template>
  <v-app>
    <v-main>
      <BubbleSort />
    </v-main>
  </v-app>
</template>

<script>
import BubbleSort from "./components/BubbleSort.vue";
export default {
  name: "App",

  components: {
    BubbleSort,
  },

  data: () => ({
    //
  }),
};
</script>
