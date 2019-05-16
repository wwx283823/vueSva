<template>
  　　<div id="svaConfig">
  <div class="row">
    <div class="col-lg-12">
      <div class="panel panel-success">
        <div class="panel-heading">
          SVA配置
        </div>
        <div class="panel-body">
          <div class="row">
            <form role="form">
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">站点名称:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.siteName" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">用户名:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.userName" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">SVA名称:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.svaName" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">密码:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.myWorld" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">IP:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.ip" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">订阅类型:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.dataType" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">Token端口号:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.tokenPort" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">ID类型:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.idType" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">Broken端口号:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.brokenPort" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="form-group">
                  <div class="col-lg-3" style="text-align: right;">
                    <label style="padding-top: 6px">状态:</label>
                  </div>
                  <div class="col-lg-7">
                    <input v-model="svaModel.status" class="form-control">
                  </div>
                </div>
              </div>
              <div class="col-lg-12">
                <div class="form-group">
                  <div class="col-lg-12" style="text-align: center;">
                    <button @click="svaConfirm"  class="btn btn-primary">确定</button>
                  </div>

                </div>

              </div>
            </form>
            <!-- /.col-lg-6 (nested) -->
          </div>
          <!-- /.row (nested) -->
        </div>
        <div class="panel-footer">

        </div>
        <div class="panel panel-default">
          <div class="panel-heading">
            SVA信息列表
          </div>
          <div class="panel-body">
            <div class="table-responsive">
              <v-table
                is-vertical-resize
                style="width:100%"
                is-horizontal-resize
                :vertical-resize-offset='55'
                :min-height='150'
                :columns="columns"
                :table-data="myTableData"
                :column-cell-class-name="columnCellClass2"
                row-hover-color="#eee"
                row-click-color="#edf7ff"
                :cell-edit-done="cellEditDone"
                @on-custom-comp="customCompFunc"
              ></v-table>
            </div>
          </div>
        </div>
      </div>
      <!-- /.panel -->
    </div>
    <!-- /.col-lg-12 -->
  </div>
  　　</div>
</template>
<style >


  @import '../../static/css/app.css';
</style>
<script type="text/javascript">
  import axios from 'axios'
  import Vue from 'vue'
  export default {
//    inject:['reload'],
    data() {
      return {
        svaModel:{
          siteName:'',
          id:'',
          svaName:'',
          ip:'',
          tokenPort:'',
          brokenPort:'',
          userName:'',
          myWorld:'',
          dataType:'',
          idType:'',
          status:''
        },
        myTableData:[],
        columns: [
//          {field: 'id',show:false},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'name', title: '站点名称',isEdit:true, width:120,titleAlign: 'center',titleCellClassName:'title-cell-class-name-test',columnAlign: 'center',isResize:true},
          {field: 'createTime', title: '创建时间',width:150, titleAlign: 'center', columnAlign: 'center',isResize:true},
          {field: 'updateTime', title: '修改时间',width:150, titleAlign: 'center', columnAlign: 'center',isResize:true},
          {field: 'custome-adv', title: '操作',width: 100, titleAlign: 'center',columnAlign:'center',componentName:'table-operation',isResize:true}

        ]
      }
    },
    methods:{
      svaConfirm(){
        let _this = this;
        let formData = new FormData();
        formData.append('name', this.svaModel.name);
        formData.append('id', this.svaModel.id);
//        _this.reload();
        axios.post('/api/saveSiteInfo', formData).then(function (response) {
          if (response.status === 200) {
            _this.getSiteInfo();
            _this.svaModel.name = "";
          }
        })
      },
      deleteData(id){
        let myParam = {'id':id};
        let _this = this;
        axios.get('/api/deleteSiteInfoById',{
          params:
          myParam
        }).
        then(function(response){
          _this.getSiteInfo();
        }).catch(function(err){
          console.log(err);
        });
      },
      customCompFunc(params) {

        console.log(params);

        if (params.type === 'delete') { // do delete operation
          this.deleteData(params[id]);
        } else if (params.type === 'edit') { // do edit operation
          this.svaModel.name = params.rowData['name'];
          this.svaModel.id = params[id];
        }

      },
      getSiteInfo(){
        let _this = this;
        let sz = {'id':21,'name':'测试','createTime':'2018-03-05 18:32:34','updateTime':'2018-03-05 18:32:34'};
        _this.myTableData.push(sz);
//        axios.get('/api/getSiteInfo').
//        then(function(response){
//          _this.myTableData = response.data;
//        }).catch(function(err){
//          console.log(err);
//        });
      },
      columnCellClass2(rowIndex,columnName,rowData){
        return 'column-cell-class-name-test';
      },
      cellEditDone(newValue,oldValue,rowIndex,rowData,field){

        this.myTableData[rowIndex][field] = newValue;
        this.svaModel.id = this.myTableData[rowIndex]['id'];
        this.svaConfirm();
        // 接下来处理你的业务逻辑，数据持久化等...
      }
    },
    created(){
      this.getSiteInfo();
    },
    mounted(){
//      this.getParam();
    },
  }
  // 自定义列组件
  Vue.component('table-operation',{
    template:`<span>
        <a href="" @click.stop.prevent="update(rowData,index)">编辑</a>&nbsp;
        <a href="" @click.stop.prevent="deleteRow(rowData,index)">删除</a>
        </span>`,
    props:{
      rowData:{
        type:Object
      },
      field:{
        type:String
      },
      index:{
        type:Number
      }
    },
    methods:{
      update(){
        // 参数根据业务场景随意构造
        let params = {type:'edit',id:this.rowData.id,rowData:this.rowData};
        this.$emit('on-custom-comp',params);
      },

      deleteRow(){
        // 参数根据业务场景随意构造
        let params = {type:'delete',id:this.rowData.id};
        this.$emit('on-custom-comp',params);

      }
    }
  })
</script>

<style>
</style>
