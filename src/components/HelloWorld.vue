<script>
import { ref } from 'vue'
import * as echarts from 'echarts';

export default{
  props: {
    msg: String
  }, 
  data(){
    return{
      greeting: "Testing!",
      count: 0,
      userInput: "",
      testId: "This is the test id."
    }
  },
  methods: {
    myFunctionClick: function () {
      this.$refs.myId.innerText = 'Hello Bro';
      // console.log(this.$refs.myId)
    }
  },
  mounted() {
    console.log(`the component is now mounted.`)
    let myChart = echarts.init(this.$refs.main);
    myChart.setOption({
    //   xAxis: {
    //     type: 'category',
    //     data: ['A', 'B', 'C']
    //   },
    //   yAxis: {
    //     type: 'value'
    //   },
    //   series: [
    //     {
    //       data: [120, 200, 150],
    //       type: 'line'
    //     }
    //   ]

      tooltip: {
        trigger: 'axis',
        axisPointer: { type: 'cross' }
      },
      legend: {},
      xAxis: [
        {
          type: 'category',
          axisTick: {
            alignWithLabel: true,
          },
          data: [
            'January',
            'February',
            'March',
            'April',
            'May',
            'June',
            'July',
            'August',
            'September',
            'October',
            'November',
            'December'
          ]
        }
      ],
      yAxis: [
        {
          type: 'value',
          name: 'Precipitation',
          min: 0,
          max: 300,
          position: 'right',
          axisLabel: {
            formatter: '{value} ml'
          },
          splitLine: {
            show: false
          },
          nameTextStyle: {
            align: "left"
          }
        },
        {
          type: 'value',
          name: 'Temp',
          min: 0,
          max: 25,
          position: 'left',
          axisLabel: {
            formatter: '{value} °C'
          },
          nameTextStyle: {
            align: "right"
          }
        },
        {
          type: 'value',
          name: 'Testing',
          min: 0,
          max: 12,
          position: 'left',
          axisLabel: {
            formatter: '{value} T'
          },
          splitLine: {
            show: false
          },
          offset: 60,
          axisLine: {
            show: true
          },
          nameTextStyle: {
            align: "right"
          }
        },
        {
          type: 'value',
          name: 'DT',
          min: 0,
          max: 30,
          position: 'right',
          axisLabel: {
            formatter: '{value} D',
          },
          splitLine: {
            show: false
          },
          offset: 60,
          axisLine: {
            show: true,
          },
          nameTextStyle: {
            align: "left"
          }, 
          
        },
        {
          type: 'value',
          name: 'FT',
          min: 0,
          max: 100,
          position: 'right',
          axisLabel: {
            formatter: '{value} F',
          },
          //the line
          splitLine: { 
            show: false
          },
          offset: 100,
          axisLine: {
            show: true,
          },
          nameTextStyle: {
            align: "left"
          },
          //the small label
          // axisPointer:{ 
          //   show: false
          // }
        }
      ],
      series: [
        {
          name: 'Precipitation',
          type: 'line',
          yAxisIndex: 0,
          data: [6, 32, 200, 86, 68.7, 100.7, 125.6, 112.2, 78.7, 48.8, 36.0, 19.3]
        },
        {
          name: 'Temp',
          type: 'line',
          smooth: true,
          yAxisIndex: 1,
          data: [
            6.0,
            10.2,
            10.3,
            11.5,
            10.3,
            13.2,
            14.3,
            16.4,
            18.0,
            16.5,
            12.0,
            5.2
          ]
        },
        {
          name: 'Testing',
          type: 'line',
          yAxisIndex: 1,
          data: [
            1.0,
            2.0,
            3.0,
            4.0,
            5.0,
            13.0,
            7.0,
            8.0,
            9.0,
            1.0,
            11.0,
            12.0
          ]
        },
        {
          name: 'DT',
          type: 'line',
          yAxisIndex: 1,
          data: [
            20.0,
            4.0,
            6.0,
            10.0,
            20.0,
            13.0,
            7.0,
            17.0,
            9.0,
            15.0,
            11.0,
            20.0
          ]
        },
        {
          name: 'FT',
          type: 'line',
          yAxisIndex: 4,
          data: [
            10.0,
            40.0,
            60.0,
            10.0,
            25.0,
            100.0,
            70.0,
            17.0,
            3.0,
            35.0,
            55.0,
            50.0
          ]
        }
      ]
    });
  }
}



// Draw the chart



</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>
  <div>{{greeting}}</div>

  <input v-model="userInput" />
  <div id="displayUserInput">
    
    <p>The user input will be display in here: {{userInput}}</p>
  </div>
  <div id="testId">{{testId}}</div>

  <div ref="myId">the ref</div>
  <button @click="myFunctionClick()">Click Here</button>
  <div ref="main" style="width: 100%;height:400px;">test</div>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
