<template>
  <div class="inputFields">
    <input
      type="text"
      class="input__field input__title"
      @keyup="firstTitle"
      data-set="title"
      spellcheck="false"
      placeholder=">제목을 입력하세요"
    />
    <input
      type="text"
      class="input__field input__subtitle"
      @keyup="subTitle"
      data-set="subtitle"
      spellcheck="false"
      placeholder=">부제목을 입력하세요"
    />
    <input
      type="text"
      class="input__field input__category"
      @keyup="thirdTitle"
      data-set="category"
      spellcheck="false"
      placeholder=">분류를 입력하세요"
    />
  </div>
</template>

<script>
export default {
  name: "InputText",
  data() {
    return {};
  },
  methods: {
    firstTitle(e) {
      this.$emit("firstTitleValue", e.target.value);
    },
    subTitle(e) {
      this.$emit("subTitleValue", e.target.value);
    },
    thirdTitle(e) {
      this.$emit("thirdTitleValue", e.target.value);
    },
  },
};
</script>
