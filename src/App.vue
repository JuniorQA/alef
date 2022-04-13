<template>
  <div id="app">
    <div class="flex wrapper">
    <header>
      <div class="header-container flex">
        <div>
          <img class='logo' src="@/assets/Logo_imi_horizontal.png"> 
        </div>
        <div class="header-nav">
          <ul class="flex">
            <li><a href="#">Форма</a></li>
            <li><a href="#">Превью</a></li>
          </ul>
        </div>
      </div>
    </header>
    <section class="main">
    <section>
    <div class="main-container">
      <h2 class="main-header">Персональные данные</h2>
      <mainInput v-for="(item, index) in placeholderCredentials"
                  v-bind:key = 'item'
                  v-bind:index = 'index'
                  v-bind:item = 'item' 

      />
    </div>
    </section>
    <section class="childs">
      <div class="main-container">
        <div class="flex space-between no-wrap">
          <h2 class="main-header">Дети (макс.5)</h2>
          <div class="btn-container flex align-items-center relative">
            <div>
              <button class="add-btn flex justify-content-end"
                      v-on:click='addItem()'>
                <div class="plus"></div>
                Добавить ребенка
              </button>
            </div>
          </div> 
        </div>
            <credentialGroup  v-bind:childQuantity = 'childQuantity' 
                              v-for = "item in childQuantity"
                              v-bind:key = 'item'
                              v-bind:item = 'item'
                              v-bind:placeholderCredentials = 'placeholderCredentials'
            />
        <button class="save-btn" v-on:click= 'save()'>Сохранить</button>
      </div>
    </section>
    </section>
    <footer>
      <p>all rights reserved</p>
    </footer>
    </div>
  </div>
</template>

<script>

import credentialGroup from '@/components/credentialGroup'
import mainInput from '@/components/input'


export default {
  name: 'App',
  data(){
    return{
       placeholderCredentials: ["Имя", "Возраст"],
       childQuantity : 2,
       personalCredentials : {
        name: 'petr',
        age : '',
       },
       inputValue: '',
    }
  },
  methods: {
   addItem(){
   // if (this.childQuantity < 5) {
      this.childQuantity++;
   // }
   },
   save(){
    let childs = [];
    childs.length = this.childQuantity;
    for (let i = 0; i < childs.length; i++) {
      childs[i] = {
        name: 'Ivan',
        age : '20',
      }
    }
    console.log(this.personalCredentials.name);
    console.log(childs[1].name);
   }
  },
  components: {
    credentialGroup,
    mainInput
  }
}
</script>

<style>
  body{
    height: 100%;
    background-color: #FFFFFF;
    padding: 0;
    margin: 0;
    font-family: 'Montserrat';
    font-size: 14px;
  }
  header{
    border-bottom: 1px solid #F2F2F2;
  }
  .logo{
    width: 175px;
    height: 32px;
  }
  .header-container{
    margin: 25px 90px;
  }
  .flex{
    display: flex;
  }
  .header-nav{
    margin: 0 auto;
  }
  .header-nav ul li{
    list-style: none;
  }
  .header-nav ul li a{
    text-decoration: none;
    color: #111111;
    margin: 24px;
  }
  @font-face {
    font-family: "Montserrat";  
    src: url("~@/assets/fonts/Montserrat-VariableFont_wght.ttf") format("truetype"); 
    font-style: normal; 
    font-weight: normal; 
} 
.main-container{
  margin: 45px auto;
  width: 50%;
}
.main-input{
  width: 100%;
  height: 56px;
  border: 1px solid #F1F1F1;
  border-radius: 4px;
  font-family: "Montserrat";
  margin: 10px 0;
  padding: 0 10px;
  font-size: 150%;
  min-width: 100px;
}
.main-input::placeholder{
  padding-top: 8px;
  padding-left: 16px;
}
.main-input:focus::-webkit-input-placeholder {position: absolute; top: 0; font-size: 75%; transition: 0.5s;}
.main-input:focus::-moz-placeholder          {position: absolute; top: 0; font-size: 75%; transition: 0.5s;}
.main-input:focus:-moz-placeholder           {position: absolute; top: 0; font-size: 75%; transition: 0.5s;}
.main-input:focus:-ms-input-placeholder      {position: absolute; top: 0; font-size: 75%; transition: 0.5s;}

.main-header{
  margin: 20px 0px;
  white-space: nowrap;
}
.space-between{
  justify-content: space-between;
}
.childs .main-input{
  width: 40%;
  margin: 10px 18px;
}
.add-btn{
  width: 205px;
  height: 45px;
  border: 2px solid #01A7FD;
  border-radius: 100px;
  font-family: "Montserrat";
  background-color: #FFFFFF;
  font-size: 14px;
  white-space: nowrap;
  padding: 20px;
  color: #01A7FD;
  line-height: 50%;
  cursor: pointer;
}
.plus {cursor: pointer; position: absolute; top: 33px; left: 12px;}
.plus:before, .plus:after {content: ""; position: absolute; width: 16px; height: 2px; background: #01A7FD;}
.plus:before {transform: rotate(0deg);}
.plus:after {transform: rotate(-90deg);}


.align-items-center{
  align-items: center;
}
.justify-content-center{
  justify-content: center;
}
.relative{
  position: relative;
}
.justify-content-end{
  justify-content: flex-end;
}

.delete-btn{
  width: 60px;
  height: 24px;
  color: #01A7FD;
  border: none;
  background-color: #FFF;
  font-size: 14px;
  font-family: "Montserrat";
  cursor: pointer;
  padding-top: 50%;
}
.no-wrap{
  flex-wrap: nowrap;
}
.save-btn{
  width: 120px;
  height: 45px;
  background-color: #01A7FD;
  border-radius: 100px;
  padding: 10px 20px;
  color: #FFFFFF;
  font-size: 14px;
  font-family: "Montserrat";
  border: none;
  margin-top: 20px;
  cursor: pointer;
}
footer{
  background-color: #FAFAFA;
  height: var(--footer-height);
  font-size: 13px;
  font-family: "Montserrat";
  text-align: center;
  --footer-height: 76px;
}
footer p{
  padding: 0;
  margin: 0;
  line-height: var(--footer-height);
}
.wrapper{
  flex-direction: column;
  min-height: 100vh;
}
.main{
  flex: 1 1 auto;
}
.display-none{
  display: none;
}
</style>
