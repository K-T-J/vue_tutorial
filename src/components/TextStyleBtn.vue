<template>
  <div class="text__style">
    <span class="textstyle__txt">텍스트 스타일 변경</span>
    <div id="textstyle__btn__container" :ref="refTextStyleBtns" class="btns">
      <button class="btn text__btn text__shadow" @click="textShadowBtn">
        텍스트 그림자
      </button>
      <button class="btn text__btn text__invert" @click="textInvertBtn">
        텍스트 색상 반전
      </button>
      <button class="btn text__btn text__size" @click="textSizeBtn">
        제목 크기 작게
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TextStyleBtn",
  data() {
    return {
      textStyleBtns: null,
    };
  },
  methods: {
    refTextStyleBtns(el) {
      this.textStyleBtns = el.children;
    },
    textShadowBtn(e) {
      const renderTxt = document.querySelectorAll(".render");
      e.target.classList.toggle("selected"); // .toggle()은 선택한 요소가 보이면 보이지 않게, 보이지 않으면 보이게 한다
      renderTxt.forEach((item) => {
        if (e.target.classList.contains("selected")) {
          //contains() : 텍스트 검색
          item.style.textShadow = "2px 2px 4px rgba(0,0,0,0.4)";
        } else {
          item.style.textShadow = "";
        }
      });
    },
    textInvertBtn(e) {
      e.target.classList.toggle("selected");

      const renderTxt = document.querySelectorAll(".render");
      const prevSubtitle = document.querySelector(".subtitle");

      renderTxt.forEach((item) => {
        if (e.target.classList.contains("selected")) {
          //contains() : 텍스트 검색
          item.style.color = "black";
          prevSubtitle.style.borderTop = "1px solid #000000";
        } else {
          item.style.color = "#ffffff";
          prevSubtitle.style.borderTop = "1px solid #ffffff";
        }
      });
    },
    textSizeBtn(e) {
      const renderTxt = document.querySelectorAll(".render");
      const prevTitle = document.querySelector(".title");
      const prevSubtitle = document.querySelector(".subtitle");
      const prevCategory = document.querySelector(".category");

      e.target.classList.toggle("selected");

      renderTxt.forEach(() => {
        if (e.target.classList.contains("selected")) {
          prevTitle.style.fontSize = "46px";
          prevSubtitle.style.fontSize = "22px";
          prevCategory.style.fontSize = "22px";
        } else {
          prevTitle.style.fontSize = "54px";
          prevSubtitle.style.fontSize = "24px";
          prevCategory.style.fontSize = "24px";
        }
      });
    },
  },
  beforeUpdate() {
    this.textStyleBtns = null;
  },
};
</script>
<style></style>
