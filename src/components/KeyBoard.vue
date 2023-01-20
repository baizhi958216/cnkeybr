<template>
  <div class="keylist">
    <div class="col">
      <div class="key" v-for="(key, index) in key1" :key="index">
        {{ key }}
      </div>
    </div>
    <!--  -->
    <div class="col">
      <div class="key" v-for="(key, index) in key2" :key="index">
        {{ key }}
      </div>
    </div>
    <!--  -->
    <div class="col">
      <div class="key" v-for="(key, index) in key3" :key="index">
        {{ key }}
      </div>
    </div>
    <div class="col">
      <div class="key whiteb"></div>
    </div>
  </div>
</template>

<script setup lang="ts">
const key1 = ["Q", "W", "E", "R", "T", "Y", "U", "I", "O", "P"];
const key2 = ["A", "S", "D", "F", "G", "H", "J", "K", "L"];
const key3 = ["Z", "X", "C", "V", "B", "N", "M"];
const clickdown = (val: any) => {
  val.target.classList += " keyenter";
};
</script>

<style scoped>
.keylist {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.col {
  display: flex;
}
.key {
  font-family: sans-serif;
  width: 80px;
  height: 80px;
  background-color: white;
  border-radius: 10px;
  font-size: 30px;
  margin: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  user-select: none;
  cursor: pointer;
}
.keyenter {
  color: aqua;
  background-color: black;
}
.whiteb {
  width: 500px;
}
</style>