<template>
  <div class="rule-gen-complete-page">
    <header-menu
      @changePage="ChildChangePage($event)"
      @OpenInstructions="OpenInstructions()"
    />
    <div class="daruma-container">
      <img src="../assets/daruma_blue_load.svg" alt="" />
      <img src="../assets/daruma_red_load.svg" alt="" />
      <img src="../assets/daruma_green_load.svg" alt="" />
    </div>
    <p class="complete-text">COMPLETE !!</p>
    <div class="btn-container">
      <div
        class="rule-make-compleat-btn dl-btn"
        @click.prevent="downloadItem()"
      >
        <span>ファイルをダウンロード</span>
      </div>
      <div
        class="rule-make-compleat-btn attach-rule-btn"
        @click="ChangePage('trim_select_page')"
      >
        <span>ルール適用ページへ</span>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderMenu from "../components/HeaderMenu.vue";

export default {
  name: "RuleGenCompletePage",
  components: {
    HeaderMenu,
  },
  data() {
    return {
      input_code: "",
      output_code: "",
    };
  },
  created() {},
  computed: {},
  methods: {
    downloadItem() {
      this.$emit("downloadItem");
    },
    ChangePage(target) {
      this.$emit("changePage", { page: target });
    },
    ChildChangePage(target) {
      this.$emit("changePage", { page: target.page });
    },
    OpenInstructions() {
      this.$emit("OpenInstructions");
    },
    ChangeHeight() {
      console.log(this.input_area_height);
      let over_line = this.input_code.split(/\r?\n/g).length - 13;
      console.log(over_line);
      if (over_line > 0) {
        this.input_area_height = "height:" + (300 + over_line * 22.95) + "px;";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.rule-gen-complete-page {
  width: 100%;
  height: 100%;
  background-color: #dce7e4;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .daruma-container {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    img {
      margin: 5px 15px;
    }
  }
  .complete-text {
    color: #313131;
    font-size: 20px;

    margin: 10px 0 30px 0;
  }
  .btn-container {
    width: 950px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    .rule-make-compleat-btn {
      font-family: noto-sans-cjk-jp, sans-serif;
      font-weight: 700;
      font-style: normal;
      cursor: pointer;
      border-radius: 999px;
      padding: 10px 30px;
      span {
        color: #ffffff;
        font-size: 14px;
      }
      &:hover {
        background-color: #5297ac;
      }
    }
    .dl-btn {
      background-color: #e55c6e;
      margin-right: 10px;
      &:hover {
        background-color: #ba3636;
      }
    }
    .attach-rule-btn {
      background-color: #5ca1e5;
      margin-left: 10px;
      &:hover {
        background-color: #2d6599;
      }
    }
  }
}
</style>
