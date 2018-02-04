<style lang="less">
@import './home.less';
</style>
<template>
    <!-- <div class="search"  v-if="blockState">
        <div class="search-center">
            <Select @on-query-change="passValue(1)" 
                v-model="model13"
                filterable
                remote
                :remote-method="remoteMethod1"
                :loading="loading1" style="width:70%;" placeholder="请输入人物关系抽取">
                <Option v-for="(option, index) in options1" :value="option.value" :key="index" >{{option.label}}</Option>
            </Select>
            <Button type="success" class="btnSearch"><span style="margin-left:5px;font-size:16px;">搜索一下</span></Button>   
        </div>
    </div> -->
    <!-- v-else -->
    <div class="search" >
        <div class="search-top">
            <Select  @on-query-change="passValue()"
                v-model="model13"
                filterable
                remote
                :remote-method="remoteMethod1"
                :loading="loading1" 
                style="width:70%;" placeholder="请输入人物关系抽取">
                <Option v-for="(option, index) in options1" :value="option.value" :key="index" >{{option.label}}</Option>
            </Select>
            <Button type="success" class="btnSearch"><span style="margin-left:5px;font-size:16px;">搜索一下</span></Button> 
        </div>
        <div style=" width:100%;margin-top:1.5%;">
            <Menu mode="horizontal"  active-name="1">
                <MenuItem name="1">
                    <Icon type="ios-paper"></Icon>
                        论文
                </MenuItem>
                <MenuItem name="2">
                    <Icon type="ios-people"></Icon>
                        机构
                </MenuItem>
                <MenuItem name="3">
                    <Icon type="ios-people"></Icon>
                        人物
                </MenuItem>
                <MenuItem name="4">
                    <Icon type="settings"></Icon>
                        关系
                </MenuItem>
             </Menu>              
         </div>
         <div class="search-contain">
             <div class="contain_left">
                    <Row style="margin-top:1%;">
                        <Col span="24">
                           
                           <ul>
                               <li> <a href="#" class="link">人物关系</a>抽取__百度文库</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                           
                             <ul>
                               <li>  <a href="#" class="link">人物关系</a>抽取-CSDN博客</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                           
                             <ul>
                               <li> Python基于共现提取《釜山行》<a href="#" class="link">人物关系</a> - CSDN博客</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                            
                             <ul>
                               <li> 利用中文在线资源的远程监督<a href="www.baidu.com" class="link">人物关系</a>抽取 - 道客巴巴</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24"> 
                         <ul>
                               <li>基于语义角色标注的微博<a href="#" class="link">人物关系</a>抽取.pdf 全文 文档投稿网</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                         <ul>
                               <li>  基于深度学习的<a href="#" class="link">关系抽取</a> - CSDN博客</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                            
                             <ul>
                               <li> 基于CRF的面向主题的<a href="#" class="link">人物关系</a>抽取_百度学术</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                           
                              <ul>
                               <li>  基于新闻数据的中文人物社会<a href="#" class="link">关系抽取</a>研究 - 道客巴巴</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                        <Col span="24">
                          
                             <ul>
                               <li>   基于特征选择的<a href="#" class="link">人物关系</a>抽取方法 - 豆丁网</li>
                               <li>作者：李四</li>
                               <li>期刊：《百科知识》&nbsp;&nbsp;发表时间：2017/2/4</li>
                           </ul>
                        </Col>
                    </Row>
                    <!-- 处理分页的 -->
                    <div style="width:100%;padding-left:20%;"> 
                        <Page :total="100"></Page>
                    </div>
                    <!-- 处理分页的 -->
             </div>
             <div style="width:54%;float:right;" >
                  <div style="width:100%;height:500px;background:red;" id="echartContainer"></div>
                  <div style="width:100%;"></div>
             </div>
         </div>
    </div> 
