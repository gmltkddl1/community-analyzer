<template>
  <div>
  <!--Charts-->
    <div class="row">
      <div class="col-12">
        <chart-card title="정보량"
                    sub-title="24 Hours performance"
                    :chart-data="usersChart.data"
                    :chart-options="usersChart.options">
          <span slot="footer">
            <i class="ti-reload"></i> Updated 3 minutes ago
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> 디씨인사이드
            <i class="fa fa-circle text-danger"></i> 오늘의유머
            <i class="fa fa-circle text-warning"></i> 일간베스트
          </div>
        </chart-card>
      </div>
      
      <div class="col-6">
        <card :title="table1.title" :subTitle="table1.subTitle">
          <div slot="raw-content" class="table-responsive">
            <paper-table type="hover" :title="table1.title" :sub-title="table1.subTitle" :data="table1.data"
                         :columns="table1.columns">

            </paper-table>
          </div>
        </card>
      </div>

      <div class="col-6">
        <card :title="table2.title" :subTitle="table2.subTitle">
          <div slot="raw-content" class="table-responsive">
            <paper-table type="hover" :title="table2.title" :sub-title="table2.subTitle" :data="table2.data"
                         :columns="table2.columns">

            </paper-table>
          </div>
        </card>
      </div>
    
    </div>
  
    <!--Stats cards
    <div class="row">
      <div class="col-md-6 col-xl-3" v-for="stats in statsCards" :key="stats.title">
        <stats-card>
          <div class="icon-big text-center" :class="`icon-${stats.type}`" slot="header">
            <i :class="stats.icon"></i>
          </div>
          <div class="numbers" slot="content">
            <p>{{stats.title}}</p>
            {{stats.value}}
          </div>
          <div class="stats" slot="footer">
            <i :class="stats.footerIcon"></i> {{stats.footerText}}
          </div>
        </stats-card>
      </div>
    </div>
    -->

    <!--Charts-->
    <div class="row">

    </div>

  </div>
</template>

<script>
import { StatsCard, ChartCard } from "@/components/index";
import Chartist from 'chartist';
import { PaperTable } from "@/components";
const tableColumns = ["순위", "키워드"];
const tableData1 = [
  {
    순위: 1,
    키워드: "검찰",
    
  },
  {
    순위: 2,
    키워드: "조국",
  },
  {
    순위: 3,
    키워드: "법무부",
    
  },
];
const tableData2 = [
  {
    순위: 1,
    키워드: "아이즈원",
    
  },
  {
    순위: 2,
    키워드: "프로미스나인",
  },
  {
    순위: 3,
    키워드: "주작",
    
  },
];
export default {

  components: {
    StatsCard,
    ChartCard,
    PaperTable
  },

  /**
   * Chart data used to render stats, charts. Should be replaced with server data
   */
  data() {
    return {
      table1: {
        title: "정치",
        subTitle: "",
        columns: [...tableColumns],
        data: [...tableData1]
      },
      table2: {
        title: "연예인",
        subTitle: "",
        columns: [...tableColumns],
        data: [...tableData2]
      },
      statsCards: [
        {
          type: "warning",
          icon: "ti-server",
          title: "Capacity",
          value: "105GB",
          footerText: "Updated now",
          footerIcon: "ti-reload"
        },
        {
          type: "success",
          icon: "ti-wallet",
          title: "Revenue",
          value: "$1,345",
          footerText: "Last day",
          footerIcon: "ti-calendar"
        },
        {
          type: "danger",
          icon: "ti-pulse",
          title: "Errors",
          value: "23",
          footerText: "In the last hour",
          footerIcon: "ti-timer"
        },
        {
          type: "info",
          icon: "ti-twitter-alt",
          title: "Followers",
          value: "+45",
          footerText: "Updated now",
          footerIcon: "ti-reload"
        }
      ],
      usersChart: {
        data: {
          labels: [
            "9:00AM",
            "12:00AM",
            "3:00PM",
            "6:00PM",
            "9:00PM",
            "12:00PM",
            "3:00AM",
            "6:00AM"
          ],
          series: [
            [287, 385, 490, 562, 594, 626, 698, 895, 952],
            [67, 152, 193, 240, 387, 435, 535, 642, 744],
            [23, 113, 67, 108, 190, 239, 307, 410, 410]
          ]
        },
        options: {
          low: 0,
          high: 1000,
          showArea: true,
          height: "245px",
          axisX: {
            showGrid: false
          },
          lineSmooth: Chartist.Interpolation.simple({
            divisor: 3
          }),
          showLine: true,
          showPoint: false
        }
      },
      activityChart: {
        data: {
          labels: [
            "Jan",
            "Feb",
            "Mar",
            "Apr",
            "Mai",
            "Jun",
            "Jul",
            "Aug",
            "Sep",
            "Oct",
            "Nov",
            "Dec"
          ],
          series: [
            [542, 543, 520, 680, 653, 753, 326, 434, 568, 610, 756, 895],
            [230, 293, 380, 480, 503, 553, 600, 664, 698, 710, 736, 795]
          ]
        },
        options: {
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },
      preferencesChart: {
        data: {
          labels: ["62%", "32%", "6%"],
          series: [62, 32, 6]
        },
        options: {}
      }
    };
  }
};
</script>
<style>
</style>
