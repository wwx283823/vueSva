<template>
　　<div id="mapConfig">
     <div class="row">
      <div class="col-lg-12">
        <div class="panel panel-success">
          <div class="panel-heading">
            地图配置
          </div>
          <div class="panel-body">
            <div class="row">
              <form role="form">
                <div class="col-lg-6">
                    <div class="form-group">
                      <div class="col-lg-4">
                        <label>Text Input</label>
                      </div>
                      <div class="col-lg-8">
                        <input class="form-control">
                      </div>

                    </div>
                    <div class="form-group">
                      <label>File input</label>
                      <input type="file">
                    </div>
                    <button type="submit" class="btn btn-default">Submit Button</button>
                    <button type="reset" class="btn btn-default">Reset Button</button>
                </div>
                <div class="col-lg-6">
                  <div class="form-group">
                    <div class="col-lg-4">
                      <label>Text Input</label>
                    </div>
                    <div class="col-lg-8">
                      <input class="form-control">
                    </div>

                  </div>
                  <div class="form-group">
                    <label>File input</label>
                    <input type="file">
                  </div>
                  <button type="submit" class="btn btn-default">Submit Button</button>
                  <button type="reset" class="btn btn-default">Reset Button</button>
                </div>
              </form>
              <!-- /.col-lg-6 (nested) -->
            </div>
            <!-- /.row (nested) -->
          </div>
          <div class="panel-footer">
            Panel Footer
          </div>
          <div class="panel panel-default">
            <div class="panel-heading">
              Responsive Table Example
            </div>
            <div class="panel-body">
              <div class="table-responsive">
                <table class="table table-striped table-bordered table-hover">
                  <thead>
                  <tr>
                    <th>S No.</th>
                    <th>First Name</th>
                    <th>Last Name</th>
                    <th>User Name</th>
                    <th>Email ID.</th>
                  </tr>
                  </thead>
                  <tbody>
                  <tr>
                    <td>1</td>
                    <td>John</td>
                    <td>Doe</td>
                    <td>John15482</td>
                    <td>name@site.com</td>
                  </tr>
                  <tr>
                    <td>2</td>
                    <td>Kimsila</td>
                    <td>Marriye</td>
                    <td>Kim1425</td>
                    <td>name@site.com</td>
                  </tr>
                  <tr>
                    <td>3</td>
                    <td>Rossye</td>
                    <td>Nermal</td>
                    <td>Rossy1245</td>
                    <td>name@site.com</td>
                  </tr>
                  <tr>
                    <td>4</td>
                    <td>Richard</td>
                    <td>Orieal</td>
                    <td>Rich5685</td>
                    <td>name@site.com</td>
                  </tr>
                  <tr>
                    <td>5</td>
                    <td>Jacob</td>
                    <td>Hielsar</td>
                    <td>Jac4587</td>
                    <td>name@site.com</td>
                  </tr>
                  <tr>
                    <td>6</td>
                    <td>Wrapel</td>
                    <td>Dere</td>
                    <td>Wrap4585</td>
                    <td>name@site.com</td>
                  </tr>

                  </tbody>
                </table>
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
