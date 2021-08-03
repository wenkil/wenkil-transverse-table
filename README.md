## INSTALL
npm i wenkil-transverse-table

## demo
```
<template>
  <div class="app-container">
    <TransverseTable ref="transverseTable" :columnNum='4' :tableData="[
            {key:'test',value: 1},
            {key:'test',value: 1},
            {key:'test',value: 1},
            {key:'test',value: 1},
            {key:'test',value: 1},
            {key:'test',value: 1},
    ]"></TransverseTable>
  </div>
</template>


<script>
  import TransverseTable from 'wenkil-transverse-table'
  export default {
    components: {TransverseTable},
    data() {
      return {}
    },
    created() {},
    mounted() {
      this.$refs.transverseTable.setTable()
    },
    methods: {},
  }
</script>
```
在父组件里,动态获取数据时需要调用下this.$refs.transverseTable.setTable() 来渲染数据

columnNum为 列数，默认为6,可以根据需求传如你想要展示的列数
tableData为 Key Value 格式的数组

