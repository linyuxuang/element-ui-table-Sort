# element-ui-table-Sort
element ui table表格上添加序号


    我用的是vue脚手架，
      第一步：最开始的时候在data定义page
      第二步： 在序号列上加上:index="typeIndex" ，typeIndex是一个方法
      第三步： 在分页器上加上 :current-page="page" @current-change="table"
      第四步：typeindex方法内容
      第五步：在table方法里让this.page = val;其实val就是分页器上回调返回的页数，不知道的可以输出val看一下
      注意在分页上第一次加载数据的时候我们一般加上table(1);
 
 
       // 第一步
          export default{
            data(){
              return {
               page : 1;    
               }
            }

          }
      
      //第二步   这里v-bind:index = "typeIndex"
            <el-table-column
               type="index"
               :index="typeIndex"
               label="序号"
               width="150"
               align="center">
            </el-table-column>

        //第三步
          <div class="block" v-show="dataTotal>10">
              <el-pagination
                layout="total, prev, pager, next , jumper"
                :current-page="page"
                @current-change="table"
                :total="dataTotal">
              </el-pagination>
            </div>
        
          //第四步
           typeIndex(index) {
            return index + (this.page - 1) * 10 + 1;
          },   

      //第五步
         table(val){
            this.page = val;

          }     

      
      
        

