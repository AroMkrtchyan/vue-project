<template>
  <div class="Header-container">
    <div class="logo-container">
        <router-link to="/"><img src="../assets/logo.svg" alt="LOGO" class="logo"></router-link>
    </div>
    <div :class="{navBarWrapper : true , show: isOpenNavList}" >
      <span class="headerNavCloser closer" @click="isOpen">X</span>
      <ul class="navBar">
        <li>
          <router-link to="/" >Home</router-link>
        </li>
        <li>
          <router-link to="/about" exact >About</router-link>
        </li>
        <li>
          <router-link to="/portfolio" exact >Portfolio</router-link>
        </li>
        <li>
          <router-link to="/contact" exact >Contact</router-link>
        </li>
      </ul>
    </div>
    <div class="burger closer" @click.stop="isOpen">
      <div class="burgerLine burgerLine1"></div>
      <div class="burgerLine burgerLine2"></div>
      <div class="burgerLine burgerLine3"></div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
     isOpenNavList: false
    }
  },
  mounted() {
    document.addEventListener('click',  ()=>{
      if (this.isOpenNavList){
        this.isOpenNavList = false
        console.log(this.isOpenNavList)
      }
    })
  },
  methods:{
    isOpen(){
      this.isOpenNavList = !this.isOpenNavList
    },
  }
}
</script>



<style scoped>
    .Header-container {
        background: rgba(176, 224, 230, 0.94);
        height: 80px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 15px;
    }
    .logo {
        width: 55px;
    }
    .navBar{
        list-style-type: none;
        display: flex;
        align-items: center;
    }
    .navBar > li {
        font-size: 20px;
        margin-right: 20px;
    }
    .navBar > li > a {
        text-decoration: none;
        color: #3867aa;
        transition: 0.7s;
    }
    .navBar > li > a.router-link-active,
    .navBar > li > a:hover {
        color: #ff0000;
    }
    .closer {
      display: none;
    }
    @media (max-width: 600px) {
      .navBarWrapper {
        position: absolute;
        top: 0;
        right: -300px;
        background: rgb(176, 224, 230);
        min-height: 500px;
        padding: 20px 50px;
        border-bottom-left-radius: 150px;
        transition: all .7s ease;
      }
      .navBar {
        flex-direction: column;
      }
      .navBarWrapper > .navBar > li {
        margin-right: 0;
        width: 100%;
        text-align: center;
        line-height: 60px;
        border-bottom: 1px solid #ccc;
      }
      .navBar > li > a {
        padding: 10px 0;
      }
      .headerNavCloser {
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 16px;
        font-weight: bold;
        cursor: pointer;
        background: #ccc;
        width: 25px;
        height: 25px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
      }
      .burger {
        cursor: pointer;
      }
      .burgerLine {
        width: 30px;
        height: 5px;
        background: #5d5d5d;
        margin-bottom: 3px;
        border-radius: 3px;
      }
      .closer {
        display: flex;
        flex-direction: column;
      }
      .show{
        right: 0;
      }
    }
</style>

