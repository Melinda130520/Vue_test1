<template>
    <div>
        <this-dialog :is-show="isShowCheckDialog" @on-close="checkStatus">
            请检查你的支付状态！
            <div class="button" @click="checkStatus('success')">
                支付成功
            </div>
            <div class="button" @click="checkStatus('error')">
                支付失败
            </div>
        </this-dialog>

        <this-dialog :is-show="isShowSuccessDialog" @on-close="toOrderList">
            购买成功！
        </this-dialog>

        <this-dialog :is-show="isShowFailDialog" @on-close="toOrderList">
            购买失败！
        </this-dialog>
    </div>
</template>

<script>

    import Dialog from './dialog'

    export default {
        components: {
            thisDialog: Dialog
        },
        props: {
            isShowCheckDialog: {    //是否显示对话框
                type: Boolean,
                default: false
            },
            orderId: {              //订单ID
                type: [String, Number]
            }
        },
        data () {
            return {
                isShowSuccessDialog: false,    //成功对话框
                isShowFailDialog: false        //失败对话框
            }
        },
        methods: {
            // 
            checkStatus (type) {
                this.$http.post('/api/checkOrder', {
                    orderId: this.orderId
                }).then((res) => {
                    this.isShowSuccessDialog = true
                    this.$emit('on-close-check-dialog')
                }, (err) => {
                    this.isShowFailDialog = true
                    this.$emit('on-close-check-dialog')
                })

                // 判断购买失败还是成功 --- 临时添加
                if (type === "success") {
                    this.isShowSuccessDialog = true
                }else{
                    this.isShowFailDialog = true
                }
            },
            toOrderList () {
                this.$router.push({path: '/orderList'})
            }
        }
    }

</script>

