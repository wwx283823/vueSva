<template>
　　<div id="mapConfig">
      <div class="container-fluid">
        <div class="row" style="margin-top: 40px;">

          <form>
            <input type="text" value=""  placeholder="请输入用户名">
            <input type="text" value=""  placeholder="请输入年龄">
            <input type="file" @change="getFile($event)">
            <button @click="submitForm($event)">提交</button>
          </form>
        </div>

      </div>
　　</div>
</template>
<style >


  @import '../../static/css/app.css';
</style>
<script type="text/javascript">
  import axios from 'axios'
  export default {
    data() {
      return {

      }
    },
    methods:{
      columnCellClass2(rowIndex,columnName,rowData){

          return 'column-cell-class-name-test';

      },
      update(e){
        let file = e.target.files[0];
        let param = new FormData(); //创建form对象
        param.append('file',file);//通过append向form对象添加数据
        console.log(param.get('file')); //FormData私有类对象，访问不到，可以通过get判断值是否传进去
        let config = {
          headers:{'Content-Type':'multipart/form-data'}
        }; //添加请求头
        this.$http.post('http://127.0.0.1:8081/upload',param,config)
          .then(response=>{
            console.log(response.data);
          })
      },
      getFile(event) {
        this.file = event.target.files[0];
        console.log(this.file);
      },
      submitForm(event) {
        event.preventDefault();
        let formData = new FormData();
        formData.append('name', this.name);
        formData.append('age', this.age);
        formData.append('file', this.file);

        let config = {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        }

        axios.post('/api/upload', formData, config).then(function (response) {
          if (response.status === 200) {
            console.log(response.data);
          }
        })
      }
    },
    created(){
//      this.getWirelessInfos();
    },
    mounted(){
//      this.getParam();
    },
  }

</script>

<style>
</style>
