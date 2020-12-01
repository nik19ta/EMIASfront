<template>
    <div class="sub_header" >
        <div class="header" >
            <div class="text_box" >
                <p class="text" >Проект, который создает добро</p>
            </div>
            <div class="image_box" >
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
}
.text_box, 
.image_box {
    display: flex;
    justify-content: center;
    align-items: center;
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
@media screen and (min-width: 1900px) {
    .header{
        min-width: 1600px;
        max-width: 1600px;
    }    
}
</style>