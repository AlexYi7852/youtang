<template>
  <div class="tab-mail tab-list" @keyup.enter="reg">
    <div class="form-wrapper">
        <div class="account flex">
            <p class="input-title">邮箱账号:</p>
            <div class="input-row">
                <input type="mail" name="account" class="form-control" v-model="regMail" placeholder="输入邮箱账号">
            </div>
        </div>
        <div class="password flex">
            <p class="input-title">密码:</p>
            <div class="input-row">
                <input type="password" name="password" class="form-control" v-model="regPwd" placeholder="输入密码">
            </div>
        </div>
    </div>
    <div class="btn-area">
        <button class="btn" id="submitLogin" @click="reg">注册</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Hub from '../../components/hub'
import common from '../../components/common'

export default {
  data:function () {
    return {
      regMail: '',
      regPwd: ''
    }
  },
  methods: {
    // 注册接入
    reg :function(){
        let that = this;
        if (this.regMail == '' || this.regPwd == '') {
            this.$message({
                message: '请填写完整的资料',
                type: 'error'
            });
        }else{
            // md5验证
            let register = {
                'email': this.regMail,
                'password': this.regPwd,
                'post_type': 'register',
            }
            // ajax
            let url = '/api/v1/users/web_register';
            let formData = new FormData();
            formData.append('email', this.regMail);
            formData.append('password', this.regPwd);
            formData.append('post_type', 'register');
            let config = {
                headers:{
                    versions: '1',
                    as: '3',
                    tokens: common.sortMd5(register),
                    'content-type': 'multipart/form-data'
                }
            }
            axios.post(url,formData,config)
            .then(function (response) {
                if (response.data.errCode == '0') {
                    that.$alert('该邮箱已注册成功', '注册成功', {
                        confirmButtonText: '确定',
                        callback: action => {
                            Hub.$emit('loginLink',true);
                        }
                    })
                }else if(response.data.errCode == '30002'){
                    that.$alert('邮箱或密码格式错误，请输入正确的邮箱或6-16位密码', '注册失败', {
						confirmButtonText: '确定',
					})
                }else if(response.data.errCode == '30007'){
                    that.$alert('该邮箱已注册', '注册失败', {
						confirmButtonText: '确定',
					})
                }else{
                    that.$alert('注册失败', '注册失败', {
						confirmButtonText: '确定',
					})
                }
            })
            .catch(function (error) {
                that.$alert('系统错误', response.data.errMsg, {
                    confirmButtonText: '确定',
                })
            })
        }
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
        input{
            padding-left: 15px;
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