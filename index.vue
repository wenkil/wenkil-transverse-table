<template>
  <div>
    <el-table
      border
      :data="tableList"
      :show-header="false"
      :cell-style="cellStyle"
    >
      <el-table-column
        min-width="50"
        v-for="item in headList"
        :key="item.prop"
        :label="item.prop"
        :prop="item.prop"
        align="center"
      >
        <template slot-scope="{ row }">
          <span>{{ row[item.prop] }}</span>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  import Element from "element-ui";
  export default {
    props: {
      tableData: { //传进key value格式的数组
        type: Array,
        default: () => {
          return []
        }
      },
      columnNum: {
        type: Number,
        default: 6
      }
    },

    data() {
      return {
        tableList: [],
        headList: [],
      }
    },
    created() {

    },
    mounted() {

    },
    methods: {
      setTable() {
        this.tableList = []
        this.headList = []
        for (let i = 0; i < this.columnNum; i++) {
          this.headList.push(
            {prop: 'key' + (i + 1)},
            {prop: 'value' + (i + 1)}
          )
        }

        var newArr = [];

        for (var i = 0; i < this.tableData.length; i += this.columnNum) {
          let temp = this.tableData.slice(i, i + this.columnNum)
          if (temp.length < this.columnNum) {
            let d = temp.length
            for (let i = 0; i < this.columnNum - d; i++) {
              temp.push({
                key:undefined,
                value:undefined
              })
            }
          }
          newArr.push(temp);
        }

        let tempArr = []
        for (let i = 0; i < newArr.length; i++) {
          let index = 1
          let temp = {}
          for (let item of newArr[i]) {
            temp['key' + index] = item.key
            temp['value' + index] = item.value
            index++
          }
          tempArr.push(temp)
        }

        this.tableList = tempArr
      },

      cellStyle({row, column, rowIndex, columnIndex}) {
        if (row[column.property] != 0 && !row[column.property]) {
          return {
            visibility: 'hidden'
          }
        }
        if (columnIndex % 2 == 0) {
          return {
            background: '#f0f0f0'
          }
        }
      }
    },
  }
</script>

<style scoped>
  /deep/ .el-table--group::after, .el-table--border::after, .el-table::before {
    width: 0;
    border: none !important;
    background-color: transparent !important;
  }
</style>
