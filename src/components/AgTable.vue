<template>
  <ag-grid-vue
    style="width: 1200px; height: 200px"
    class="ag-theme-mycustomtheme"
    :columnDefs="columnDefs"
    :rowData="dataForTable"
  >
  </ag-grid-vue>
</template>

<script>
import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue3";

export default {
  name: "AgTable",

  data() {
    return {
      ARR_URLS_IMAGES: [
        "../assets/images/coding-one.jpeg",
        "../assets/images/coding-two.jpeg",
        "../assets/images/coding-three.jpeg",
        "../assets/images/coding-four.webp",
        "../assets/images/coding-five.webp",
        "../assets/images/coding-six.webp",
      ],

      ARR_STR: [
        "first_value",
        "second_value",
        "third_value",
        "fourth_value",
        "fifth_value",
      ],

      dataForTable: [],

      columnDefs: [
        { headerName: "First column", field: "imgPath" },
        { headerName: "Second column", field: "randStr1" },
        { headerName: "Third column", field: "floatDec2" },
        {
          headerName: "Fourth column",
          field: "randomInt1 randomInt2",
        },
        { headerName: "Fifth column", field: "randStr2" },
        { headerName: "Sixth column", field: "randStrFromArr" },
      ],
    };
  },

  methods: {
    getRandomInt(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min + 1)) + min;
    },

    getRandomFloat(min, max) {
      return Math.floor(Math.random() * (max - min) + min) / min;
    },

    getRandomStr(length) {
      return (Math.random() + 1).toString(32).substring(2).slice(0, length);
    },

    generateRandomData(num) {
      for (let i = 0; i < num; i++) {
        const indexUrl = this.getRandomInt(0, this.ARR_URLS_IMAGES.length - 1);
        const indexStr = this.getRandomInt(0, this.ARR_STR.length - 1);

        const newElem = {
          randStr1: this.getRandomStr(10),
          floatDec2: this.getRandomFloat(100, 1000),
          floatDec4: this.getRandomFloat(10000, 100000),
          randInt1: this.getRandomInt(10, 50),
          randInt2: this.getRandomInt(50, 99),
          imgPath: this.ARR_URLS_IMAGES[indexUrl],
          randStr2: this.getRandomStr(10),
          randStrFromArr: this.ARR_STR[indexStr],
        };

        this.dataForTable.push(newElem);
      }
    },
  },
  components: {
    AgGridVue,
  },
  mounted() {
    this.generateRandomData(100);
  },
};
</script>

<style lang="scss">
.ag-theme-mycustomtheme {
  margin-bottom: 150px;
  border-radius: 15px;
  font-family: "Raleway";
  font-weight: 500;
  font-size: 16px;
  min-height: 250px;
  --ag-foreground-color: inherit;
  --ag-background-color: #161618;
}

.ag-header-cell-text {
  overflow: visible;
}

.ag-root-wrapper.ag-layout-normal {
  border-radius: 10px;
}

.ag-theme-mycustomtheme .ag-header {
  font-style: italic;
}
</style>
