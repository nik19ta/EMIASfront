<template>
    <div class="login" >
        <div class="ModalWindow" >
            <div v-if="loader_up" class="loader_bc" >
                <Loader v-if="loader_up" />
            </div>
            <h2 class="title" >Профиль</h2>
            <button class="close" v-on:click="closed" >×</button> <br/>
            <button class="exit_from_acc" v-on:click="exit" >Выйти из аккаунта</button> <br/>

            <Loader v-if="fetch_is == 0" />

            <div v-if="user_data != null && fetch_is > 0" class="content" >  
                <div class="info" >
                    <div class="avatar_div" >
                        <div id="avatar" class="avatar" v-if="user_data.data.photo == null" ></div>
                        <img class="avatar_img" v-if="user_data.data.photo != null" :src="user_data.data.photo" alt="">
                    </div>
                    <div class="main_info" >
                        <p>{{user_data.data.name}}</p>
                        <p class="role" >{{user_data.data.role}}</p>
                    </div>
                </div>
                <input v-if="is_btn_chenge_avatar" type="file" class="input_file" @change="previewFiles" multiple placeholder="Поменять аватар" > 
                <button v-if="!is_btn_chenge_avatar" @click="chenge_is_btn_chenge_avatar" class="input_file" > Поменять аватар </button>
                <div class="form_div" >
                        <button v-if="!is_btn_edit_pass" @click="chenge_btn_edit_pass" class="btn_form_div" >Поменять пароль</button>
                        <input v-if="is_btn_edit_pass" v-model="new_pass" placeholder="Новый пароль" class="btn_form_div" type="text">
                        <button v-if="is_btn_edit_pass" @click="pass_ok" class="btn_form_div" > ok </button>
                    </div>
                <p>Доступные бэйджи:</p>
                <div class="Badges_content" >
                    <span class="Badges" v-for="item in user_data.data.Badges" :key="item.code" >
                        <img class="Badges_img" :src="require(`../assets/png_for_BulletinOfTheProject/${item.code}.svg`)" alt="">
                        <span class="Badge_count" >x{{item.count}}</span>
                    </span> 
                </div>
                <div class="blocks">
                    <div>
                        <p class="info_p" >Лайки: {{user_data.data.like.length}} </p>
                        <p class="info_p" >Идеи: {{user_data.data.ideas.length}} </p>
                        <p class="info_p" >Спасибо: {{user_data.data.thanks.length}} </p>
                        <p class="info_p" >Очки: {{user_data.data.points}} </p>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
import Loader from './Loader'

