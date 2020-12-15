<template>
    <div class="login" >
        <div class="ModalWindow" >
                <h1 class="title" >Регистрация</h1>
                <form>
                    <input id="login" type="text" placeholder="login" >  <br/>
                    <input type="password" id="password" placeholder="password" > <br/>
                    <input type="text" id="email" placeholder="email" > <br/>
                    <button v-on:click="submit" >Зарегистрироватся</button> <br/>
                    <p v-on:click="to_login" class="to_reg" >Уже есть аккаунт</p>
                    <button class="close" v-on:click="closed" >×</button> <br/>
                </form>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        host: {}
    },
    data: function () {
        return {
            actual_stage: 0,
            stages: 0
        }
    },
    mounted() {},
    methods: {
        closed() {
            this.$emit('close')
            this.$emit('toreg', false)
            this.$emit('tologin', false)
        },
        to_reg() {
            this.$emit('tologin', false)
            this.$emit('toreg', true)
        },
        submit(event) {
            event.preventDefault();
            fetch(this.host + 'registration', {
                    headers: {
                        'Accept': 'application/json',
                        'Content-Type': 'application/json'
                    },
                    method: "POST",
                    body: JSON.stringify({
                        login: document.querySelector('#login').value,
                        password: document.querySelector('#password').value,
                        email: document.querySelector('#email').value
                    })
                })
                .then(response => response.text())
                .then((response) => {
                    if (JSON.parse(response).status == 'not a unique login') {
                        alert("Пользователь с таким логином уже зарегистрирован.")
                    } else if (JSON.parse(response).status == 'ok') {
                        alert("Вы успешно зарегестрировались")
                        document.cookie = `user=${JSON.parse(response)['cookie']}`;
                    } else {
                        alert('error')
                    }
                    console.log(response);
                })
                .catch(err => console.log(err))
        },
        to_login() {
            console.log(1);
            this.$emit('toreg', false)
            this.$emit('tologin', true)
        },
    }
}
</script>
<style scoped>
.login{
    position: absolute;
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
    width: 450px;
    height: 500px;
    background: #fff;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
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
    margin-top: 10px;
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
    top: -30px;
    right: 2px;
    padding: 0;
    border: 0;
    width: 40px;
    height: 40px;
    background: #fff;
    cursor: pointer;
    color: rgb(30, 197, 100);
    font-size: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.to_reg{
    color: rgb(30, 197, 100) ;
    text-align: center;
    margin-top: 5px;
    cursor: pointer;
}
</style>