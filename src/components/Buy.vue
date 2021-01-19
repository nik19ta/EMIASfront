<template>
    <div class="login" >
        <div class="ModalWindow" >
            <div class="title__div" >
                <p>Заказать мерч </p>
                <button class="close" v-on:click="closed" >×</button> <br/>
            </div>
            <div class="content" >
                <img class="img-m" :src="require(`../assets/png/${search_merch(data)['img']}`)" alt="">
                <p class="text" >Вы можете получить {{search_merch(data)['p_name']}} если {{search_merch(data)['rule']}} </p>

                <button @click='closed()' >Получить!</button>
                <!-- <button class="inactive" >Получить!</button> -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        host: {},
        data: {}
    },
    data: function () {
        return {
            text: '',
            people: '',
            merch: {
                1: {
                    img: 'Bobromania_shop_2.png',
                    name: 'Маска',
                    p_name: 'Маску',
                    id: 1,
                    rule: "если ты в команде ЕМИАС"
                },
                2: {
                    img: 'croc_t_shirt_noman1.png',
                    name: 'Футболка',
                    p_name: 'Футболку',
                    id: 2,
                    rule: "если у тебя два бэйджа"
                },
                3: {
                    img: 'Bobromania_shop_3.png',
                    name: 'Чашка',
                    p_name: 'чашку',
                    id: 3,
                    rule: "если ты поделился лайфхаком/идеей"
                },
                4: {
                    img: 'Bobromania_shop.png',
                    name: 'Чашка',
                    p_name: 'чашку',
                    id: 4,
                    rule: "если ты поделился лайфхаком/идеей"
                }
            }
        }
    },
    mounted() {},
    methods: {
        search_merch(id) {
            return this.merch[id]
        },
        buy() {
            this.$emit('buy', false)
        },
        closed() {
            alert('Успех')
            this.$emit('buy', false)
        }
    }
}
</script>
<style scoped>

.content{
    width: 100%;
    height: calc(100% - 60px);
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    flex-direction: column;
    gap: 20px;
}
textarea{
    padding: 10px;
    font-family: Croc;
    resize: none;
    width: calc(100% - 40px);
    height: 65%;
    background: #fff;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    border: 0;
    font-size: 18px;
}
.title__div{
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    background: #00A560;
    height: 60px;
    width: 100%;
    position: relative;
    display: flex;
    align-items: center;
    padding-left: 20px;
    padding-right: 20px;
    color: #fff;
    font-size: 24px;
}
.image{
    width: 400px;
    margin-bottom: 20px;
    margin-top: 20px;
}
.login{
    position: fixed;
    top: 0;
    height: 100vh;
    width: 100vw;
    background: rgba(0,0,0,0.3);
    z-index: 3;
    display: flex;
    justify-content: center;
    align-items: center;
}
.ModalWindow{
    position: relative;
    width: 850px;
    height: 600px;
    background: #fff;
    border-radius: 10px;
    /* display: flex; */
    /* justify-content: center; */
    /* align-items: center; */
    /* flex-wrap: wrap; */
    /* padding: 20px; */
    /* overflow-y: auto; */
}
input, button{
    padding: 5px;
    background: #fff;
    width: 250px;
    height: 30px;
    border: 1.5px solid rgb(30, 197, 100);
    border-radius: 5px;
    font-size: 14px;
    color: #000;
    /* margin-top: 10px; */
}
button{
    background: rgb(30, 197, 100);
    color: #fff;
    margin-top: 30px;
    text-align: center;
}

form{
    margin-top: -220px;
}
.title{
    width: 100%;
    text-align: center;
    color: rgb(30, 197, 100)
}
.close{
    position: absolute;
    right: 10px;
    cursor: pointer;
    top: -25px;
    width: 40px;
    height: 40px;
    color: #fff;
    font-size: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: transparent;
    vertical-align: middle;
    border: 0;
}
.to_reg{
    color: rgb(30, 197, 100) ;
    text-align: center;
    margin-top: 5px;
    cursor: pointer;
}
.btns_inline{
    width: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-wrap: nowrap;
    align-items: center;
}
.btn{
    cursor: pointer;
    margin: 0;
    margin-left: 20px;
    width: 150px;
    background: #fff;
    border: 0;
    color: rgb(30, 197, 100);
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
}
.cancel{
    color: #E1E1E1;
}
.input{
    padding: 10px;
    font-family: Croc;
    resize: none;
    width: calc(100% - 40px);
    height: 10%;
    background: #fff;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    border: 0;
    font-size: 18px;
}
.select{
   border: 0 
}
.img-m{
    width: 125px;
    border-radius: 5px;
}
button{
    cursor: pointer;
}
.text{
    width: 100%;
    text-align: center;
}
.inactive{
    background: #f5f5f5;
    color: #5c5c5c;
    border-color: #f5f5f5;
}
</style>