<template>
  <ag-grid-vue
    style="width: 1200px; height: 200px"
    class="ag-theme-mycustomtheme"
    :columnDefs="columnDefs"
    :rowData="rowData"
  >
  </ag-grid-vue>
</template>

<!-- {
	?val1: random string, length 10,
  ?val2: random float 2 decimal,
  ?val3: random float 4 decimal,
  ?val4: random int,
  ?val5: random int,
  val6: random img path,
  ?val7: random string, length 10,
  val8: одно из 5ти значений строк [str1, str2, str3, str4, str5]

} -->

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
      const arr = [];

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

        arr.push(newElem);
      }
      return arr;
    },
  },
  components: {
    AgGridVue,
  },
  mounted() {
    this.dataForTable = this.generateRandomData(8);
    console.log(this.dataForTable);
  },
  setup() {
    return {
      columnDefs: [
        { headerName: "First column", field: "make" },
        { headerName: "Second column", field: "model" },
        { headerName: "Third column", field: "price" },
        { headerName: "Fourth column", field: "price" },
        { headerName: "Fifth column", field: "price" },
        { headerName: "Sixth column", field: "price" },
      ],
      rowData: [
        { make: "Toyota", model: "Celica", price: 35000 },
        { make: "Ford", model: "Mondeo", price: 32000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
        { make: "Porsche", model: "Boxster", price: 72000 },
      ],
    };
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
