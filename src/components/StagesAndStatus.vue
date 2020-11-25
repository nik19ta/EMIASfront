<template>
    <div class="StagesAndStatus" >
        <p class="title"> Этапы и статус</p>

        <div class="card" >
            <div class="title_card" >
                <p class="title_card_text" >Название проекта</p>
            </div>

            <div class="content" >
                <div class="content_div" >
                    <img src="../assets/start.svg" alt="">
                    <p>Старт</p>
                </div>
                <div class="progress" >

                </div>
                <div class="content_div" >
                    <img src="../assets/finish.svg" alt="">
                    <p>Финиш</p>
                </div>
            </div>
            <!-- ... -->
            

            <p class="more" >Подробнее</p>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
p {
    font-family: Croc;
    font-style: normal;
    font-weight:100;
    font-size: 15.8667px;
    line-height: 10px;
    color: #2B2B2B;
    width: 100%;
    text-align: center;
    margin-top: 10px;
}
.content_div{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}
.progress{
    width: calc(100% - 60px - 60px);
    height: 2px;
    background: #00A560;
}
.content{
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: calc(100% - 47px);
    padding-left: 20px;
    padding-right: 20px;
}
.StagesAndStatus{
    padding-left: 70px;
    padding-right: 70px;
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
    height: 220px;

    background: #FFFFFF;

    /* shadow */
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    position: relative;
}
.title_card{
    width: 100%;
    height: 47px;

    background: #00A560;

    /* shadow */
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px 10px 0px 0px;

    display: flex;
    align-items: center;
}

.title_card_text{
    font-family: Croc;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 103.4%;
    margin-left: 27px;

    /* or 17px */

    color: #FFFFFF;
}
.more{
    position: absolute;
    width: 87px;
    height: 14px;
    right: 18px;
    bottom: 23px;

    font-family: Croc;
    font-style: normal;
    font-weight: 300;
    font-size: 15.8667px;
    line-height: 103.4%;

    /* or 16px */
    text-decoration-line: underline;

    color: #00A560;
}
</style>