export default {
    props: {
        host: {}
    },
    components: {
        Loader
    },
    data: function () {
        return {
            actual_stage: 0,
            stages: 0,
            name: "",
            user_data: null,
            fetch_is: 0,
            loader_up: false,
            is_btn_chenge_avatar: false,
            is_btn_edit_pass: false,
            new_pass: ''
        }
    },
    mounted() {
        this.get_info()
    },
    methods: {
        chenge_btn_edit_pass() {this.is_btn_edit_pass = !this.is_btn_edit_pass},
        chenge_is_btn_chenge_avatar() {this.is_btn_chenge_avatar = !this.is_btn_chenge_avatar},
        pass_ok() {
            this.chenge_btn_edit_pass()
            fetch(this.host + 'passwd', {
                    headers: {
                        'Accept': 'application/json',
                        'Content-Type': 'application/json'
                    },
                    credentials: 'include',
                    mode: 'cors',
                    method: "POST",
                    body: JSON.stringify({
                        pass: this.new_pass,
                        cookie: document.cookie.split('=')[1]
                    })
                })
                .then(response => response.text())
                .then((response) => {
                    if (JSON.parse(response).status == 'ok') {
                        alert('Успех')
                    } else {
                        alert('Ошибка')
                    }
                })
                .catch(err => console.log(err))
        },
        async previewFiles(event) {
            const toBase64 = file => new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.readAsDataURL(file);
                reader.onload = () => resolve(reader.result);
                reader.onerror = error => reject(error);
            });
            this.user_data.data.photo = await toBase64(event.target.files[0]);


            this.chenge_is_btn_chenge_avatar()
            this.chenge(this.user_data.data.photo)
        },
        chenge(img_data) {
            console.log(img_data);
            this.loader_up = true

            fetch(this.host + 'chenge_img', {
                    headers: {
                        'Accept': 'application/json',
                        'Content-Type': 'application/json'
                    },
                    credentials: 'include',
                    mode: 'cors',
                    method: "POST",
                    body: JSON.stringify({
                        img: img_data,
                        cookie: document.cookie.split('=')[1]
                    })
                })
                .then(response => response.text())
                .then((response) => {
                    if (JSON.parse(response).status == 'ok') {
                        setTimeout(() => {
                            this.loader_up = false
                        }, 300)
                    } else {
                        this.loader_up = false
                    }
                })
                .catch(err => console.log(err))
        },
        exit() {
            let vm = this;
            fetch(this.host + 'exit', {
                        headers: {
                            'Accept': 'application/json',
                            'Content-Type': 'application/json'
                        },
                        credentials: 'include',
                        method: "POST",
                        body: JSON.stringify({"cookie":document.cookie.split('=')[1]})
                    })
                    .then(response => response.text())
                    .then((response) => {
                        console.log(JSON.parse(response)['data']);
                        console.log('ok');
                        console.log(JSON.parse(response)['data'] == 'ok');
                        if (JSON.parse(response)['data'] == 'ok') {
                            vm.closed()
                            localStorage.name = "false";
                            document.cookie = `user=false`;
                        } else {
                            alert('Error')
                        }
                    })
                    .catch(err => console.log(err))

        },
        get_info() {
            if (document.cookie.split('=')[1] == "false") {
                this.$emit('tologinfromlk')
            } else {
                fetch(this.host + 'information_about_user', {
                        headers: {
                            'Accept': 'application/json',
                            'Content-Type': 'application/json'
                        },
                        credentials: 'include',
                        method: "POST",
                        body: JSON.stringify({"cookie":document.cookie.split('=')[1]})
                    })
                    .then(response => response.text())
                    .then((response) => {
                        if (!JSON.parse(response)['data']) {
                            this.$emit('tologinfromlk')
                        } else {
                            this.fetch_is = 1
                            this.user_data = JSON.parse(response);
                        }
                    })
                    .catch(err => console.log(err))
            }
        },
        closed() {
            this.$emit('toprof')
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
    align-items: flex-start;
    flex-wrap: wrap;
    padding: 20px;
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
    cursor: pointer;
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
.exit_from_acc{
    background: transparent;
    color: rgb(30, 197, 100);
    border: 0;
    cursor: pointer;
    position: absolute;
    bottom: 10px;
}

.Badges_img{
    width: 35px;
}
.content{
    width: 100%;
    height: 80%;
}
.Badges_content{
    margin-top: 5px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 10px;
}
.avatar{
    width: 100px;
    height: 100px;
    background: -webkit-linear-gradient(45deg, rgb(0, 165, 96), rgb(0, 158, 165) 65%);
    background: -moz-linear-gradient(45deg, rgb(0, 165, 96), rgb(0, 158, 165) 65%);
    background: linear-gradient(45deg, rgb(0, 165, 96), rgb(0, 158, 165) 65%);
    border-radius: 100px;
}
.avatar_img{
    width: 100px;
    height: 100px;
    border-radius: 100px;
}
.info{
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: flex-start;
    padding-bottom: 5px;
}
.main_info{
    width: calc(100% - 100px - 20px);
}
.info_p{
    margin-top: 7px;
}
.loader_bc{
    background: #0002;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 5;
    border-radius: 9px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.input_file{
    margin: 0;
}
.role{
    margin-top: 10px;
}
.blocks{
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}
.form_div{
    width: 250px;
    display: flex;
    align-items: flex-end;
    height: 35px;
    gap: 10px;
    margin-bottom: 20px;
}
.btn_form_div{
    width: 100%;
}
</style>