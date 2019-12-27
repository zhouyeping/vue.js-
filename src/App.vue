<template>
  <div id="app">
    <complaint></complaint>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import FirstComponent from './components/Firstcomponent'
import SecondComponent from "./components/SecondComponent";
import Complaint from './components/Complaint'

export default {
  name: 'App',
  data(){
    return {
      head: ["姓名", "年龄", "地区"],
      rowInfos: [
        {age: 23, name: "Tom", region: "shandong"},
        {age: 24, name: "Tina", region: "hebei"},
        {age: 25, name: "Hobby", region: "guangdong"},
        {age: 16, name: "Anna", region: "shanghai"}
      ] }
  },
  components: {
    HelloWorld,
    FirstComponent,
    SecondComponent,
    Complaint
  }
}
</script>

<style>
  html, body{
    margin: 0;
    padding: 0;
  }
</style>
