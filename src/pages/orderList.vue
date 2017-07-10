<template>
    <div class="order-wrap">
        <h3>您的产品</h3>
        <div class="order-list-choose">
            <div class="order-list-option">
                选择产品：
                <!-- 下拉组件 -->
                <v-selection :selections="products" @on-change="productChange"></v-selection>
            </div>

            <div class="order-list-option">
                <div class="time-float">开始日期：</div>
                <v-date-picker @on-change="getStartDate"></v-date-picker>
            </div>

            <div class="order-list-option">
                <div class="time-float">结束日期：</div>
                <v-date-picker @on-change="getEndDate"></v-date-picker>
            </div>

            <div class="order-list-option">
                关键词：
                <!-- 使用lazy表示数据绑定不会同步更新到数据中，这有等输入结束以后才会同步 -->
                <input type="text" v-model.lazy="query" class="order-query">
            </div>
        </div>
        <div class="order-list-table">
            <table>
                <tr>
                    <th v-for="head in tableHeads" @click="changeOrderType(head)" :class="{active:head.active}">{{ head.label }}</th>
                </tr>
                <tr v-for="item in tableData" :key="item.period">
                    <td v-for="head in tableHeads">{{ item[head.key] }}</td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>

    import VSelection from '../components/selection'     //下拉选择
    import VDatePicker from '../components/datepicker'   //选择时间组件
    import _ from 'lodash'    //工具库


    export default {
        components: {
            VSelection,
            VDatePicker
        },
        data () {
            return {
                query: '',        //关键词
                productId: 0,
                startDate: '',    //开始时间
                endDate: '',      //结束时间
                products: [       //下拉列表
                    {
                        label: '数据统计',
                        value: 0
                    },
                    {
                        label: '数据预测',
                        value: 1
                    },
                    {
                        label: '流量分析',
                        value: 2
                    },
                    {
                        label: '广告发布',
                        value: 3
                    }
                ],
                tableHeads: [        //订单列表头部
                    {
                        label: '订单号',
                        key: 'orderId'
                    },
                    {
                        label: '购买产品',
                        key: 'product'
                    },
                    {
                        label: '版本类型',
                        key: 'version'
                    },
                    {
                        label: '有效时间',
                        key: 'period'
                    },
                    {
                        label: '购买日期',
                        key: 'date'
                    },
                    {
                        label: '数量',
                        key: 'buyNum'
                    },
                    {
                        label: '总价',
                        key: 'amount'
                    }
                ],
                currentOrder: 'asc',      //订单列表排序
                tableData: []             //列表数据
            }
        },
        watch: {
            query () {
                this.getList()
            }
        },
        methods: {
            // 下拉选中，进行刷选
            productChange (obj) {
                this.productId = obj.value
                this.getList()
            },

            // 获取当前时间，进行刷选
            getStartDate (date) {
                this.startDate = date
                this.getList()
            },

            // 获取结束时间，进行刷选
            getEndDate (date) {
                this.endDate = date
                this.getList()
            },

            // 获取订单列表，通过向后台发送请求参数
            getList () {
                let reqParams = {
                    query: this.query,
                    productId: this.productId,
                    startDate: this.startDate,
                    endDate: this.endDate
                }
                this.$http.post('/api/getOrderList', reqParams).then((res) => {
                    this.tableData = res.data.list
                }, (err) => {

                })
            },

            // 点击表格头部，表格排序
            changeOrderType (headItem) {

                // 将所有设置为active样式设置为false
                this.tableHeads.map((item) => {
                    item.active = false
                    return item
                })

                // 当前点击的那一项，头部添加样式
                headItem.active = true

                // 判断当前排序方式
                if (this.currentOrder === 'asc') {
                    this.currentOrder = 'desc'
                }else if (this.currentOrder === 'desc') {
                    this.currentOrder = 'asc'
                }

                // 获取排序后的数据
                this.tableData = _.orderBy(this.tableData, headItem.key, this.currentOrder)
            }
        },
        mounted () {
            this.getList()
        }
    }
</script>

<style scoped>
    .order-wrap {
        width: 1200px;
        min-height: 800px;
        margin: 20px auto;
        overflow: hidden;
    }
    .order-wrap h3 {
        font-size: 20px;
        font-weight: bold;
        margin-bottom: 20px;
    }
    .order-query {
        height: 25px;
        line-height: 25px;
        border: 1px solid #e3e3e3;
        outline: none;
        text-indent: 10px;
    }
    .order-list-option {
        display: inline-block;
        padding-left: 15px;
    }
    .order-list-option:first-child {
        padding-left: 0;
    }
    .order-list-table {
        margin-top: 20px;
    }
    .order-list-table table {
        width: 100%;
        background: #fff;
    }   
    .order-list-table td,
    .order-list-table th {
        border: 1px solid #e3e3e3;
        text-align: center;
        padding: 10px 0;
    }
    .order-list-table th {
        background: #4fc08d;
        color: #fff;
        border: 1px solid #4fc08d;
        cursor: pointer;
    }
    .order-list-table th.active {
        background: #35495e;
    }
    .order-wrap .order-list-option .time-float{
        display: inline-block;
        float: left;
        height: 27px;
        line-height: 22px;
    }
</style>