</template>
<script>
let echarts = require('echarts');
// import cityData from './map-data/get-city-value.js';
// import homeMap from './components/map.vue';
// import dataSourcePie from './components/dataSourcePie.vue';
// import visiteVolume from './components/visiteVolume.vue';
// import serviceRequests from './components/serviceRequests.vue';
// import userFlow from './components/userFlow.vue';
// import countUp from './components/countUp.vue';
// import inforCard from './components/inforCard.vue';
// import mapDataTable from './components/mapDataTable.vue';
// import toDoListItem from './components/toDoListItem.vue';
export default {
    name: 'home',

    components: {
        // homeMap,
        // dataSourcePie,
        // visiteVolume,
        // serviceRequests,
        // userFlow,
        // countUp,
        // inforCard,
        // mapDataTable,
        // toDoListItem
    },
    data() {
        return {
            theme1: 'dark',
            blockState: true,
            model13: '',
            loading1: false,
            options1: [],
            list: [
                '地理关系抽取',
                '音乐关系抽取',
                '基因蛋白质关系抽取',
                '人物关系抽取'
            ]
        };
    },
    computed: {},
    methods: {
        remoteMethod1(query) {
            if (query !== '') {
                this.loading1 = true;
                setTimeout(() => {
                    this.loading1 = false;
                    const list = this.list.map(item => {
                        return {
                            value: item,
                            label: item
                        };
                    });
                    this.options1 = list.filter(
                        item =>
                            item.label
                                .toLowerCase()
                                .indexOf(query.toLowerCase()) > -1
                    );
                }, 200);
            } else {
                this.options1 = [];
            }
        },
        passValue(data) {
            if (data == 1) {
                this.blockState = false;
            }
        },
        //初始化右侧图形的数据
        init() {
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(
                document.getElementById('echartContainer')
            );
            // 绘制图表
            var size = 60;
            var size1 = 30;
            var yy = 200;
            var yy1 = 250;
            myChart.setOption({
                title: {
                    text: '人物关系图',
                    top: 'top',
                    left: 'left',
                    textStyle: {
                        color: '#f7f7f7'
                    }
                },
                tooltip: {
                    formatter: '{b}'
                },
                toolbox: {
                    show: true,
                    feature: {
                        restore: {
                            show: true
                        },
                        saveAsImage: {
                            show: true
                        }
                    }
                },
                backgroundColor: '#f8f8f9',
                animationDuration: 1000,
                animationEasingUpdate: 'quinticInOut',
                series: [
                    {
                        name: '知识体系',
                        type: 'graph',
                        layout: 'force',
                        force: {
                            repulsion: 60,
                            gravity: 0.1,
                            edgeLength: 30,
                            layoutAnimation: true
                        },
                        data: [
                            {
                                name: '人物关系抽取',
                                x: 0,
                                y: yy,
                                symbolSize: 100,
                                category: '人物关系抽取',
                                draggable: 'true'
                            },
                            {
                                x: 130,
                                y: yy,
                                name: '苏州大学',
                                symbolSize: size,
                                category: '苏州大学',
                                draggable: 'true'
                            },
                            {
                                x: 140,
                                y: yy1,
                                name: '周国栋',
                                symbolSize: size1,
                                category: '苏州大学',
                                draggable: 'true'
                            },
                            {
                                x: 170,
                                y: yy1,
                                name: '华中科技大学',
                                symbolSize: size,
                                category: '华中科技大学',
                                draggable: 'true'
                            },
                            {
                                x: 180,
                                y: yy,
                                name: '何婷婷',
                                symbolSize: size1,
                                category: '华中科技大学',
                                draggable: 'true'
                            },
                            {
                                x: 260,
                                y: yy,
                                name: '哈尔滨工业大学',
                                symbolSize: size,
                                category: '哈尔滨工业大学',
                                draggable: 'true'
                            },
                            {
                                x: 270,
                                y: yy1,
                                name: '秦兵',
                                symbolSize: size1,
                                category: '哈尔滨工业大学',
                                draggable: 'true'
                            }
                        ],
                        links: [
                            {
                                source: '人物关系抽取',
                                target: '苏州大学'
                            },
                            {
                                source: '人物关系抽取',
                                target: '华中科技大学'
                            },
                            {
                                source: '人物关系抽取',
                                target: '哈尔滨工业大学'
                            },
                            {
                                source: '苏州大学',
                                target: '周国栋'
                            },
                            {
                                source: '华中科技大学',
                                target: '何婷婷'
                            },
                            {
                                source: '哈尔滨工业大学',
                                target: '秦兵'
                            }
                        ],
                        categories: [
                            {
                                name: '人物关系抽取'
                            },
                            {
                                name: '苏州大学'
                            },
                            {
                                name: '华中科技大学'
                            },
                            {
                                name: '哈尔滨工业大学'
                            }
                        ],
                        roam: false,
                        label: {
                            normal: {
                                show: true,
                                position: 'inside',
                                formatter: '{b}',
                                fontSize: 16,
                                fontStyle: '600'
                            }
                        },
                        lineStyle: {
                            normal: {
                                width: 6,
                                color: 'source',
                                curveness: 0,
                                type: 'solid'
                            }
                        }
                    }
                ]
            });
        }
    },
    mounted() {
        this.init();
    }
};
</script>
