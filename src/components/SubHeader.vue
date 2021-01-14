<template>
    <div class="sub_header">
        <div class="header">
            <div class="text_box">
                <p class="text">КИС ЕМИАС - дорога в цифровое будущее</p>
            </div>
            <div class="image_box">
                <img src="../assets/sub_header_image.svg" alt="">
            </div>
        </div>
    </div>
</template>

<script>
</script>

<style scoped>
.sub_header {
    background: #FFFFFF;
    height: 220px;
    display: flex;
    justify-content: center;
}
.header{
    display: flex;
    justify-content: center;
    align-self: center;
    min-width: 100%;
    /* min-width: 1200px; */
    /* max-width: 1900px; */
    /* display: flex; */
    /* justify-content: space-between; */
    /* align-self: center; */
}
.text_box{
    width: 60%;
}
.image_box{
    width: 40%;
    /* margin-right: 50px; */
}
.text_box, 
.image_box {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding-right: 50px;
}
.text{
    font-family: Croc;
    font-style: normal;
    font-weight: 300;
    font-size: 36px;
    line-height: 103.4%;
    width: 100%;
    margin-left: 70px;

    /* or 37px */

    color: #2B2B2B;
}

@media screen and (min-width: 1550px) {
    .header {
        min-width: 1550px;
        max-width: 1550px;

    }
}

@media screen and (max-width: 850px) {
    .text{
        margin-left: 30px;
    }
}
@media screen and (max-width: 650px) {
    .sub_header {
        position: relative;
    }
    .image_box {
        position: absolute;
        right: 0px;
        top: 0px;
        opacity: .3;
        width: 90%;
    }
    .text_box {
        width: 100%;
        z-index: 1;
    }
    img {
        max-width: 300px;
        min-width: 300px;
    }
}
@media screen and (max-width: 465px) {
    .text{
        margin-left: 10px;
    }
}
</style>