<template>
  <div class="main" >
    <Login :host='this.host' v-if="is_login" @tologin='to_login' @toreg='toReg' />  
    <Reg :host='this.host' v-if="is_reg" @tologin='to_login' @toreg='toReg' />  
    <Header @tologin='to_login' />
    <SubHeader/>
    <StagesAndStatus :host='this.host' />
    <BulletinOfTheProject/>
    <ProjectProgressBar :host='this.host' />
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
import Login from './Login.vue'
import Reg from './Reg.vue'


export default {
  name: 'HelloWorld',
  props: {
    host: {}
  },
  data() {
    return {
      is_login: false,
      is_reg: false,
    }
  },
  components: {
    Header,
    SubHeader,
    StagesAndStatus,
    BulletinOfTheProject,
    ProjectProgressBar,
    GiftsProject,
    Login,
    Reg
  }, 
  methods: {
    to_login(data) {
      this.is_login = data;

      // When the modal is shown, we want a fixed body
      // document.body.style.position = 'fixed';
      if (data) {
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }

      // When the modal is hidden, we want to remain at the top of the scroll position
      // document.body.style.position = '';
      // document.body.style.top = '';
    },
    toReg(data) {
      this.is_reg = data;

      // When the modal is shown, we want a fixed body
      // document.body.style.position = 'fixed';
      if (data) {
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }
    }
  }
}
</script>


<style scoped>
.main {
  min-height: 100vh;
  padding-bottom: 30px;
}
</style>
