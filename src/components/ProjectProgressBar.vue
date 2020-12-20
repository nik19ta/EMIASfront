<template>
    <div class="ProjectProgressBar" >
        <div class="ProgressBar" >

            <div class="title"> 
                <p>Прогрессбар проекта</p>
                <div class="btns" >
                    <button @click="saythings_modal" class="btn" > <p class="text_btn">Сказать спасибо</p></button>
                    <button @click="awardbadge" class="btn" > <p class="text_btn">Вручить бейдж</p></button>
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

                <div class="row" @click='open(1)' >
                    <p>Администраторы</p>
                    <img src="../assets/mdi_keyboard_arrow_down.svg" v-bind:class="[isClosed1 ? 'opened' : 'closed', 'transition']" alt="">
                </div>
                <div id='div1' class="content" style="display : none"  >
                    <div v-for="people in people_array" :key="people.id" >
                        <people :people='people' role='Администратор' />
                    </div>
                </div>
                <div class="row" @click='open(2)' >
                    <p>Тимлиды</p>
                    <img src="../assets/mdi_keyboard_arrow_down.svg" v-bind:class="[isClosed2 ? 'opened' : 'closed', 'transition']" alt="">
                </div>
                <div id='div2' class="content"  style="display : none" >
                    <div v-for="people in people_array" :key="people.id" >
                        <people :people='people' role='Тимлид' />
                    </div>
                </div>
                <div class="row"  @click='open(3)' >
                    <p>Координаторы</p>
                    <img src="../assets/mdi_keyboard_arrow_down.svg" v-bind:class="[isClosed3 ? 'opened' : 'closed', 'transition']" alt="">
                </div>
                <div id='div3' class="content" style="display : none"  >
                    <div v-for="people in people_array" :key="people.id" >
                        <people :people='people' role='Координатор' />
                    </div>
                </div>
                <div class="row" @click='open(4)'>
                    <p>Технические специалисты</p>
                    <img src="../assets/mdi_keyboard_arrow_down.svg" v-bind:class="[isClosed4 ? 'opened' : 'closed', 'transition']" alt="">
                </div>
                <div id='div4' class="content" style="display : none"  >
                    <div v-for="people in people_array" :key="people.id" >
                        <people :people='people' role='Технический специалист' />
                    </div>
                </div>
                <div class="row" @click='open(5)'>
                    <p>Аналитики</p>
                    <img src="../assets/mdi_keyboard_arrow_down.svg" v-bind:class="[isClosed5 ? 'opened' : 'closed', 'transition']" alt="">
                </div>
                <div id='div5' class="content" style="display : none"  >
                    <div v-for="people in people_array" :key="people.id" >
                        <people :people='people' role='Аналитик' />
                    </div>
                </div>
                <div class="row" @click='open(6)' >
                    <p>Консультанты </p>
                    <img src="../assets/mdi_keyboard_arrow_down.svg" v-bind:class="[isClosed6 ? 'opened' : 'closed', 'transition']" alt="">
                </div>
                <div id='div6' class="content" style="display : none"  >
                    <div v-for="people in people_array" :key="people.id" >
                        <people :people='people' role='Консультант' />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import $ from 'jquery'
import people from './People'

export default {
    name: 'ProjectProgressBar',
    props: {
        host: {}
    },
    components: {
        people
    },
    mounted() {
        this.get_people()
    },
    data: function() {
        return {
            isClosed1: false,
            isClosed2: false,
            isClosed3: false,
            isClosed4: false,
            isClosed5: false,
            isClosed6: false,
            people_array: []
        }
    },
    methods: {
        awardbadge() {
            this.$emit('awardbadge', {"data":this.people_array})
        },
        saythings_modal() {
            this.$emit('saythanks', {"data":this.people_array})
        },
        get_people() {
            fetch(this.host + 'get_people', {
                headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json'
                },
                method: "GET"
            })
            .then(response => response.text())
            .then((response) => { 
                this.people_array = JSON.parse(response)['status']
                console.log(this.people_array);
                })
            .catch(err => console.log(err))
        },
        open(data) {
            this[`isClosed${data}`] = !this[`isClosed${data}`]
            
            for (let i = 0; i < 6; i++) {
                if (this[`isClosed${i + 1}`] == true && `isClosed${i + 1}` != `isClosed${data}`) {
                    $(`div#div${i + 1}`).slideToggle();
                    this[`isClosed${i + 1}`] = false
                }
            }

            $(`div#div${data}`).slideToggle();
        }
    }
}
</script>

<style scoped>
.people_name {
    margin-left: 10px;
}
.name{
    align-items: center;
}
.content{
    height: 200px;
    padding-left: 10px;
    padding-right: 10px;
    overflow-y: auto;
}
.Team_title, .name{
    width: 30%;
}
.name{
    display: flex;
    justify-content: flex-start;
}
.Badges_title, .Badges{
    width: 38%;
}
.Like_title, .Like{
    width: 10%;
}
.Ideas_title, .Ideas{
    width: 10%;
}
.Thanks_title, .Thanks{
    width: 12%;
}

/* <!-- 30% --><!-- 38% --><!-- 10% --><!-- 10% --><!-- 12% --> */

.row {
    padding-left: 10px;
    padding-right: 10px;
    height: 54px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    cursor: pointer;
}

.ProjectProgressBar{
    width: 100%;
    display: flex;
    justify-content: center;
}
.ProgressBar{
    width: 100%;
    padding-left: 70px;
    padding-right: 70px;
    border-radius: 10px;
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
    height: auto;

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
.transition {
    transition: all 0.3s;
}
.closed {
    transform: rotate(0deg);
    }
.opened {
    transform: rotate(180deg);
}

button {
    cursor: pointer;
}

@media screen and (min-width: 1550px) {
    .ProgressBar{
        min-width: 1550px;
        max-width: 1550px;

    }    
}
@media screen and (max-width: 850px) {
    .ProgressBar{
        padding-left: 30px;
        padding-right: 30px;
    }
}
@media screen and (max-width: 750px) {
    .Team_title, .name{
    width: 30%;
    }
    .Badges_title, .Badges{
        width: 31%;
    }
    .Like_title, .Like{
        width: 14%;
    }
    .Ideas_title, .Ideas{
        width: 14%;
    }
    .Thanks_title, .Thanks{
        width: 11%;
    }
}
</style>
    