<template>
    <div class="MainNavigation">
        <div class="echarts">
            <IEcharts
                    :option="bar"
                    :loading="loading"
            />
        </div>
        <button @click="loadInfo">Add Date</button>
        {{loadData}}
    </div>
</template>

<script>
    import IEcharts from 'vue-echarts-v3/src/full.js';

    export default {
        name: "main-schedule",
        components: {
            IEcharts
        },
        props:[
        ],
        data: () => ({
            loading: false,
            bar: {
                title: {
                    text: 'OPEN'
                },
                tooltip: {},
                xAxis: {
                    data: ''
                },
                yAxis: {},
                series: {
                    name: 'Some',
                    type: 'bar',
                    data: [5, 20, 69, 10, 10, 20]
                },
                loadData:''
            }

        }),
        methods: {
            doRandom() {
                const that = this;
                let data = [];
                for (let i = 0, min = 5, max = 99; i < 6; i++) {
                    data.push(Math.floor(Math.random() * (max + 1 - min) + min));
                }
                that.loading = !that.loading;
                that.bar.series[0].data = data;
            },
            loadInfo() {
                let xhr = new XMLHttpRequest();
                xhr.open('GET', 'http://wb-predictivemaintenance-api.prsp7vkew2.eu-central-1.elasticbeanstalk.com/api/TorqueValues', false);
                xhr.send();
                if (xhr.status !== 200) {
                    alert('Ошибка ' + xhr.status + ': ' + xhr.statusText);
                } else {
                    let data = xhr.responseText;
                    let newData  = JSON.parse(data);
                    let dataOpen = newData.map(function(name) {
                        if (name.Direction === "Open") {
                            return name
                        }
                    });

                    this.loadData = dataOpen;
                    console.log(this.loadData);
                    alert("Данный Open загруженны");

                    this.series.data = this.series.data.push(
                        this.loadData.map(function (item) {
                            alert(item.Position);
                            return item.Position
                        }))
                }
            }
        }
    };

</script>

<style scoped>
    .MainNavigation{
        display: inline-block;
        width: 97%;
        background: #fff;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    }
    .echarts {
        width: 400px;
        height: 400px;
    }
</style>