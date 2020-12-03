<template>
    <div v-if="people.role == role" class="user">
        <div class="name">
            <div v-if="people.photo == null" class="avatar"></div>
            <div v-else> <img :src="people.photo" alt=""> </div>
            <div class="people_name">{{people.name}}</div>
        </div>
        <div class="Badges">
            <!-- {{people.Badges.length == 0 ? 'Пока что нет.' : people.Badges.length}} -->
            <div class="Badge_div" v-for="Badge in people.Badges" :key='Badge.code' >
                <img class="Badges_img" v-if="people.Badges.length != 0" :src="require(`../assets/png_for_BulletinOfTheProject/${Badge.code}.svg`)" alt="">
                <span class="Badge_count" >
                    x{{Badge.count}}
                </span>
            </div>
            <!-- {{people.Badges}} -->
        </div>
        <div class="Like">{{people.like.length}}</div>
        <div class="Ideas">{{people.ideas.length}}</div>
        <div class="Thanks">{{people.thanks.length}}</div>
    </div>
</template>

<script>
    export default {
        name: 'ProjectProgressBar',
        props: {
            people: {},
            role: {}
        },
    }
</script>

<style  scoped>
.Badge_count{
    margin-left:5px;
}
.Badge_div{
    display: flex;
    align-items:flex-end;
    margin-right: 10px;
}
.Badges_img{
    width: 45px;
    height: 45px;
}
.user{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-bottom: 10px;
    margin-top: 10px;
}
.avatar{
    width: 50px;
    height: 50px;
    background: -webkit-linear-gradient(45deg, rgb(0, 165, 96), rgb(0, 158, 165) 65%);
    background: -moz-linear-gradient(45deg, rgb(0, 165, 96), rgb(0, 158, 165) 65%);
    background: linear-gradient(45deg, rgb(0, 165, 96), rgb(0, 158, 165) 65%);
    border-radius: 100px;
}
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
}
.name{
    width: 30%;
}
.name{
    display: flex;
    justify-content: flex-start;
}
 .Badges{
    width: 38%;
    display: flex;
}
 .Like{
    width: 10%;
}
 .Ideas{
    width: 10%;
}
.Thanks{
    width: 12%;
}
</style>