<template>
  <div>
    <v-button @click.native="onBtnClick">button</v-button>
    <v-row>
      <v-col span="23">col-23</v-col>
      <v-col span="1">1</v-col>
    </v-row>
    <v-table :data-source="dataSource" :columns="columns">
      <div slot="noDataTip">if dataSource is null, i will displayed</div>
      <template scope="props" :slot="age">
        <span>年龄：{{props.record.age}}</span>
      </template>
      <template scope="props" :slot="operation">
        <v-button @click.native="onOperate(props.record)">操作</v-button>
      </template>
    </v-table>
  </div>
</template>
<script>
  import Vue from 'vue'
  import atui from 'atui'
  import 'atui/dist/greater-blue.css'

  console.log(atui)
  // 全局注册atui组件
  Vue.use(atui)

  // table配置
  const dataSource = [{
    key: '1',
    name: '胡彦斌',
    age: 32,
    address: '西湖区湖底公园1号'
  }, {
    key: '2',
    name: '胡彦祖',
    age: 42,
    address: '西湖区湖底公园1号'
  }];

  const columns = [{
    title: '姓名',
    dataIndex: 'name',
    key: 'name',
  }, {
    title: '年龄',
    dataIndex: 'age',
    key: 'age',
  }, {
    title: '住址',
    dataIndex: 'address',
    key: 'address',
  },{
    title: '操作',
    key: 'operation'
  }];


  export default{
    components: {
      
    },
    data() {
      return {
        dataSource: dataSource,
        columns: columns
      }
    },
    methods: {
      onBtnClick () {
        alert(1)
      },
      onOperate (record) {
        alert('您点击了:'+record.name)
        console.log(record)
      }
    }
  }
</script>

<style type="text/css">
  body {
    padding: 20px;
  }
</style>