<template>
    <div class="row">
      <div class="col-12">
        <card :title="table1.title" :subTitle="table1.subTitle">
          <div slot="raw-content" class="table-responsive">
            <paper-table :data="table1.data" :columns="table1.columns">

            </paper-table>
          </div>
        </card>
      </div>

      <div class="col-12">
        <card :title="table2.title" :subTitle="table2.subTitle">
          <div class="table-full-width table-responsive">
            <paper-table type="hover" :title="table2.title" :sub-title="table2.subTitle" :data="table2.data"
                         :columns="table2.columns">

            </paper-table>
          </div>
        </card>
      </div>

    </div>
</template>
<script>
import { PaperTable } from "@/components";
import axios from 'axios';

const tableColumns = ["순위", "제목", "사이트명", "추천수", "조회수"];

export default {
  components: {
    PaperTable
  },

  data() {
    return {
      table1: {
        title: "정치",
        subTitle: "",
        columns: [...tableColumns],
        data: []
      },
      table2: {
        title: "연예인",
        subTitle: "",
        columns: [...tableColumns],
        data: []
      },
      tableData:[]

    };
  },
  mounted: function(){
    
    const self = this;

    axios
      .get("/'정치사회'.json")
      .then(function(res){ 
        self.table1.data = res.data.정치사회
        self.tableData=res.data
        console.log(self.tableData);
      })
      .catch(function(err){
        console.error('으앙 터짐..');
        console.error(err);
      });
    axios
      .get("/'연예인'.json")
      .then(function(res){ 
        self.table2.data = res.data.연예인
        self.tableData=res.data
        console.log(self.tableData);
      })
      .catch(function(err){
        console.error('으앙 터짐..');
        console.error(err);
      });
  }
};
</script>
<style>
</style>
