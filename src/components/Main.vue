<template>
  <div class="main" >
    <Login :host='this.host' v-if="is_login" @tologin='to_login' @toreg='toReg' />  
    <Registration :host='this.host' v-if="is_reg" @tologin='to_login' @toreg='toReg' />  
    <Header @tologin='to_login' />
    <SubHeader/>
    <StagesAndStatus :host='this.host' />
    <Modal v-if="modal" :data='data_for_modal' @tomodal='to_modal' />
    <ShareIdea :host='this.host'  v-if="is_share_idea" :data='data_for_share_idea' @shareidea='shareidea' @updateideas='updateideas' />
    <BulletinOfTheProject :host='this.host'  @tomodal='to_modal' @shareidea='shareidea' :ideas_array='ideas_array' />
    <SayThanks v-if="is_say_thanks"  @saythanks='saythanks' />
    <AwardBadge v-if="is_awardbadge"  @awardbadge='awardbadge' />
    <ProjectProgressBar :host='this.host' @saythanks='saythanks' @awardbadge='awardbadge' />
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
import ShareIdea from './ShareIdea'
import SayThanks from './SayThanks'
import AwardBadge from './AwardBadge'



export default {
  name: 'HelloWorld',
  props: {
    host: {}
  },
  data() {
    return {
      is_login: false,
      is_reg: false,
      is_say_thanks: false,
      is_awardbadge: false,
      is_say_thanks_array: {},
      modal: false,
      data_for_modal: {},
      data_for_share_idea: {},
      is_share_idea: false,
      ideas_array: []
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
    Modal,
    ShareIdea,
    SayThanks,
    AwardBadge
  }, 
  mounted() {
    this.get_ideas()
  },
  methods: {
    get_ideas() {
            fetch(this.host + 'get_ideas', {
                headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json'
                },
                method: "GET"
            })
            .then(response => response.text())
            .then((response) => { 
                this.ideas_array = JSON.parse(response)['ideas']
                console.log(this.ideas_array);
            })
            .catch(err => console.log(err))
        },
    updateideas() {
      this.get_ideas()
      this.is_share_idea = !this.is_share_idea;
      document.body.style.overflowY = 'auto';
    },
    shareidea(data) {
      this.is_share_idea = !this.is_share_idea;
      if (data) {
        this.data_for_share_idea = data;
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }
    },
    saythanks(data) {
      this.is_say_thanks = !this.is_say_thanks;
      if (data) {
        this.data_for_share_idea = data;
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }
    },
    awardbadge(data) {
      this.is_awardbadge = !this.is_awardbadge;
      if (data) {
        document.body.style.overflowY = 'hidden';
      } else {
        document.body.style.overflowY = 'auto';
      }
    },
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
