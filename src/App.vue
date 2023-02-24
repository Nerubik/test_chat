<template>
  <div class="container">
    <header-user :header="header"/>
    <div class="info-block">
      <p class="info-text">Add new member</p>
      <div class="info-message">
        <div class="info-left">
          <img src="../src/assets/images/user.png" alt="user icon" class="user-icon">
          <p class="user-name">David Tennant</p>
        </div>
        <div class="round"></div>
        <img src="../src/assets/images/info.png" alt="user icon" class="info-icon">
      </div>
      <under-buttons :buttons="infoButtons"/>
      <div class="views">
        <img src="../src/assets/images/eye.png" alt="eye icon" class="eye">
        <span class="views-count">1</span>
      </div>
    </div>
    <div class="wrapper">
      <mess-list :messages="messages"/>
    </div>
    <form class="input-mes" @submit.prevent>
      <img src="../src/assets/images/user.png" alt="user icon" class="user-icon">
      <input type="text" placeholder="Add comment" :value="body" @keypress.enter="sendMess">
    </form>
  </div>
</template>

<script>
import MessList from "@/components/MessList.vue";
import HeaderUser from "@/components/HeaderUser.vue"
import UnderButtons from "@/components/UnderButtons.vue";
export default {
  name: 'App',
  data() {
    return {
      header: {name: "Bitrix24", date: "16 january 09:23"},
      messages: [
        {id: 1, name: 'David', time: '11:30', body: 'Hi, Rose'},
        {id: 2, name: 'David', time: '11:32', body: 'I am a time traveler'},
        {id: 3, name: 'David', time: '11:35', body: 'It is my TARDIS'},
      ],
      body: '',
      infoButtons: [
        {id: 1, name: 'Like'},
        {id: 2, name: 'Comment'},
        {id: 3, name: 'Stop view'},
        {id: 4, name: 'More'}
      ]
    }
  },
  methods: {
    sendMess(e) {
      if (e.target.value == '') return;
      let wrapper = document.querySelector('.wrapper');
      let date = new Date();
      const newMess = {
        id: Date.now(),
        name: 'David',
        time: `${date.getHours()}:${date.getMinutes()}`,
        body: e.target.value
      }
      this.messages.push(newMess);
      e.target.value = '';
      wrapper.scrollTop = wrapper.scrollHeight;
    },
  },
  components: {
    MessList, HeaderUser, UnderButtons
  }
}
</script>

<style>
  * {
    margin: 0;
    font-size: 16px;
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    padding: 0;
    box-sizing: border-box;
  }
  .user-icon {
    height: 50px;
    width: 50px;
    margin-right: 15px;
  }
  .info-icon {
    width: 50px;
    border: 8px solid white;
    border-radius: 50%;
    z-index: 1;
  }
  .container {
    padding: 20px;
    width: 700px;
    margin: 20px;
    min-height: 600px;
    border-radius: 10px;
    box-shadow: 0px 0px 15px rgb(71, 71, 71);
  }
  .info-block {
    position: relative;
    margin-left: 65px;
    margin-top: 15px;
    margin-bottom: 20px;
  }
  .info-text {
    margin-bottom: 15px;
  }
  .info-message {
    position: relative;
    display: flex;
    align-items: center;
    padding: 30px;
    justify-content: space-between;
    background-color: #f3fed6;
    border-radius: 20px;
    margin-bottom: 15px;
  }
  .info-left {
    display: flex;
    align-items: center;
  }
  .user-name {
    color: blueviolet;
    font-weight: bold;
  }
  .input-mes {
    margin-left: 65px;
    display: flex;
    align-items: center;
    width: calc(100% - 65px);
  }
  input {
    width: 100%;
    height: 40px;
    padding: 0 20px;
    border-radius: 20px;
    border: 1px solid rgb(200, 200, 200);
  }
  .wrapper {
    max-height: 294px;
    overflow: auto;
  }
  .round {
    position: absolute;
    z-index: 0;
    bottom: -35px;
    right: 30px;
    width: 240px;
    height: 120px;
    background-color: #f3fed6;
    border-top: 30px solid #ebfac1;
    border-left: 30px solid #ebfac1;
    border-right: 30px solid #ebfac1;
    border-radius: 50% 50% 0 0 / 100% 100% 0 0;
  }
  .round::before {
    content: '';
    position: absolute;
    height: 35px;
    bottom: 0;
    left: -35px;
    right: -35px;
    background-color: white;
  }
  .views {
    display: flex;
    position: absolute;
    bottom: 0;
    left: 225px;
    align-items: center;
  }
  .eye {
    width: 17px;
    margin-right: 3px;
  }
  .views-count {
    font-size: 14px;
    color: #858585;
  }
</style>
