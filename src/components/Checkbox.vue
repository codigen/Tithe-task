<template>
  <div class="container">
    <div class="card" v-for="(username, index) in codepally" :key="index">
      <input
        class="checkbox"
        :id="username[0]"
        @click="checkbox($event)"
        type="checkbox"
        :value="username[0]"
        v-model="selected"
      />
      <label class="username" :for="username[0]">{{username[1]}}</label>
    </div>
    <pre class="flex">{{selected}}</pre>
  </div>
</template>
<script>
import { codepally_data } from "../lib/app.js";
export default {
  name: "Hello",
  data: () => ({
    selected: [],
    codepally: []
  }),
  mounted: function() {
    let c = Object.keys(codepally_data).map(key => [key, codepally_data[key]]);
    this.codepally = c;
  },
  methods: {
    checkbox(event) {
      if (event.target.tagName == "LABEL") {
        event.target.parentNode.classList.toggle("blue");
        console.log(event);
      }
      if (event.target.type == "checkbox") {
        event.target.parentNode.classList.toggle("blue");
      }
      event.target.classList.toggle("blue");
    }
  }
};
</script>
<style>
.container {
  width: 300px;
  display: flex;
  flex-direction: column;
}
.card {
  margin-bottom: 5px;
  display: flex;
  box-shadow: 0px 1px 4px #eee;
  padding: 0px 9px;
  width: 300px;
  background: white;
  cursor: pointer;
  flex-direction: unset !important;
}
.username {
  padding: 0px 10px; 
  margin: 10px;
}
.checkbox {
  padding: 0px 10px;
  margin: 10px;
  outline: none;
}
.blue {
  background: dodgerblue;
  color: white;
}
.flex {
  display: inline-block;
  overflow: hidden;
  
}

input[type="checkbox"].checkbox {
  font-size: 20px;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  width: 2.5em;
  height: .8em;
  background: #ddd;
  border-radius: 3em;
  position: relative;
  cursor: pointer;
  outline: none;
  -webkit-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
}

input[type="checkbox"].checkbox:checked {
  background: #0ebeff;
}

input[type="checkbox"].checkbox:after {
  position: absolute;
  content: "";
  width: 1.5em;
  height: .8em;
  border-radius: 50%;
  background: #fff;
  -webkit-box-shadow: 0 0 0.25em rgba(0, 0, 0, 0.3);
  box-shadow: 0 0 0.25em rgba(0, 0, 0, 0.3);
  -webkit-transform: scale(0.7);
  transform: scale(0.7);
  left: 0;
  -webkit-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
}

input[type="checkbox"].checkbox:checked:after {
  left: calc(100% - 1.5em);
}
</style>