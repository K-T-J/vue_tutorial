<template>
  <div
    id="capture"
    class="preview"
    style="
      background: url(https://images.unsplash.com/photo-1620121478247-ec786b9be2fa?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1489&q=80)
        center center / cover no-repeat rgb(120, 170, 249);
    "
  >
    <ul class="components" id="comp__opt1">
      <li
        class="render title"
        style="color: rgb(255, 255, 255); font-size: 54px"
      >
        {{ inputTitle }}
      </li>
      <li
        class="render subtitle"
        style="
          color: rgb(255, 255, 255);
          border-top: 1px solid rgb(255, 255, 255);
          font-size: 24px;
        "
      >
        {{ inputSubTitle }}
      </li>
      <li
        class="render category"
        style="color: rgb(255, 255, 255); font-size: 24px"
      >
        {{ inpuThirdTitle }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "MainContent",
  props: {
    inputTitle: {
      type: String,
      default: "",
    },
    inputSubTitle: {
      type: String,
      default: "",
    },
    inpuThirdTitle: {
      type: String,
      default: "",
    },
  },
  data() {
    return {};
  },
};
</script>
<style></style>
