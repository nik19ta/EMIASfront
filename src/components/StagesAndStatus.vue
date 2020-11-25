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
                    <p class="text">Старт</p>
                </div>
                <div class="progress" >
                    <div class="point done_point " ></div>
                    <div class="line done_line" ></div>
                    <div class="point done_point" ></div>
                    <div class="line done_line" ></div>
                    <div class="point done_point" ></div>
                    <div class="line done_line" ></div>
                    <div class="point done_point" ></div>
                    <div class="line done_line" ></div>
                    <div class="point done_point" ></div>
                    <div class="line done_line" ></div>
                    <div class="point done_point" ></div>
                    <div class="line done_line" ></div>
                    <div class="point now_point" ></div>
                    <div class="line not_line" ></div>
                    <div class="point not_point" ></div>
                    <div class="line not_line" ></div>
                    <div class="point not_point" ></div>
                    <div class="line not_line" ></div>
                    <div class="point not_point" ></div>
                </div>
                <div class="content_div" >
                    <img src="../assets/finish.svg" alt="">
                    <p class="text">Финиш</p>
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
.point{
    width: 18px;
    height: 18px;
    border-radius: 100%;
    margin-top: calc(-18px/2 + 1px);
    /* background: #00A560; */
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
}
.line{
    width: calc((100% - 60px - 60px)/10);
}
.done_line{
    background: #00A560;
}
.not_line {
    background: #C4C4C4;
}
.done_point{
    background: #00A560;
}
.now_point{
    background: #FFFFFF;
    border: 1px solid #00A560;
    box-shadow: 0px 3.96667px 22.8083px -2.975px rgba(0, 0, 0, 0.1);
}
.now_point::before {
    content: "";
    display: block;
    /* position: absolute; */
    background: #00A560;
    border-radius: 100%;
    width: 9px;
    height: 9px;
    /* margin-top: calc(-9px/2 + 1px); */
}

.not_point{
    background: #FFFFFF;
    border: 1px solid #C4C4C4;
    box-sizing: border-box;
}

.text {
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
    /* background: #00A560; */
    display: flex;
    justify-content: space-between;
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
