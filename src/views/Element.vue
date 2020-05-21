<template>
  <div>
    <h1>This is an element page</h1>
    <el-table :data="tableData">
      <el-table-column prop="date" label="Date" width="140"></el-table-column>
      <el-table-column prop="name" label="Name" width="120"></el-table-column>
      <el-table-column prop="age" label="Age" width="120"></el-table-column>
      <el-table-column prop="address" label="Address"></el-table-column>
    </el-table>
    <el-backtop></el-backtop>

    <el-button @click="drawer = true" type="primary">点我打开</el-button>
    <el-drawer
      title="我是标题"
      size="50%"
      :visible.sync="drawer"
      :before-close="handleClose">
      <span>我来啦!</span>
    </el-drawer>
  </div>
</template>
<script lang="ts">
  import { Component, Vue } from "vue-property-decorator";
  export default Vue.extend({
    data() {
      let isDone:Boolean = false;
      isDone = true;
      let number:Number = 213;
      let str:String = "test";
      let test:void= undefined;
      let str1:any = "test1";
      str1 = 123;

      interface Person {
        readonly id:number;
        date:String;
        name:String;
        age:Number;
        address?:String;
        [propName: string]: any;
      }
      const item:Person = {
        id:1001,
        date: '2016-05-02',
        name: 'Tom',
        age: 18,
        address:'address'
      };

      let arr: any[] = [1,'2',3,4,5];
      let arr1: Array<string> = ['233','213','2131213'];

      
      return {
        tableData: Array(20).fill(item),
        drawer: false,
      }
    },
    methods:{
      testFun1(address:String | Number = 'this is test'):String {
        return address.toString();
      },
      testFun():void {
        console.log(123);
      },
      handleClose(done:any):void {
        this.$confirm('确认关闭？')
          .then(_ => {
            done();
            console.log(this.testFun1(123));
          })
          .catch(_ => {});
      }
    }
  });
</script>
