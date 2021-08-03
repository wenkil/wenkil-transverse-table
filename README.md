## INSTALL
npm i wenkil-transverse-table

## 效果展示
![image](https://user-images.githubusercontent.com/48345586/127952584-0db67fdf-d7b8-4c37-a66a-b1efad7f344d.png)

![image](https://user-images.githubusercontent.com/48345586/127952594-d01bb6e5-9d4e-4206-8567-acb186666d7e.png)


## DEMO

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

我的github地址 https://github.com/wenkil 欢迎指点
