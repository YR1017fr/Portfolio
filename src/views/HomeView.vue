<template>
  <v-app id="home">
    <v-container fluid>
      <div class="head">
        <v-row>
          <v-col cols="12" sm="5">
            <div style="position: relative" class="mt-16">
              <p class="text-white text-h3">魏宏瑋</p>
              <p class="text-grey text-h4 mt-2">Fontend Developer</p>
            </div>
          </v-col>
        </v-row>
      </div>
      <v-col cols="12" class="mt-16 px-16 d-flex flex-column align-center" id="about">
        <p class="mt-16 text-h4">關於我</p>
        <div class="divider bg-light-blue-darken-3 mb-6"></div>
        <v-row class="px-16">
          <v-col cols="12" sm="6">
            <p class="text-grey">畢業於國立成功大學土木系，因緣際會下踏上前端工程師的道路，喜歡有挑戰性的工作</p>
            <p class="text-grey">主要使用Vue + elementUI進行網頁開發，亦使用過React、Vuetify、Tailwind等前端/CSS框架。</p>
            <p class="text-grey">有許多與後端、PM溝通的經驗，也曾使用Express.js架設基礎的後端</p>
            <p class="text-grey">參與過使用uni-app、LIFF的專案</p>
            <br />
            <v-btn tile dark color="light-blue-darken-4" class="mt-4" @click="downloadResume">
              Download Resume
            </v-btn>
          </v-col>
          <v-col cols="12" sm="6" class="d-flex flex-column">
            <div class="time-line">
              <p>創蹟數位科技有限公司- 減災動資料平台前端程式修正(React)</p>
              <p>艾立斯科技股份有限公司- 網頁前端工程師(Vue)
                <br>(2022.02 ~ 在職)
              </p>
            </div>
          </v-col>
        </v-row>
      </v-col>


      <v-col cols="12" id="portfolio">
        <div class="pre">
          <div class="text-center mt-16 pt-10 d-flex flex-column align-center">
            <p class="text-h4">作品</p>
            <div class="divider bg-light-blue-darken-3 mb-6"></div>
          </div>
          <v-row class="justify-center">
            <v-col cols="12" sm="6">
              <v-hover v-slot="{isHovering, props}" v-for="(item, index) in projects" :key="index">
                <v-card :elevation="isHovering ?12 :2" class="mw-auto" v-bind="props">
                  <v-carousel
                    cycle
                    height="250"
                    :show-arrows="false"
                    hide-delimiter-background
                    show-arrows-on-hover>
                    <v-carousel-item v-for="(img, index2) in item.images" :key="index2" class="bg-light-blue-lighten-2">
                      <v-img :src="img" height="250px" contain></v-img>
                    </v-carousel-item>
                  </v-carousel>
                  <v-card-title class="text-h5">
                    <a :href="item.url" target="_blank" class="project-name">
                       {{item.name}}
                    </a>
                    <a :href="item.url" target="_blank">
                      <v-img src="@/assets/images/github.png" height="20px" width="20px" contain class="d-inline-flex"/>
                    </a>
                  </v-card-title>
                  <v-card-subtitle class="text-h6">{{item.finishDate}}</v-card-subtitle>
                  <v-card-text>
                    {{item.description}}
                  </v-card-text>
                  </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-container>
    <Footer-view/>
  </v-app>
</template>

<script>
import { defineComponent } from "vue"

// Components
import FooterView from "@/components/FooterView.vue"

export default defineComponent({
  name: "HomeView",
  components: {
    FooterView
  },
  setup() {
    const downloadResume = () => {
      window.open('https://docs.google.com/document/d/1Cs7L1nqNIRm25rS-VHILOD_P9DErPtMajVaXr6VgLCU/export?format=pdf')
    }

    const projects = [
      {
        name: '部落格模板',
        images: [
          require('@/assets/images/project1-1.png'),
          require('@/assets/images/project1-2.png'),
          require('@/assets/images/project1-3.png')
        ],
        url: 'https://fireblogs-bb0a0.firebaseapp.com/',
        gitUrl: 'https://github.com/YR1017fr/FireBlog/',
        finishDate: 'Aug 2022',
        description: `以Vue建構多個可重複使用的組件完成網站畫面，使用Firebase提供後端服務讓用戶可登入、新增/修改發文。
        (註: 因沒有fileServer，上傳圖片皆改為固定圖片)`
      }
    ]
    return {
      projects,
      downloadResume
    };
  },
});
</script>

<style scoped>
.divider {
  height: 20px;
  width: 20px;
  border-radius: 10px;
  position: relative;
}

.divider::before {
  content: '';
  position: absolute;
  width: 100px;
  height: 5px;
  top: calc(50% - 2.5px);
  right: 20px;
  background-color: #0277bd;
}

.divider::after {
  content: '';
  position: absolute;
  width: 100px;
  height: 5px;
  top: calc(50% - 2.5px);
  left: 20px;
  background-color: #a0cce6;
}

.v-container {
  padding: 0;
}

.v-card-text {
  padding: 20px 10%;
  font-size: 16px;
  text-align: left; 
  white-space:pre-line;
}

.v-carousel-item {
  background-color: #c8c8c8;
}

.head {
  position: relative;
  text-align: center;
  margin-bottom: 6px;
  height: 250px;
  width: 100%;
  color: white;
  background-color: black;
}

.head::before {
  content: "";
  position: absolute; 
  top: 99%;
  right: 0;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 125px 100vw 0 0;
  border-color: black transparent transparent transparent;
}


.first {
  width: 100%;
  height: 280px;
  text-align: center;
  padding: 2rem;
}

.pre {
  width: 100%;
  text-align: center;
  background-color: #F5F5F5;
}

.time-line > p {
  margin: 20px 10px 20px 30px;
  position: relative;
}

.time-line > p:first-of-type {
  margin-top: 0;
}

.time-line > p:last-of-type {
  margin-bottom: 0;
}

.time-line > p::before {
  content: "";
  width: 24px;
  height: 24px;
  border-radius: 12px;
  border: 3px grey solid;
  background: white; 
  position: absolute; 
  left: -29px; 
  top: calc(50% - 12px);
}

.time-line > p::after {
  content: "";
  width: 5px;
  height: 100px;
  border-radius: 10px;
  background: grey; 
  position: absolute; 
  left: -20px; 
  top: calc(50% - 10px);
  z-index: -1;
}

.project-name,
.project-name:active,
.project-name:focus {
  color: black;
}
</style>
