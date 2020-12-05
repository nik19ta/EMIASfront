<template>
  <div class="main" >
    <Login :host='this.host' v-if="is_login" @tologin='to_login' @toreg='toReg' />  
    <Registration :host='this.host' v-if="is_reg" @tologin='to_login' @toreg='toReg' />  
    <Header @tologin='to_login' />
    <SubHeader/>
    <StagesAndStatus :host='this.host' />
    <Modal v-if="modal" :data='data_for_modal' @tomodal='to_modal' />
    <BulletinOfTheProject :host='this.host'  @tomodal='to_modal'  />
    <ProjectProgressBar :host='this.host' />
    <GiftsProject/>
  </div>
</template>

<script>
import Registration from './Registration.vue'
import Modal from './Modal'
import Header from './Header.vue'
import SubHeader from './SubHeader'
import StagesAndStatus from './StagesAndStatus'
import BulletinOfTheProject from './BulletinOfTheProject.vue'
import ProjectProgressBar from './ProjectProgressBar.vue'
import GiftsProject from './GiftsProject.vue'
import Login from './Login.vue'


export default {
  name: 'HelloWorld',
  props: {
    host: {}
  },
  data() {
    return {
      is_login: false,
      is_reg: false,
      modal: false,
      data_for_modal: {}
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
    Registration,
    Modal
  }, 
  methods: {
    to_modal(data) {
      this.modal = !this.modal;
      if (data) {
        this.data_for_modal = data; 
      }
      if (data) {
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }
    },
    to_login(data) {
      this.is_login = data;
      if (data) {
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }
      
    },
    toReg(data) {
      this.is_reg = data;
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
