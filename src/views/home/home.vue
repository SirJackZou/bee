<style lang="less">
@import './home.less';
// @import '../../styles/common.less';
</style>
<template>
            <div class="search"  v-if="blockState">
                <div class="search-center">
                    <Select @on-query-change="passValue()" 
                        v-model="model13"
                        filterable
                        remote
                        :remote-method="remoteMethod1"
                        :loading="loading1" style="width:70%;" placeholder="请输入人物关系抽取">
                        <Option v-for="(option, index) in options1" :value="option.value" :key="index" >{{option.label}}</Option>
                    </Select>
                    <Button type="success" class="btnSearch" ><span style="margin-left:5px;font-size:16px;">搜索一下</span></Button>
                </div>
              </div>
                <div class="search" v-else>
                    <div class="search-top">
                        <Select  
                            v-model="model13"
                            filterable
                            remote
                            :remote-method="remoteMethod1"
                            :loading="loading1" style="width:70%;" placeholder="请输入人物关系抽取">
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
                </div>
        
    
</template>
<script>
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
            blockState:true,
            model13: '',
            loading1: false,
            options1: [],
            // model13: '',
            // loading1: false,
            // options1: [],
            // list: ['地理关系抽取','音乐关系抽取', '基因蛋白质关系抽取', '人物关系抽取'],
            list: [
                'Alabama',
                'Alaska',
                'Arizona',
                'Arkansas',
                'California',
                'Colorado',
                'Connecticut',
                'Delaware',
                'Florida',
                'Georgia',
                'Hawaii',
                'Idaho',
                'Illinois',
                'Indiana',
                'Iowa',
                'Kansas',
                'Kentucky'
            ]
        }
           
    },
    computed: {
    },
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
        passValue() {
            //  console.log(1);
            //  this.$router.push({
            //             name: 'search_index'
            //         });
            this.blockState=false;
            console.log( this.blockState);
        }
    }
};
</script>
