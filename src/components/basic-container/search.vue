<template>
  <div>
    <el-input
            :placeholder="placeholder"
            v-model.trim="value"
            class="searchClass"
            @keyup.enter.native="searchEnterFun"
            maxlength="20"
    >
      <el-button slot="append" icon="el-icon-search" @click.native="searchData" circle></el-button>
    </el-input>
  </div>
</template>

<script>
  import * as publicRule from "@/rules/rules.js";

  export default {
    props: ["placeholder"],
    name: "search",
    data() {
      return {
        value: ""
      };
    },
    methods: {
      searchData() {
        if (publicRule.searchRule(this.value)) {
          this.validata();
        } else {
          this.$message.warning("包含特殊字符，不支持查询")
        }

      },
      getContent() {
        return this.value;
      },
      searchEnterFun(e) {
        let keyCode = window.event ? e.keyCode : e.which;
        if (keyCode === 13) {
          this.validata();
        }
      },
      validata() {
        publicRule.passHtmlAndSql(null, this.value, err => {
          if (err) {
            this.$message.error(err.message);
          } else {
            this.$emit("searchData");
          }
        });
      }
    }
  };
</script>

<style lang="scss">
  .searchClass {
    border: 1px solid #e3e3e3;
    /*background: #f4f4f4;*/
    width: 260px;
    box-sizing: border-box;
    border-radius: 100px;
  }

  .searchClass .el-input-group__append {
    border: none;
    padding: 0px 20px 0px 0px;
    background-color: transparent;
  }

  .searchClass .el-input__inner {
    height: 32px;
    line-height: 36px;
    border: none;
    background-color: transparent;
  }
</style>
