<template>
    <div class="login-form">
        <div class="g-form">
            <!-- 用户名 -->
            <div class="g-form-line">
                <span class="g-form-label">用户名：</span>
                <div class="g-form-input">
                    <input type="text"  v-model="usernameModel" placeholder="请输入用户名">
                </div>
                <span class="g-form-error">{{ userErrors.errorText }}</span>
            </div>
            
            <!-- 密码框 -->
            <div class="g-form-line">
                <span class="g-form-label">密码：</span>
                <div class="g-form-input">
                    <input type="password" v-model="passwordModel" placeholder="请输入密码">
                </div>
                <span class="g-form-error">{{ passwordErrors.errorText }}</span>
            </div>
            
            <!-- 登录按钮 -->
            <div class="g-form-line">
                <div class="g-form-btn">
                    <a class="button" @click="onLogin">登录</a>
                </div>
            </div>

            <!-- 错误提示 -->
            <p>{{ errorText }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                usernameModel: '',      //用户名 
                passwordModel: '',      //密码
                errorText: ''           //错误信息
            }
        },
        computed: {
            userErrors () {              //用户名校验

                let errorText, status

                // 判断用户名是否包含@符号
                if (!/@/g.test(this.usernameModel)) {
                    status = false
                    errorText = '不包含@符号'
                }else {
                    status = true
                    errorText = ''
                }

                if (!this.userFlag) {
                    errorText = ''
                    this.userFlag = true
                }

                return {
                    status,
                    errorText
                }
            },
            passwordErrors () {           //密码校验
                let errorText, status

                // 校验密码长度
                if (!/^\w{1,6}$/g.test(this.passwordModel)) {
                    status = false
                    errorText = '密码不是1-6位'
                }else {
                    status = true
                    errorText = ''
                }

                if (!this.passwordFlag) {
                    errorText = ''
                    this.passwordFlag = true
                }

                return {
                    status,
                    errorText
                }
            }
        },
        methods: {
            onLogin () {
                if (!this.userErrors.status || !this.passwordErrors.status) {
                    this.errorText = '部分选项未通过'
                }else {
                    this.errorText = ''
                    this.$http.get('api/login').then((res) => {
                        this.$emit('has-log', res.data)
                    }, (error) => {
                        console.log(error)
                    })
                }
            }
        }
    }
</script>

<style scoped>

</style>
