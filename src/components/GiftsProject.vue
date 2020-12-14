<template>
    <div class="StagesAndStatus" >
        <div class="Status" >
            <p class="title"> Подарки проекта</p>

            <div class="card" >
                <img class="img" src="../assets/png/Bobromania_shop.png" alt="">
                <img class="img" src="../assets/png/Bobromania_shop_2.png" alt="">
                <img class="img" src="../assets/png/Bobromania_shop_3.png" alt="">
                <img class="img" src="../assets/png/croc_t_shirt_noman.jpg" alt="">
            </div>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
.StagesAndStatus{
    width: 100%;
    display: flex;
    justify-content: center;
}
.Status{
    padding-left: 70px;
    padding-right: 70px;
    width: 100%;
}
.title{
    margin-top: 74px;
    font-family: Croc;
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    line-height: 103.4%;
}
.card{
    margin-top: 27px;
    width: 100%;
    /* height: 220px; */

    position: relative;
}
.img{
    margin-left: 9.5px;
    width: 190px
}
@media screen and (min-width: 1550px) {
    .Status{
        min-width: 1550px;
        max-width: 1550px;

    }    
}
</style>
