<template>
    <div class="BulletinOfTheProject" >
        <p class="title"> Вестник проекта</p>

        <div class="card" >
            <div class="content" >
                <div class="card_in_project" >
                    <div class="status" >Реализована</div>
                    <p class="text_in_card" >Какой то написанный текст</p>
                </div>
                <div class="card_in_project" >
                    <div class="status" >Реализована</div>
                    <p class="text_in_card" >Вместо цвета будет картинка, но её нет, вот</p>
                </div>
                <div class="card_in_project" >
                    <div class="status" >Реализована</div>
                    <p class="text_in_card" >Текст "реализована" опционален ? </p>
                </div>
                <div class="card_in_project" >
                    <div class="status" >Реализована</div>
                    <p class="text_in_card" >Ну как то так</p>
                </div>
            </div>
            <p class="more" >Подробнее</p>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
.card_in_project{
    width: 234px;
    height: 157px;
    background: burlywood;
    border-radius: 5px;
    margin-left: 5px;
    margin-right: 5px;
    position: relative;
    display: flex;
    justify-content: start;
    align-items: flex-end;

}
.text_in_card{
    padding: 10px;
    color: #fff;
    line-height: 17px;
}
.status{
    position: absolute;
    background: #00A560;
    border-radius: 1px;
    padding-left: 5px;
    padding-right: 5px;
    color: #fff;
    font-size: 15px;
    top: 15px;
}
.content{
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    height: calc(100% - 47px);
    padding-left: 20px;
    padding-right: 20px;
}
.BulletinOfTheProject{
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
    height: 257px;

    background: #FFFFFF;

    /* shadow */
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    position: relative;
}
.more{
    position: absolute;
    width: 87px;
    height: 14px;
    right: 18px;
    bottom: 20px;

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
    