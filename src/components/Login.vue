<template>
  <div class="login">
    <group class="group1css">
      <x-input title="" name="mobile" placeholder="请输入手机号" v-model="mobile" keyboard="number" is-type="china-mobile" required></x-input>
<!--      <x-input title="" type="text" placeholder="请输入验证码" v-model="code" required>-->
<!--        <x-button slot="right" type="primary" mini :disabled="getCode.disabled" @click.native="handleGetCode" style="width: 100px;">{{getCode.txt}}</x-button>-->
<!--      </x-input>-->
      <x-input title="" type="password" placeholder="请输入密码" v-model="password" :min="6" :max="16" required></x-input>
<!--      <x-input title="" type="password" placeholder="确认密码" v-model="passwordC" :min="6" :max="16" required></x-input>-->
    </group>
<!--    <p><span>注册后，您的微信账号和手机号都可以登录</span></p>-->
    <box gap="10px 25px">
      <x-button class="button1css" type="primary" @click.native="handleLogin">登陆</x-button>
    </box>
    <p class="p1css">
      <router-link to="/">没有账号？去注册</router-link>
    </p>
  </div>
</template>

<script>
    import { XInput, Box, Group, XButton } from 'vux'
    export default {
        name: 'Login',
        data() {
            return {
                mobile: '', //手机号
                // code: '', //验证码
                password: '' //密码
                // passwordC: '', //确认密码
                // getCode: {
                //     txt: '获取验证码',
                //     disabled: false,
                // }
            }
        },
        methods: {
            handleGetCode() {
                if(this.mobile) {
                    this.getCode.disabled = true;
                    this.getCode.txt = '获取中...';
                    let seconds = 60;
                    let self = this;
                    let time = setInterval(function() {
                        --seconds;
                        self.getCode.txt = seconds + 's';
                        if(seconds <= 0) {
                            clearInterval(time);
                            self.getCode.disabled = false;
                            self.getCode.txt = '获取验证码';
                        }
                    }, 1000)
                } else {
                    alert('请先填写手机号');
                }
            },
            handleLogin() {
                if(!this.mobile || !this.password ) {
                    alert('您有未填项，不能登陆')
                } else if(this.mobile !== '18666668888'||this.password !=='123456') {
                    alert('手机号或者密码错误，请重新输入！')
                } else {
                    alert('登陆成功！')
                    this.$router.push({
                        path:'/Index'
                    })
                }
            }
        },
        created() {
            window.document.title = '登陆';
        },
        components: {
            XInput,
            XButton,
            Group,
            Box
        }
    }
</script>

<style scoped lang="less">
  .button1css,.group1css,.p1css{
    width: 50%;
    margin: auto;
  }
</style>
