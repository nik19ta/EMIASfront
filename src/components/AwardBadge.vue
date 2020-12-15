<template>
    <div class="login" >
        <div class="ModalWindow" >
            <div class="title__div" >
                <p>Вручить бэйдж</p>
                <button class="close" v-on:click="closed" >×</button> <br/>
            </div>
            <div class="content" >
                <select id='people' class="input select ">
                    <option :value='item.name' v-for='item in awardbadge_array.data' :key='item.name' >{{item.name}}</option>
                </select>

                <p>Выберите бейдж который хотите вручить</p>
                <div class="assets_b" >
                    <span v-for="i in 11" :key="i">
                        <img v-bind:class="badge == i ? 'active' : 'an'" @click="chenge_b(i)" class="icon" :src="require(`../assets/png_for_BulletinOfTheProject/${i}.svg`)" alt="">
                    </span>
                </div>

                <div class="btns_inline" >
                    <button v-bind:class="badge < 1 ? 'dis_clacc' : ''" v-on:click="say" class="btn" >Вручить</button>
                    <button v-on:click="closed"  class="btn cancel " >Отмена</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        awardbadge_array: {},
        host: {}
    },
    data: function () {
        return {
            text: '',
            badge: 0
        }
    },
    mounted() {},
    methods: {
        chenge_b(data) {
            if (this.badge == data) {
                this.badge = 0;
            } else {
                this.badge = data;
            }
        },
        say() {
            if (this.badge < 1) {
                alert('Бэйдж не выбран!')
            } else {
                fetch(this.host + 'award_badge', {
                    headers: {
                        'Accept': 'application/json',
                        'Content-Type': 'application/json'
                    },
                    method: "POST",
                    body: JSON.stringify({
                        from: "user..",
                        badge: this.badge,
                        to: document.querySelector('#people').value
                    })
                })
                .then(response => response.text())
                .then((response) => { 
                    console.log(response) 
                    if (JSON.parse(response).status == 'ok') {
                        alert('Успех')
                        this.$emit('awardbadge')
                    }
                })
                .catch(err => console.log(err))
            }

        },
        closed() {
            this.$emit('awardbadge')
        }
    }
}
</script>
<style scoped>

.content{
    width: 100%;
    height: calc(100% - 60px);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
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
.icon{
    width: 45px;
    cursor: pointer;
    transition:width .3s, margin 0.2s;
}
.assets_b{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
    height: 25%;
}
.assets_b p{
    width: 100%;
    text-align: center;
}
.active{
    width: 65px;
    margin-top: -10px;
    margin-right: 0px;
}
.dis_clacc{
    color: gray;
}
</style>