<template>
    <div class="StagesAndStatus" >
        <div class="Status" >
            <p class="title"> Подарки проекта</p>

            <div class="card" >
                <img class="img" src="../assets/png/1.png" alt="">
                <img class="img" src="../assets/png/2.png" alt="">
                <img class="img" src="../assets/png/3.png" alt="">
                <img class="img" src="../assets/png/4.png" alt="">
                <img class="img" src="../assets/png/2.png" alt="">
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
}
@media screen and (min-width: 1900px) {
    .Status{
        min-width: 1700px;
        max-width: 1700px;

    }    
}
@media screen and (min-width: 1600px) {
    .Status{
        min-width: 1700px;
        max-width: 1700px;
    }    
}
</style>
