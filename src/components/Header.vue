<template>
    <div class="header" >
        <img class="logo" src="../assets/logo.svg" alt="">

        <div class="exit_and_profile" >
            <img src="../assets/mdi_perm_identity.svg" alt="">
            <img src="../assets/mdi_exit_to_app.svg" alt="">
        </div>
    </div>
</template>

<script>
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
</style>
