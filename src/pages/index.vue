<template>
    <div class="index">
        <Login></Login>
        <header></header>
    </div>
</template>

<script>
import Login from '../components/login';
import header from '../components/header';
export default {
    components: {
        Login,
        header
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
</style>