<script>
export default {
    data() {
      return {
        search:{
          slot:''
        },
        data: [
          {
            name:'张三',
            sex:'男',
            date:'2018-08-08',
            time:'13:00:00'
          }, {
            name:'李四',
            sex:'女',
            date:'2018-08-09',
            time:'13:00:00'
          }
        ],
        option:{
          page:false,
          align:'center',
          menuAlign:'center',
          column:[
             {
              label:'姓名',
              prop:'name',
              search:true,
            },
            {
              label:'性别',
              prop:'sex',
              search:true,
            }
          ]
        },
         option1:{
          page:false,
          align:'center',
          menuAlign:'center',
          column:[
             {
              label:'姓名',
              prop:'name',
            },
            {
              label:'性别',
              prop:'sex',
            },
            {
              label:'日期',
              prop:'date',
              type:'date',
              more:true,
              search:true,
            },
            {
              label:'时间',
              prop:'time',
              type:'time',
              more:true,
              search:true,
            },
          ]
        },
      };
    },
    methods: {
      searchChange1(params){
        this.$message.success('搜索数据'+ JSON.stringify(Object.assign(params,this.search)));
      },
      searchChange(params){
        this.$message.success('搜索数据'+ JSON.stringify(params));
      },
      searchReset1(){
        this.search={};
        this.$message.success('清空回调')
      }
    }
}
</script>

<style>

</style>

## Crud 模块



### 搜索

:::demo  配置`cloumn`数组对象中的`search`属性为`true`时，即可激活该字段的搜索功能，点击搜索功能回调`search-change`方法，返回搜索的参数`
```html
<avue-crud :data="data" :option="option"  @search-change="searchChange"></avue-crud>

<script>
export default {
    data() {
      return {
        data: [
          {
            name:'张三',
            sex:'男',
            date:'2018-08-08',
            time:'13:00:00'
          }, {
            name:'李四',
            sex:'女',
            date:'2018-08-09',
            time:'13:00:00'
          }
        ],
        option:{
          page:false,
          align:'center',
          menuAlign:'center',
          column:[
             {
              label:'姓名',
              prop:'name',
              search:true,
            },
            {
              label:'性别',
              prop:'sex',
              search:true,
            }
          ]
        },
      };
    },
    methods: {
      searchChange(params){
        this.$message.success('搜索数据'+ JSON.stringify(params));
      },
    }
}
</script>
```
:::


### 日期和时间范围

:::demo  配置`more`为`true`时， `type`为`time`、`date`、`datetime`控件时他们全部变成范围筛选
```html
<avue-crud :data="data" :option="option1"  @search-change="searchChange"></avue-crud>

<script>
export default {
    data() {
      return {
        data: [
          {
            name:'张三',
            sex:'男',
            date:'2018-08-08',
            time:'13:00:00'
          }, {
            name:'李四',
            sex:'女',
            date:'2018-08-09',
            time:'13:00:00'
          }
        ],
       option1:{
          page:false,
          align:'center',
          menuAlign:'center',
          column:[
             {
              label:'姓名',
              prop:'name',
            },
            {
              label:'性别',
              prop:'sex',
            },
            {
              label:'日期',
              prop:'date',
              type:'date',
              more:true,
              search:true,
            },
            {
              label:'时间',
              prop:'time',
              type:'time',
              more:true,
              search:true,
            },
          ]
        },
      };
    },
    methods: {
      searchChange(params){
        this.$message.success('搜索数据'+ JSON.stringify(params));
      },
    }
}
</script>
```
:::


### 自定义内容

:::demo  设置卡槽名字为`search`即可，一定要加`el-form-item`否则格式排版会出问题，目前的排版为一次追加，不够的排到下一行，如果要清空数据，需要在`search-reset`回调中手动清空你自定义的数据
```html
<avue-crud :data="data" :option="option" @search-reset="searchReset1" @search-change="searchChange1">
  <template slot="search">
    <el-form-item label="自定义">
      <el-input v-model="search.slot" placeholder="自定义搜索" size="small"/>
    </el-form-item>
  </template>
</avue-crud>

<script>
export default {
    data() {
      return {
        search:{
          slot:''
        },
        data: [
          {
            name:'张三',
            sex:'男',
            date:'2018-08-08',
            time:'13:00:00'
          }, {
            name:'李四',
            sex:'女',
            date:'2018-08-09',
            time:'13:00:00'
          }
        ],
        option:{
          page:false,
          align:'center',
          menuAlign:'center',
          column:[
             {
              label:'姓名',
              prop:'name',
              search:true,
            },
            {
              label:'性别',
              prop:'sex',
              search:true,
            }
          ]
        },
      };
    },
    methods: {
      searchChange1(params){
        this.$message.success('搜索数据'+ JSON.stringify(Object.assign(params,this.search)));
      },
      searchReset1(){
        this.search={};
        this.$message.success('清空回调')
      }
    }
}
</script>
```
:::