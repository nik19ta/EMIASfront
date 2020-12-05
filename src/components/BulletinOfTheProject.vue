<template>
    <div class="BulletinOfTheProject" >
        <div class="Project" >
            <p class="title"> Вестник проекта</p>

            <div class="card" >
                <div v-if="!is_more" class="content" >
                    <div 
                    v-for="item in data" 
                    :key="item.title" 
                    class="card_in_project" 
                    :style="`background-image: url(${item.img})`" >
                        
                        <div v-if="item.status" class="status" >Реализованно</div>
                        <p class="text_in_card" >{{item.title}}</p>
                    </div>
                </div>

                <div v-if="is_more" class="main" >
                    <div class="left" >
                        <button class="share__idea" >Поделиться идеей</button>

                        <div class="center" >
                            <img src="../assets/like.svg" alt="">
                            лайк идее 
                            <pre> </pre>
                            <img src="../assets/settings.svg" alt="">
                            лайк идее
                        </div>

                        <div class="name__idea" >
                            Название лайфхака
                        </div>
                        <div class="name__idea" >
                            Название лайфхака
                        </div>
                        <div class="name__idea" >
                            Название лайфхака
                        </div>
                        <div class="name__idea" >
                            Название лайфхака
                        </div>
                        <div class="name__idea" >
                            Название лайфхака
                        </div>

                    </div>
                    <div class="right" >
                        <div  class="content_more" >
                            <div 
                                v-for="item in data" 
                                :key="item.title" 
                                @click="() => to_modal(item)"
                                class="card_in_project_more" >

                            <div v-if="item.status" class="status" >Реализованно</div>
                            <img class="more__img" :src="item.img" alt="">

                            <p class="text__card__more item__title " >{{item.title}}</p>
                            <p class="text__card__more" >{{item.text.substr(0, 200) + '...'}}</p>


                            </div>
                        </div>
                    </div>
                </div>

                <p class="more" @click="more" >{{ is_more ? 'Свернуть' : 'Подробнее'}}</p>
            </div>
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
            data: [],
            is_more: false
        }
    },
    mounted() {
        this.get_data()
    },
    methods: {
        to_modal(data) {
            this.$emit('tomodal', data)
        },
        more(){
            this.is_more = !this.is_more;
        },
        get_data() {
            const vm = this;
            fetch(this.host + 'bulletin_project', {
                headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json'
                },
                method: "GET",
            })
            .then(response => response.text())
            .then((response) => {
                response = JSON.parse(response)
                vm.data = response.status;
            })
            .catch(err => console.log(err))
        }
    }
}
</script>
<style scoped>
.name__idea{

    display: flex;
    align-items: center;
    padding: 10px;
    margin-top: 10px;

    width: 303px;
    height: 61px;
    background: #FFFFFF;

    /* shadow */
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
}
.center{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 10px;
    margin-top: 30px;
    margin-bottom: 30px;
    width: 100%;
    padding-left: 15%;
}
.share__idea{
    border: 0;

    height: 40px;
    width: 220px;

    color: #fff;
    font-size: 14px;

    cursor: pointer;

    background: #00A560;

    /* shadow */
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
}
.more__img{
    border-radius: 5px;
}
.main{
    display: flex;
    align-items:flex-start;
}
.left{
    width: 30%;
    height: 100px;
    padding-left: 20px;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
.right{
    width: calc(100% - 30%);
    display: flex;
    justify-content: space-around;
    align-items: flex-start;
    flex-wrap: wrap;
}
.item__title{
    font-weight: bold;
    margin-top: 50px ;
}
.more__img{
    /* height: 200px; */
    width: 100%;
}
.text__card__more{
    padding-left: 5px;
    padding-right: 5px;
}
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
    background-size: cover;
}
.card_in_project_more{
    width: 256px;
    height: 450px;
    margin-bottom: 20px;
    background: burlywood;
    border-radius: 5px;
    margin-left: 5px;
    margin-right: 5px;
    position: relative;
    display: flex;
    justify-content: start;
    align-items: flex-start;
    background-size: cover;
    background: #FFFFFF;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    flex-wrap: wrap;
    margin-right: 20px;
    margin-left: 20px;
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
.content_more {
    display: flex;
    justify-content:center;
    align-items: center;
    width: 100%;
    max-width: 800px;
    /* height: 470px; */
    padding-left: 20px;
    padding-right: 20px;
    flex-wrap: wrap;
}
.BulletinOfTheProject{
    display: flex;
    justify-content: center;
}
.Project{
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
    padding-top: 30px;
    padding-bottom: 50px;

    background: #FFFFFF;

    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    position: relative;
}
.more{
    cursor: pointer;

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
@media screen and (min-width: 1900px) {
    .Project{
        min-width: 1700px;
        max-width: 1700px;
    }    
}
@media screen and (min-width: 1600px) {
    .Project{
        min-width: 1700px;
        max-width: 1700px;
    }    
}
</style>
    