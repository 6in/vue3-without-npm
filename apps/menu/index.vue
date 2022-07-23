<template>
  <div v-if="true">
    <hot-table ref="table" :root="root" :settings="hotSettings"></hot-table>
    <Calendar v-model="value" />
  </div>
</template>

<script>

export default {
  components: {
    HotTable: Handsontable.vue.HotTable,
    Calendar: primevue.calendar
  },
  mounted() {
    const vm = this
    debugger
    fetch("./data/test.json").then(res => res.json()).then(json => {
      vm.$refs.table.hotInstance.loadData(json)
    })
  },
  data() {
    return {
      value: "",
      root: "testHot",
      hotSettings: {
        data: [],
        colHeaders: ["編集", "選択", "商品CD", "商品名", "単価", "備考"],
        columns: [
          { readOnly: true, type: "text" },
          { type: "checkbox" },
          { type: "text", width: 80 },
          { type: "text", width: 200, className: "htLeft htMiddle" },
          {
            type: "numeric",
            numericFormat: { pattern: "0,00", culture: "ja-JP" },
          },
          { type: "text", width: 300, className: "htLeft htMiddle" },
        ],
        enterMoves: { row: 0, col: 1 },
        outsideClickDeselects: true,
        manualColumnResize: true,
        fillHandle: false,
        licenseKey: "non-commercial-and-evaluation",
      },
    };
  },
};
</script>