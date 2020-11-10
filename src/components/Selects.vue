<template>
  <div style="width:200px;margin:0 auto;">
    <button @click="selectClick" style="margin-bottom:2px">
      {{ placeholder
      }}<img
        src="../assets/arrow.png"
        style="float:right"
        :class="{ buttonarrow: ifShow }"
      />
    </button>
    <div
      v-for="(item, index) in list"
      :key="index"
      v-show="ifShow"
      class="button-item"
      @click="itemaClick(index)"
    >
      <button class="button-item">
        {{ item
        }}<img
          src="../assets/check.png"
          style="float:right"
          v-show="index == list.indexOf(placeholder)"
        />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Selects",
  props: {
    list: Array,
  },
  data() {
    return {
      placeholder: "请选择",
      ifShow: false,
    };
  },
  methods: {
    selectClick() {
      this.ifShow = !this.ifShow;
    },
    itemaClick(index) {
      this.placeholder = this.list[index];
      this.$emit("checkItem", index);
      this.ifShow = false;
    },
  },
};
</script>

<style scoped>
html {
  height: 100%;
}
body {
  height: 100%;
  margin: 0px;
}
button {
  text-align: left;
  padding-left: 20px;
  width: 200px;
  height: 30px;
  border: 1px solid #22222233;
  background-color: #ffffff;
}
button:focus {
  outline: none;
  border: 1.5px solid#1ABC9C;
}
.button-item:focus {
  outline: none;
  background-color: #1abc9c;
}
.button-item {
  margin-top: -1px;
}
.buttonarrow {
  transform: rotate(90deg);
  -ms-transform: rotate(90deg); /* IE 9 */
  -moz-transform: rotate(90deg); /* Firefox */
  -webkit-transform: rotate(90deg); /* Safari 和 Chrome */
  -o-transform: rotate(90deg);
}
</style>
