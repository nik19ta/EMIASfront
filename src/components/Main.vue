<template>
  <div class="main" >
    <Header/>
    <SubHeader/>
    <StagesAndStatus/>
    <BulletinOfTheProject/>
    <ProjectProgressBar/>
    <GiftsProject/>
  </div>
</template>

<script>
import Header from './Header.vue'
import SubHeader from './SubHeader'
import StagesAndStatus from './StagesAndStatus'
import BulletinOfTheProject from './BulletinOfTheProject.vue'
import ProjectProgressBar from './ProjectProgressBar.vue'
import GiftsProject from './GiftsProject.vue'


export default {
  name: 'HelloWorld',
  components: {
    Header,
    SubHeader,
    StagesAndStatus,
    BulletinOfTheProject,
    ProjectProgressBar,
    GiftsProject
  }
}
</script>


<style scoped>
.main {
  min-height: 100vh;
  padding-bottom: 30px;
}
</style>
