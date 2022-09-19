<template>
  <div>
    <v-card height="200" class="d-flex justify-center flex-row ma-1">
      <v-card
        v-for="item in selectedArray"
        :key="item"
        :color="$vuetify.theme.dark ? 'blue' : 'blue'"
        class="ma-1"
        :height="200 - 100 / item"
        outlined
        tile
      >
        {{ item }}
      </v-card>
    </v-card>
    <v-btn @click="startSort()">Sort</v-btn>
  </div>
</template>
<script>
export default {
  name: "BubbleSort",
  data() {
    return {
      selectedArray: [],
    };
  },
  methods: {
    shuffleArray(array) {
      for (var i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        const temp = array[i];
        array[i] = array[j];
        array[j] = temp;
      }
      return array;
    },
    sleep(ms) {
      return new Promise((resolve) => setTimeout(resolve, ms));
    },
    async startSort() {
      var thoarray = this.selectedArray;
      for (let i = 0; i < thoarray.length; i++) {
        for (let j = 0; j < thoarray.length - 1; j++) {
          await new Promise((resolve) => {
            setTimeout(() => {
              if (thoarray[j] > thoarray[j + 1]) {
                var temp = thoarray[j];
                thoarray[j] = thoarray[j + 1];
                thoarray[j + 1] = temp;
              }
              this.selectedArray = thoarray.map((x) => x);
              resolve(console.log("here"));
            }, 100);
          });
        }
      }
      console.log(thoarray);
    },
  },
  mounted() {
    var arr = [...Array(10).keys()].map((x) => ++x);
    arr = this.shuffleArray(arr);
    console.log(arr);
    this.selectedArray = arr;
  },
};
</script>
