<template>

  <div>

    <div class=" bg-white py-8 pl-20">
        <div class="ml-[80px]">
        <h2 class="text-4xl">PieCloud</h2>
        <p>Status: 100% [All operation]</p>
    </div>
    </div>
    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <div class="flex my-4 h-[80px] w-[1200px] bg-white overflow-hidden  sm:rounded-lg">
          <div
            class="flex justify-center items-center my-4 mx-2  h-[50px] w-[120px]  sm:rounded-lg"
          >
          <div class="button" :class="{ active: activeButton === 'stats' }" @click="toggleButton('stats')">Stats</div>
          </div>
          <div class="flex justify-center items-center my-4 mx-2 h-[50px] w-[120px] sm:rounded-lg">
            <div class="button" :class="{ active: activeButton === 'tasks' }" @click="toggleButton('tasks')">Tasks</div>
          </div>
          <div class="flex justify-center items-center my-4 mx-2 h-[50px] w-[120px] sm:rounded-lg">

            <div class="button" :class="{ active: activeButton === 'support' }" @click="toggleButton('support')">Support</div>
          </div>
          <div class="flex justify-center items-center my-4 mx-2 h-[50px] w-[120px] sm:rounded-lg">

            <div class="button" :class="{ active: activeButton === 'status' }" @click="toggleButton('status')">Status</div>
          </div>
        </div>
        <div v-if="activeButton === 'stats'"><div class="flex">
          <div class="mx-6 h-[300px] w-[600px] bg-white overflow-hidden sm:rounded-lg">
            <div class="w-[540px] flex justify-between mt-4">
              <div>
                <p class="ml-6 w-2 text-black text-2xl">2000</p>
                <p class="ml-6 w-2 text-black text-sm">USERS</p>
              </div>
              <svg
                class="h-6 w-6"
                fill="#000000"
                height="200px"
                width="200px"
                version="1.1"
                id="Capa_1"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                viewBox="0 0 32.055 32.055"
                xml:space="preserve"
                transform="rotate(90)"
              >
                <g id="SVGRepo_bgCarrier" stroke-width="0" />
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round" />
                <g id="SVGRepo_iconCarrier">
                  <g>
                    <path
                      d="M3.968,12.061C1.775,12.061,0,13.835,0,16.027c0,2.192,1.773,3.967,3.968,3.967c2.189,0,3.966-1.772,3.966-3.967 C7.934,13.835,6.157,12.061,3.968,12.061z M16.233,12.061c-2.188,0-3.968,1.773-3.968,3.965c0,2.192,1.778,3.967,3.968,3.967 s3.97-1.772,3.97-3.967C20.201,13.835,18.423,12.061,16.233,12.061z M28.09,12.061c-2.192,0-3.969,1.774-3.969,3.967 c0,2.19,1.774,3.965,3.969,3.965c2.188,0,3.965-1.772,3.965-3.965S30.278,12.061,28.09,12.061z"
                    />
                  </g>
                </g>
              </svg>
            </div>
            <canvas id="myChart"></canvas>
          </div>
          <div class="data">


      </div>
          <div class="mx-4 h-[300px] w-[600px] bg-white overflow-hidden  sm:rounded-lg">
            <div class="w-[540px] flex justify-between mt-4">
              <div>
                <p class="ml-6 w-2 text-black text-2xl">123</p>
                <p class="ml-6 w-2 text-black text-sm">SUBCRIBERS</p>
              </div>
              <svg
                class="h-6 w-6"
                fill="#000000"
                height="200px"
                width="200px"
                version="1.1"
                id="Capa_1"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                viewBox="0 0 32.055 32.055"
                xml:space="preserve"
                transform="rotate(90)"
              >
                <g id="SVGRepo_bgCarrier" stroke-width="0" />
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round" />
                <g id="SVGRepo_iconCarrier">
                  <g>
                    <path
                      d="M3.968,12.061C1.775,12.061,0,13.835,0,16.027c0,2.192,1.773,3.967,3.968,3.967c2.189,0,3.966-1.772,3.966-3.967 C7.934,13.835,6.157,12.061,3.968,12.061z M16.233,12.061c-2.188,0-3.968,1.773-3.968,3.965c0,2.192,1.778,3.967,3.968,3.967 s3.97-1.772,3.97-3.967C20.201,13.835,18.423,12.061,16.233,12.061z M28.09,12.061c-2.192,0-3.969,1.774-3.969,3.967 c0,2.19,1.774,3.965,3.969,3.965c2.188,0,3.965-1.772,3.965-3.965S30.278,12.061,28.09,12.061z"
                    />
                  </g>
                </g>
              </svg>
            </div>

            <canvas id="myChart2"></canvas>

          </div>
        </div></div>
        <div v-if="activeButton === 'tasks'" class="text-2xl">Tasks go here</div>
        <div v-if="activeButton === 'support'" class="text-2xl">Support go here</div>
        <div v-if="activeButton === 'status'" class="text-2xl">Status go here</div>
      </div>
    </div>
  </div>
</template>

  <script>
import Chart from 'chart.js/auto';

export default {

    mounted() {
        // Your component mounted hook code here
        // This is where you can initialize the chart
        var ctx = document.getElementById('myChart').getContext("2d");
        new Chart(ctx, {
            type: 'line',
            data: {
                labels: this.chartData.map(item => item[0]),
                datasets: [{
                    label: 'Example',
                    data: this.chartData.map(item => item[1]),
                    backgroundColor: ['#2ecc71', '#e74c3c', '#8e44ad', '#d35400', '#16a085']
                }]
            },
            options: {
                title: {
                    display: true,
                    fontSize: 22,
                    text: 'Example'
                }
            }
        });
        var ctx = document.getElementById('myChart2').getContext("2d");
        new Chart(ctx, {
            type: 'line',
            data: {
                labels: this.chartData.map(item => item[0]),
                datasets: [{
                    label: 'Example',
                    data: this.chartData.map(item => item[1]),
                    backgroundColor: ['#2ecc71', '#e74c3c', '#8e44ad', '#d35400', '#16a085']
                }]
            },
            options: {
                title: {
                    display: true,
                    fontSize: 22,
                    text: 'Example'
                }
            }
        });
    },
    data() {
        return {
            activeButton: 'stats',
            chartData: [
                ['2014', 100],
                ['2015', 200],
                ['2016', 300],
                ['2017', 400],
                ['2018', 500]
            ]
        };
    },
    methods: {
        toggleButton(button) {
            this.activeButton = button;
        },
    },
};


  </script>


  <style scoped>
  .button {
    display: inline-block;
    padding: 10px 30px;
    cursor: pointer;
    border-radius: 8%;
  }

  .button.active {
    background-color: blue;
    color: #fff;
  }

  .data {
    margin-top: 20px;
  }
  </style>
