<template>
  <div class="tab-tel tab-list" @keyup.enter="login">
    <div class="form-wrapper">
        <div class="account flex">
            <p class="input-title">手机号:</p>
            <div class="input-row flex">
                <input type="text" name="countrycode" class="countrycode form-control" v-model="loginCountry" placeholder="国家码">
                <input type="tel" v-model="loginTel" name="account" class="form-control" maxlength="11" placeholder="输入手机号">
            </div>
        </div>
        <div class="password flex">
            <p class="input-title">密码:</p>
            <div class="input-row">
                <input type="password" v-model="loginTelpwd" name="password" class="form-control" placeholder="输入密码">
            </div>
        </div>
    </div>
    <div class="btn-area">
        <button class="btn" id="submitLogin" @click="login">登录</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import common from '../../components/common'

export default {
    data: function(){
        return{
            loginCountry: '',
            loginTel: '',
            loginTelpwd: '',
            msg: '',
            ip: ''
        }
    },
    mounted(){
        this.ip_info();
    },
    methods:{
        ip_info(){
            let that = this;
            axios.get('/api/v1/getip')
            .then(function (response) {
                that.ip = response.data.data;
                let url = '/api/v1/user/ipto_info';
                axios.post(url,that.ip)
                .then(function (response) {
                    that.loginCountry = response.data.data.phone_code;
                })
            })
        },
        login:function(){
            if (this.loginTel == '' || this.loginTelpwd == '' || this.loginCountry == '') {
                let alert = {
                    message: '请填写完整的资料',
                    type: 'warning'
                }
                this.alertOpen(alert.message,alert.type);
            }else{
                let that = this;
                // md5验证
                let login = {
                    'telephone': this.loginTel,
                    'password': this.loginTelpwd,
                    'post_type': 'login',
                    'areacode': this.loginCountry
                }
                // ajax
                let url = '/api/v1/phone/web_login';
                let formData = new FormData();
                formData.append('telephone', this.loginTel);
                formData.append('password', this.loginTelpwd);
                formData.append('post_type', 'login');
                formData.append('areacode', this.loginCountry);
                let config = {
                    headers:{
                        versions: '1',
                        tokens: common.sortMd5(login),
                        'content-type': 'multipart/form-data'
                    }
                }
                axios.post(url,formData,config)
                .then(function (response) {
                    if (response.data.errCode == '0') {
                        let alert = {
                            message: '登录成功',
                            type: 'success'
                        }
                        that.alertOpen(alert.message,alert.type);
                        window.localStorage.setItem('id',response.data.data.id);
                        window.localStorage.setItem('child',response.data.data.role_id);
                        window.localStorage.setItem('token_id',response.data.data.token_id);
                        window.location.href = '/study';
                    }else if(response.data.errCode == '30005'){
                        let alert = {
                            message: '用户名或密码错误',
                            type: 'error'
                        }
                        that.alertOpen(alert.message,alert.type);
                    }else{
                        let alert = {
                            message: '登录失败',
                            type: 'error'
                        }
                        that.alertOpen(alert.message,alert.type);
                    }
                })
                .catch(function (error) {
                    let alert = {
                        message: '系统错误',
                        type: 'error'
                    }
                    that.alertOpen(alert.message,alert.type);
                })
            }
        },
        alertOpen(msg,tp){
            this.$message({
                message: msg,
                type: tp
            });
        }
    }
}
</script>

<style lang="less" scoped>
.form-wrapper{ 
    margin-top: 80px;
    .account{
        margin-top: 20px;
        border-bottom: 1px solid #ff7b48;
        p{
            width: 65px;
            line-height: 40px;
            color: #ff7b48;
        }
    }
    .password{
        margin-top: 20px;
        border-bottom: 1px solid #ff7b48;
        p{
            width: 65px;
            line-height: 40px;
            color: #ff7b48;
        }
    }
    .input-title{
        font-size: 14px;
        color: #555;
    }
    .input-row{ width: calc(~'100% - 65px');
        .countrycode{
            margin-right: 10px;
            padding-left: 0;
            width: 40px;
            text-align: center;
        }
        input{
            width: 100%;
            height: 40px;
            border: 0;
            background: #FFFFFF;
            outline: 0;
        }
    }
}
.btn-area{
    margin-top: 80px;
    .btn-link{
        display: block;
        margin-top: 15px;
        text-align: center;
        font-size: 16px;
        color: #F8763D;
    }
    .btn{
        width: 100%;
        height: 50px;
        background-color: #ff7b48;
        border-radius: 6px;
        box-shadow: 0px 0px 7px 3px #ece5e3;
        font-size: 16px;
        border: 0;
        color: #FFFFFF;
        cursor: pointer;
    }
}
</style>