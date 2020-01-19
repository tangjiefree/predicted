<template>
    <div class="header">
        <div class="logo"></div>
        <div class="center">
            {{self}}
        </div>
        <div class="regist">
            {{regist}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'header',
    data() {
        return {
            self: '注册',
            regist: '登陆'
        }
    }
}
</script>

<style lang="less" scoped>
    .header {
        display: flex;
        align-items: flex-end;
        height: .88rem;
        .logo {
            width: 2.84rem;
            height: .86rem;
            background: url('../assets/logo.png') no-repeat;
            background-size: contain;
        }
        .center,
        .regist {
            width: 1.8rem;
            color:#fff;
            line-height: .5rem;
            font-size: .26rem;
            height: .5rem;
            background: url(../assets/head.png) no-repeat;
            background-size: contain;
        }

    }
</style>