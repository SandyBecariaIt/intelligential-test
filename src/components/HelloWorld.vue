<template>
  <div class="hello">
    <div v-for="(item, index) in item" :key="index">
      <p>{{ item }}</p>
    </div>
    <p>Resultado: {{ seconArray }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  
  data() {
    return {
      i: 0,
      seconArray: [],
      item: [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
      ]
    }
  },

  mounted() {
     this.getSidebar();
  },

  methods: {
    getSidebar() {
      var count = 0;
      var colums = 0;
      var rows = this.item.length;

      this.getTop(count, colums, rows);
      this.getRight(count, colums, rows);
      this.getLeft(count, colums, rows);
      this.getBottom(count, colums, rows);
    },
    getTop(count, colums, rows) {
      for (count = colums; count < rows; count++) {
        this.seconArray[this.i] = this.item[colums][count];
        this.i ++;
      }
    },
    getRight(count, colums, rows) {
      for (count = colums + 1; count < rows; count++) {
        this.seconArray[this.i] = this.item[count][rows-1];
        this.i ++;
      }
    },
    getLeft(count, colums, rows) {
      for (count = rows - 2; count >= 0; count--) {
        this.seconArray[this.i] = this.item[rows-1][count];
        this.i ++;
      }
    },
    getBottom(count, colums, rows) {
      for (count = colums; count < rows-1 ; count ++) {
        this.seconArray[this.i] = this.item[rows - 2][count];
        this.i ++;
      }
    }
  }
}
</script>
