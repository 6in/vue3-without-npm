<template>
  <table>
    <tr v-for="row in rows" :key="row[0]">
      <td>{{ row[0] }}</td>
      <td>{{ row[1] }}</td>
      <td>{{ row[2] }}</td>
      <td>{{ row[3] }}</td>
      <td>{{ row[4] }}</td>
    </tr>
  </table>
</template>

<script>
var data = [
  [1, false, "S0001", "りんご", 100, "青森産"],
  [2, false, "S0002", "みかん", 80, "静岡産"],
  [3, false, "S0003", "メロン", 1000, "袋井クラウンメロン"],
];

export default {
  components: {
    HotTable: Handsontable.vue.HotTable,
  },
  data() {
    return {
      rows: data,
    };
  },
};
</script>