<template>

    <!--main content start-->
    <div id="main-content">
        <div class="wrapper">
            <div class="row">
                <div class="col-md-12">
                    <!--breadcrumbs start -->
                    <ul class="breadcrumb">
                        <li><router-link :to="{name: 'index'}"><i class="icon-home"></i> Home</router-link></li>
                        <li class="active">数据统计</li>
                        <li class="active">金额统计</li>
                    </ul>
                    <!--breadcrumbs end -->
                </div>
            </div>
            <div class="panel">
                <div class="panel-body">
                    <router-link :to="{name: 'statistics_money_charts'}">
                        <el-tag>已支付订单</el-tag>
                    </router-link>
                    <router-link :to="{name: 'statistics_orderNotPay_charts'}">
                        <el-tag class="activeTag">未支付订单</el-tag>
                    </router-link>
                    <router-link :to="{name: 'statistics_finishWithDraw_charts'}">
                        <el-tag>支出统计</el-tag>
                    </router-link>
                </div>
            </div>

            <charts-common :apiAct="orderNotPayUser" text="未支付人数统计" :showDev="showDev"></charts-common>
            <charts-common :apiAct="orderNotPayCount" text="未支付次数统计" :showDev="showDev"></charts-common>
            <charts-common :apiAct="orderNotPayPrices" text="未支付金额统计" :showDev="showDev"></charts-common>
            <charts-common :apiAct="orderTransformRate" text="下单转化率" :showDev="showDev" :yName="yName" :formatter="formatter"></charts-common>
        </div>
    </div>
    <!--main content end-->
</template>
<style scoped>
    .activeTag{
        color: #FFF;background: #2185D0
    }
</style>
<script>
    import {orderNotPayUser,orderNotPayCount,orderNotPayPrices,orderTransformRate} from 'api/moneyCharts';
    import chartsCommon from 'components/statistics/charts_common';

    export default {
        name: 'moneyCharts',
        components: {chartsCommon},
        data() {
            return {
                orderNotPayUser,orderNotPayCount,orderNotPayPrices,orderTransformRate,
                yName:'单位百分比',formatter:'%',
                showDev:false
            };
        }
    }
</script>
