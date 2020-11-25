<template>
    <div class="ProjectProgressBar" >
        <div class="title"> 
            <p>Прогрессбар проекта</p>
            <div class="btns" >
                <button class="btn" > <p class="text_btn">Сказать спасибо</p></button>
                <button class="btn" > <p class="text_btn">Вручить бейдж</p></button>
            </div>
        </div>

        <div class="card" >
            <div class="title_card" >
                <div class="Team_title" >Команда</div>
                <div class="Badges_title" >Бейджи</div>
                <div class="Like_title" >Лайк</div>
                <div class="Ideas_title" >Идеи</div>
                <div class="Thanks_title" >Спасибо</div>
            </div>
            <!-- ... -->


            <!-- 30 -->
            <!-- 38 -->
            <!-- 10 -->
            <!-- 10 -->
            <!-- 12 -->

            <p class="more" >Подробнее</p>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
.Team_title{
    width: 30%;
}
.Badges_title{
    width: 38%;
}
.Like_title{
    width: 10%;
}
.Ideas_title{
    width: 10%;
}
.Thanks_title{
    width: 12%;
}
.ProjectProgressBar{
    padding-left: 70px;
    padding-right: 70px;
}
.text_btn {
    font-family: Croc;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 103.4%;
    text-align: center;
    color: #00A560;
}
.btn{
    padding: 10px;
    padding-left: 20px ;
    padding-right: 20px ;
    margin: 5px;
    border-radius: 10px;
    border: 0;
    background: #fff;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);;
}
.title{
    margin-top: 74px;
    font-family: Croc;
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    line-height: 103.4%;
    display: flex;
    justify-content: space-between;
}
.btns{
    display: flex;
    justify-content: center;
}
.card{
    margin-top: 20px;
    width: 100%;
    height: 307px;

    background: #FFFFFF;

    /* shadow */
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    position: relative;
}
.title_card{
    width: 100%;
    height: 47px;
    padding-left: 10px;
    padding-right: 10px;
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
    