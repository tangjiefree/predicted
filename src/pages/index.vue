<template>
    <div class="index">
        <Login></Login>
        <Head></Head>
        <Foot class="bottom"></Foot>
    </div>
</template>

<script>
import Login from '../components/login';
import header from '../components/header';
import footer from '../components/footer'
export default {
    components: {
        Login,
        Head: header,
        Foot: footer
    },
    data() {
        return {

        }
    }
}
</script>

<style lang="less" scoped>
    .index {
        width: 100%;
        height: 100%;
        background: url(../assets/index-1.png) no-repeat;
        background-size: cover;
    }
    .bottom {
        position: fixed;
        bottom: 0;
    }
</style>