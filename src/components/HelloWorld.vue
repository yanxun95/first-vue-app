<script>
import Echarts from "./Echarts.vue";
import Leaflet from "./Leaflet.vue";

export default {
  props: {
    msg: String,
  },
  data() {
    return {
      greeting: "Testing!",
      count: 0,
      userInput: "",
      testId: "This is the test id.",
    };
  },
  methods: {
    myFunctionClick: function () {
      this.$refs.myId.innerText = "Hello Bro";
    },
    passDataFunction() {
      console.log("this is test Emit Function");
    },
  },
  components: { Echarts, Leaflet },
};
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>
  <div>{{ greeting }}</div>
  <Leaflet @getData="passDataFunction()" />

  <input v-model="userInput" />
  <div id="displayUserInput">
    <p>The user input will be display in here: {{ userInput }}</p>
  </div>
  <div id="testId">{{ testId }}</div>
  <Echarts />
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
