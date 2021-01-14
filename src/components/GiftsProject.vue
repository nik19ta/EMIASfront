<template>
    <div class="StagesAndStatus">
        <div class="Status">
            <p class="title"> Подарки проекта</p>
            <div class="card">
                <div class="content_for_photo">
                    <p>Если ты в команде ЕМИАС</p>
                    <img class="img" src="../assets/png/Bobromania_shop_2.png" alt="">
                </div>
                <div class="content_for_photo">
                    <p>Если у тебя два бэйджа</p>
                    <img class="img" src="../assets/png/croc_t_shirt_noman1.png" alt="">
                </div>
                <div class="content_for_photo">
                    <p>Если ты поделился лайфхаком/идеей</p>
                    <img class="img" src="../assets/png/Bobromania_shop_3.png" alt="">
                    <img class="img" src="../assets/png/Bobromania_shop.png" alt="">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
.StagesAndStatus {
    width: 100%;
    display: flex;
    justify-content: center;
}

.Status {
    padding-left: 70px;
    padding-right: 70px;
    width: 100%;
}

.title {
    margin-top: 74px;
    font-family: Croc;
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    line-height: 103.4%;
}

.card {
    margin-top: 27px;
    width: 100%;
    /* height: 220px; */

    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.img {
    margin-left: 9.5px;
    width: 190px
}

.content_for_photo {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}

.content_for_photo p {
    font-size: 18px;
    width: 100%;
    text-align: center;
}

@media screen and (min-width: 1550px) {
    .Status {
        min-width: 1550px;
        max-width: 1550px;

    }
}

@media screen and (max-width: 850px) {
    .Status {
        padding-left: 30px;
        padding-right: 20px;
    }

    .content_for_photo {
        width: 100%;
    }

    .card {
        flex-wrap: wrap;
    }

    .content_for_photo p {
        font-size: 20px;
        width: 100%;
        text-align: left;
    }

    .content_for_photo p::after {
        content: ':';
    }
}
@media screen and (max-width: 465px) {
    .Status{
        padding-left: 10px;
        padding-right: 10px;
    }
}
</style>