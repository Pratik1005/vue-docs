<script setup>
import {ref, reactive} from "vue";

const message = ref("Dynamic Text");
const counter = reactive({count: 0});
const titleClass = ref("title");

const text = ref("");

const tab = reactive({
  tab1: true,
  tab2: false,
});
let id = 1;
const list = ref([
  {id: id++, text: "Learn HTML"},
  {id: id++, text: "Learn JavaScript"},
  {id: id++, text: "Learn Vue"},
]);

function showError() {
  titleClass.value = "error";
}

function showSuccess() {
  titleClass.value = "success";
}
console.log("tab", tab);
function handleTab(tabNum) {
  if (tabNum === "tab1") {
    tab.tab1 = true;
    tab.tab2 = false;
  } else {
    console.log("tab2 clicked");
    tab.tab1 = false;
    tab.tab2 = true;
  }
  console.log("tab up", tab);
}
</script>

<template>
  <h1 :class="titleClass">{{ message }}</h1>
  <p>Count is {{ counter.count }}</p>
  <div>
    <button @click="showError">Error</button>
    <button @click="showSuccess">Success</button>
  </div>
  <div>
    <input v-model="text" placeholder="type" />
    <p>{{ text }}</p>
  </div>

  <div>
    <button @click="handleTab('tab1')">Tab 1</button>
    <button @click="handleTab('tab2')">Tab 2</button>
    <h2 v-if="tab.tab1">Tab1</h2>
    <h2 v-else>Tab1</h2>
  </div>

  <ul>
    <li v-for="item in list" :key="item.id">{{ item.text }}</li>
  </ul>
</template>

<style scoped>
.error {
  color: red;
}

.success {
  color: green;
}
</style>
