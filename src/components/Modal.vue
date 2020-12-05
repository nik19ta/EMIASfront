<template>
    <div class="login" >
        <div class="ModalWindow" >
                <h1 class="title" >{{data.title}}</h1>
                <img class="image" :src="data.img">
                <p >{{data.text}}</p>
                <button class="close" v-on:click="closed" >×</button> <br/>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        data: {}
    },
    data: function () {
        return {
            // data: {}
        }
    },
    mounted() {},
    methods: {
        closed() {
            this.$emit('tomodal', false)
        }
    }
}
</script>
<style scoped>
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
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    padding: 20px;
    overflow-y: auto;
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
    position: fixed;
    /* top:30px; */
    margin-top: -550px;
    margin-right: -790px;
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