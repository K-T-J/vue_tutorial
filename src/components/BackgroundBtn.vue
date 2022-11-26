<template>
  <div class="background__btns">
    <span class="background__txt">배경을 정해주세요</span>
    <div :ref="refContainer" id="background__btn__container" class="btns">
      <button class="btn random__gradient" @click="randomGradient">
        랜덤 그라디언트
      </button>
      <button class="btn random__solid" @click="randomSolid">랜덤 단색</button>
      <button class="btn img__url" @click="imgUrl">이미지 URL</button>
      <v-btn>test</v-btn>
    </div>
  </div>
</template>

<script>
export default {
  name: "BackgroundBtn",
  data() {
    return {
      backgroundBtns: null,
      randomGradientBtn: null,
      randomSolidBtn: null,
      imgUrlBtn: null,
      domBody: document.body,
      preview: null,
    };
  },
  methods: {
    refContainer(el) {
      this.backgroundBtns = el.children;
    },
    refGradint(el) {
      this.randomGradientBtn = el;
    },
    refSolid(el) {
      this.randomSolidBtn = el;
    },
    refImgUrl(el) {
      this.imgUrlBtn = el;
    },
    randomRGB() {
      let rgb = "";
      rgb += (Math.floor(Math.random() * 90 + 1) + 150)
        .toString(16)
        .padStart(2, "0");
      rgb += (Math.floor(Math.random() * 90 + 1) + 150)
        .toString(16)
        .padStart(2, "0");
      rgb += (Math.floor(Math.random() * 90 + 1) + 150)
        .toString(16)
        .padStart(2, "0");
      return rgb;
    },
    randomGradient() {
      this.preview = document.querySelector(".preview");
      const rgb1 = this.randomRGB();
      const rgb2 = this.randomRGB();

      this.selectedNow(this.randomGradientBtn);
      this.domBody.style.background = `linear-gradient(to bottom, #${rgb1}, #${rgb2})`;
      this.preview.style.background = `linear-gradient(to bottom, #${rgb1}, #${rgb2})`; // linear-gradient: 두 개 이상의 색상 간의 점진적 전환으로 구성된 이미지를 만듬
    },
    randomSolid() {
      this.preview = document.querySelector(".preview");
      const rgb = this.randomRGB();
      this.selectedNow(this.randomSolidBtn);
      this.domBody.style.background = this.preview.style.background = "";
      this.domBody.style.backgroundColor =
        this.preview.style.backgroundColor = `#${rgb}`;
    },
    imgUrl() {
      this.preview = document.querySelector(".preview");
      const regex =
        /((([A-Za-z]{3,9}:(?:\/\/)?)(?:[-;:&=\\+\\$,\w]+@)?[A-Za-z0-9.-]+(:[0-9]+)?|(?:www.|[-;:&=\\+\\$,\w]+@)[A-Za-z0-9.-]+)((?:\/[\\+~%\\/.\w-_]*)?\??(?:[-\\+=&;%@.\w_]*)#?(?:[\w]*))?)/;
      let imgUrl = prompt("이미지 주소를 입력하세요 😇");
      if (imgUrl == null) return; //취소 눌렀을 때 알림이 발생하지 않도록 수정
      if (!imgUrl.match(regex)) {
        //match : 문자열이 정규식과 매치되는 부분을 검색
        alert("올바르지 않은 URL입니다 😨");
        return;
      }

      this.domBody.style.background =
        this.preview.style.background = `url('${imgUrl}')`;
      this.domBody.style.backgroundSize = this.preview.style.backgroundSize =
        "cover"; //cover : 배경을 사용하는 요소를 다 채울 수 있게 이미지를 확대 또는 축소한다 가로 세로 비율을 유지한다
      this.domBody.style.backgroundRepeat =
        this.preview.style.backgroundRepeat = "no-repeat"; // background-repeat : 배경 이미지의 반복 여부와 반복 방향을 정한다 no-repeat : 반복하지 않는다
      this.domBody.style.backgroundPosition =
        this.preview.style.backgroundPosition = "center"; // background-Position : 배경 이미지의 위치를 정하는 속성

      this.selectedNow(this.imgUrlBtn);
    },
    //selected 속성
    selectedNow(value) {
      for (let i = 0; i < this.backgroundBtns.length; i++) {
        this.backgroundBtns[i].classList.remove("selected");
      }
      value.classList.add("selected");
    },
  },
  beforeUpdate() {
    this.randomGradientBtn = null; //초기화
    this.randomSolidBtn = null;
    this.imgUrlBtn = null;
  },
};
</script>
