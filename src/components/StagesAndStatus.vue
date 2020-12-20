<template>
    <div class="StagesAndStatus" >
        <div class="Status" >
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
                        <div v-for="i in stages" :key="i" :class="[i < stages ? 'item' : '']" >
                            <div class="point" :class="[i == actual_stage ? 'now_point' : i < actual_stage ? 'done_point' : 'not_point']" ></div>
                            <div v-if="i < stages" class="line" :class="[i < actual_stage ? 'done_line' : 'not_line']"  ></div>
                        </div>
                    </div>
                    <div class="content_div" >
                        <img src="../assets/finish.svg" alt="">
                        <p class="text">Финиш</p>
                    </div>
                </div>
                <p @click='open' class="more" >{{text}}</p>

                <div id='div' class="center" > 
                    <div  class="map" >
                        <iframe src="https://yandex.ru/map-widget/v1/?um=constructor%3Adb52615e4ba013599c00400374ecf0c8225ca41074dd5d09aaf9d455dbb5f0f4&amp;source=constructor" width="800" height="450" frameborder="0"></iframe>
                    </div>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import $ from 'jquery'

export default {
    props: {
        host: {}
    },
    data: function() {
        return {
            actual_stage: 0,
            stages: 0,
            text: 'Подробнее'
        }
    },
    mounted() {
        const vm = this;
        fetch(this.host + 'project_status', {
            headers: {
                'Accept': 'application/json',
                'Content-Type': 'application/json'
            },
            method: "GET",
        })
        .then(response => response.text())
        .then((response) => {
            response = JSON.parse(response)
            vm.actual_stage = response.status.actual_stage;
            vm.stages = response.status.stages;
        })
        .catch(err => console.log(err))
    },
    methods: {
        open() {
            $(`div#div`).slideToggle();
            if (this.text == "Подробнее") {
                this.text = 'Свернуть'
            } else {
                this.text = "Подробнее"
            }
        }
    }
}
</script>


<style scoped>
.center{
    display: none;
    width: 100%;
    justify-content: center;
}
.map{
    height: 500px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.item{
    display: flex;
    width: 100%;
    position: relative;
    justify-content: space-around;
}
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
    width: 70%;
}
.not_line {
    background: #C4C4C4;
    width: 70%;
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
    margin-top: 45px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: calc(100% - 47px);
    padding-left: 20px;
    padding-right: 20px;
}
.StagesAndStatus{
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    /* padding-left: 70px; */
    /* padding-right: 70px; */
}
.Status{
    width: 100%;
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
    min-height: 220px;

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

    cursor: pointer;

    /* or 16px */
    text-decoration-line: underline;

    color: #00A560;
}
@media screen and (min-width: 1550px) {
    .Status{
        min-width: 1550px;
        max-width: 1550px;

    }    
}
@media screen and (max-width: 850px) {
    .Status{
        padding-left: 30px;
        padding-right: 30px;
    }
}
</style>
