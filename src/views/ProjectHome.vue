<template>
  <div class="body">
    <section class="wrapper">
      <article class="contents">
        <header>
          <h1># Thumbnail Maker</h1>
          <p>썸네일 메이커 v 1.2.1 - velog format</p>
          <div class="author">
            <a class="logo" href="https://naver.com" target="_blank">
              <img src="../assets/img/logo_thumbnail.jpg" />
              <span class="user">kimtaejun</span>
            </a>
          </div>
        </header>
        <MainContent
          :inputTitle="inputTitle"
          :inputSubTitle="inputSubTitle"
          :inpuThirdTitle="inpuThirdTitle"
        />
        <div class="control__panel">
          <InputText
            @firstTitleValue="firstTitleValue"
            @subTitleValue="subTitleValue"
            @thirdTitleValue="thirdTitleValue"
          />
          <BackgroundBtn />
          <ThumbnailBtn />
          <TextStyleBtn />
          <MasterBtn />
        </div>
      </article>
      <div class="copyright">
        <a href="https://naver.com" target="_blank">
          <p class="me">ⓒ Wonkook Lee</p>
          <p class="unsplash">Images from Unsplash</p>
        </a>
      </div>
    </section>
  </div>
</template>

<script>
//import HomeFooter from '../components/Footer.vue'
import MainContent from "../components/MainContent.vue";
import InputText from "../components/InputText.vue";
import BackgroundBtn from "../components/BackgroundBtn.vue";
import ThumbnailBtn from "../components/ThumbnailBtn.vue";
import TextStyleBtn from "../components/TextStyleBtn.vue";
import MasterBtn from "../components/MasterBtn.vue";
//import html2canvas from 'html2canvas';
export default {
  components: {
    //HomeFooter
    MainContent,
    InputText,
    BackgroundBtn,
    ThumbnailBtn,
    TextStyleBtn,
    MasterBtn,
  },
  data() {
    return {
      inputTitle: "제목을 입력하세요",
      inputSubTitle: "부제목을 입력하세요",
      inpuThirdTitle: "분류를 입력하세요",
    };
  },
  methods: {
    firstTitleValue(value) {
      this.inputTitle = value;
    },
    subTitleValue(value) {
      this.inputSubTitle = value;
    },
    thirdTitleValue(value) {
      console.log("value > ", value);
      this.inpuThirdTitle = value;
    },
  },
};
</script>

<style>
@import "../assets/css/projectStyle.css";
</style>
