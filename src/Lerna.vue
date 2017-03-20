<template>
  <div id="app">
    hello <el-button>world</el-button>
    <v-button @click.native="hello">vbutton</v-button>
    <div style="width:218px;margin:0 auto;">
      <v-date-picker style="width: 218px"></v-date-picker>
    </div>
    <div>
      <v-dropdown>
        <div>
          点击显示菜单 <icon type="down"></icon>
        </div>
        <ul slot="dropdown-menu">
          <li><a>选项一</a></li>
          <li><a>选项二</a></li>
          <li><a>选项三</a></li>
          <li role="separator" class="atui-dropdown-divider"></li>
          <li><a href="#">其它</a></li>
        </ul>
      </v-dropdown>
    </div>
    <div style="width:800px;margin:20px auto;">
      <v-table :data-source="gridData" :columns="gridColumns" row-key="key" :pagination="pagination"></v-table>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import elButton from 'element-ui/lib/button';
// import sugarBoy from 'sugarboy';
// import vSelect from 'sugarboy/lib/select';
// import { select as vSelect } from 'sugarboy';
// import atui from 'atui';
import vButton from 'atui/lib/button';
import vDatePicker from 'atui/lib/date-picker';
import vDropdown from 'atui/lib/dropdown';
import vIcon from 'atui/lib/icon';
import vTable from 'atui/lib/table';
import 'atui/dist/greater-blue.css';


// import sugarSelect from 'sugar-select';

// const vButton = atui.Button;
Vue.component(elButton.name, elButton);
Vue.component(vButton.name, vButton);
Vue.component(vDatePicker.name, vDatePicker);
Vue.component(vDropdown.name, vDropdown);
Vue.component(vIcon.name, vIcon);

var columns = [{
  title: '姓名',
  dataIndex: 'name',
  filters: [{
    text: '姓李的的',
    value: '李',
  }, {
    text: '姓胡的',
    value: '胡',
  }],
  sorter:true,
  width:150
}, {
  title: '年龄',
  dataIndex: 'age',
  sorter: function(a, b) { return a.age - b.age },
  render: function(text, record, index) {
    return '<input v-model="gridData['+ index +'].age"/>'
  },
  width:250
}, {
  title: '地址',
  dataIndex: 'address',
  filters: [{
    text: '南湖',
    value: '南湖',
  }, {
    text: '西湖',
    value: '西湖',
  }],
  filterMultiple: false,
  width:250

},{
    title: '操作',
    key: 'operation',
    render: function(text, record) {
      if(record) {
        return '<icon type="info-s"></icon><a href="'+ record.key+'.html" target="_blank">详情</a>'
      }
    }
  }
]

const data = [];
for (let i = 0; i < 46; i++) {
  data.push({
    key: i,
    name: `李大嘴${i}`,
    age: 32,
    address: `西湖区湖底公园${i}号`,
  });
}

const pagination = {
  total: data.length,
  pageSize: 20
}

// 配置选择数据的选项
var rowSelection = {
  getCheckboxProps: function(record) {
    return {
      disabled: record.name === '胡彦祖'    // 配置无法勾选的列
    };
  },
  onChange: function(selectedRowKeys, selectedRows) {
    console.log('rowSelection.onChange',selectedRowKeys, selectedRows);
  },
  onSelect: function(record, selected, selectedRows) {
    console.log('rowSelection.onSelect',record, selected, selectedRows);
  },
  onSelectAll: function(selected, selectedRows, changeRows) {
    console.log('rowSelection.onSelectAll',selected, selectedRows, changeRows);
  }
};

export default {
  name: 'app',
  components: {
    elButton,
    vButton,
    vDatePicker,
    vDropdown,
    vIcon,
    vTable,
  },
  data() {
    return {
      gridData: data,
      gridColumns: columns,
      pagination: pagination,
    }
  },
  mounted() {
    console.log('------');
    // console.log(vSelect);
    // console.log(vSelect.echo());
    // console.log(sugarBoy);
    // console.log(vButton);
    console.log(vButton);
  },
  methods: {
    hello() {
      console.log('hello');
    },
  },
};
</script>

<style>
body {
  font-size: 14px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul {
  -webkit-margin-before: 0;
  -webkit-margin-after: 0;
  -webkit-padding-start: 0;
}
li {
  list-style: none;
}
</style>
