<template>
    <div class="header" >
        <img class="logo" src="../assets/logo.svg" alt="">

        <div class="exit_and_profile" >
            <img v-if="is_name" v-on:click="to_prof" class="cursor" src="../assets/mdi_perm_identity.svg" alt="">
            <img v-on:click="to_login" class="cursor" src="../assets/mdi_exit_to_app.svg" alt="">
        </div>
    </div>
</template>

<script>
export default {
    props: {
        host: {}
    },
    data: function () {
        return {
            actual_stage: 0,
            stages: 0,
            is_name: false
        }
    },
    mounted() {
        if (localStorage.name != undefined) {this.is_name = true;}
        else {this.is_name = false;}
    },
    methods: {
        to_login() {this.$emit('tologin', true)},
        to_prof() {this.$emit('toprof', true)}
    }
}
</script>

<style scoped>
.header {
    background: #FFFFFF;
    height: 68px;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    padding-left: 20px;
    padding-right: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
}
.logo{
    margin-left: 50px;
}
.exit_and_profile{
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100%;
    width: 70px;
}
.cursor{
    cursor: pointer;
}
</style>
