## ECharts
    import * as echarts from 'echarts';

    <div class="charts" ref="charts"></div>
    mounted(){
        // 初始化实例
        const lineCharts = echarts.init(this.$refs.charts)
        // 配置对象
        lineCharts.setOption({
            title: {
                text: '',  // 标题
                subtext: '',  // 子标题
                left: 'center',  // 位置
            }
            <!-- 图表配置 -->
            grid: {
                top: 0,
                right: 0,
                bottom: 0,
                left: 0,
                width: 0,
                height: 0
            },
            // x轴配置
            xAxis: {
                data: [],  // 数据
                // show: false,
                // type: 'category'  // 类目轴
            },
            // y轴配置
            yAxis: {
                // show: false,
                // 是否显示y轴轴线
                axisLine: {
                    show: true
                },
                // 是否显示y轴刻度
                axisTick: {
                    show: true
                }
            },
            // 系列的设置： 绘制图表类型、数据展示
            series: [
                {
                    type: 'line',
                    data: [50, 65, 35, 99, 33, 66, 40, 75, 20, 82],
                    // 拐点样式
                    itemStyle: {
                        opacity: 0
                    },
                    // 线条样式
                    lineStyle: {
                        color: 'pink'
                    },
                    // 填充颜色
                    areaStyle: {
                        color: {
                            type: 'linear',
                            x: 0,
                            y: 0,
                            x2: 0,
                            y2: 1,
                            colorStops: [{
                                offset: 0, color: 'pink' // 0% 处的颜色
                            }, {
                                offset: 1, color: 'white' // 100% 处的颜色
                            }],
                            global: false // 缺省为 false
                        }
                    },
                    // 平滑曲线
                    smooth: true
                },
                {
                    type: 'bar',
                    data: [50, 65, 35, 99, 33, 66, 40, 75, 20, 82],
                    color: 'cyan'
                },
                {
                    name: '饼状图',
                    type: 'pie',
                    data: [
                        {name: '衣服', value: 10},
                        {name: '直播', value: 20},
                        {name: '游戏', value: 30},
                        {name: '电影', value: 40}
                    ],
                    width: 250,
                    height: 250,
                    radius: 50,
                    left: 700,
                }
            ],
            // 提示组件
            tooltip: {},
            // 切换组件
            legend: {
                data: ['柱状图', '折线图', '饼状图']
            },
            // 工具栏组件
            toolbox: {
                show: true,
                feature: {
                dataZoom: {
                    yAxisIndex: "none"
                },
                dataView: {
                    readOnly: false
                },
                magicType: {
                    type: ["line", "bar"]
                },
                restore: {},
                saveAsImage: {}
                }
            }
        })
    }