<template>
  <div>
    <v-button @click.native="onBtnClick">button</v-button>
    <v-row>
      <v-col span="23">col-23</v-col>
      <v-col span="1">1</v-col>
    </v-row>
    <v-table :data-source="dataSource" :columns="columns" @row-click="onRowClick">
      <div slot="noDataTip">if dataSource is null, i will displayed</div>
      <template scope="props" slot="age">
        <span>年龄：{{props.record.age}}</span>
      </template>
      <template scope="props" slot="operation">
        <v-button @click.native="onOperate(props.record)">操作</v-button>
      </template>
    </v-table>
    <v-row>
      <v-col span="6">
        <v-menu @click.native="onMenuClick" v-model="menuData"></v-menu>
      </v-col>
    </v-row>
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
        columns: columns,
        menuData: [
          {
            type: 'SubMenu',
            uuid: 'sub1',
            title: '导航一',
            show: true, // 是否展开SubMenu
            children: [
              {
                type: 'MenuItemGroup',
                title: '分组1',
                uuid: 'sub1',
                children: [
                  {
                    type: 'MenuItem',
                    uuid: '1',
                    content: '<a href="//github.com/aliqin/atui">选项1</a>'
                  },
                  {
                    type: 'MenuItem',
                    uuid: '2',
                    selected: true, // 是否选中该菜单项
                    content: '选项2'
                  }
                ]
              },
              {
                type: 'MenuItemGroup',
                title: '分组2',
                uuid: 'sub2',
                children: [
                  {
                    type: 'MenuItem',
                    uuid: '3',
                    content: '选项3'
                  },
                  {
                    type: 'MenuItem',
                    uuid: '4',
                    content: '选项4'
                  }
                ]
              }
            ]
          },
          {
            type: 'SubMenu',
            title: '导航二',
            uuid: 'sub2',
            children: [
              {
                type: 'MenuItem',
                uuid: '5',
                content: '选项5'
              },
              {
                type: 'MenuItem',
                uuid: '6',
                content: '选项6'
              },
              {
                type: 'SubMenu',
                uuid: 'sub3',
                title: '三级导航',
                children: [
                  {
                    type: 'MenuItem',
                    uuid: '7',
                    content: '选项7'
                  },
                  {
                    type: 'MenuItem',
                    uuid: '8',
                    content: '选项8'
                  }
                ]
              }
            ]
          }
        ]
      }
    },
    methods: {
      onBtnClick () {
        alert(1)
      },
      onOperate (record) {
        alert('您点击了:'+record.name)
        console.log(record)
      },
      onMenuClick () {
        console.log(arguments)
      },
      onRowClick (rowIndex,record) {
        console.log(rowIndex,record)
      }
    }
  }
</script>

<style type="text/css">
  body {
    padding: 20px;
  }
</style>