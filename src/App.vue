<template>
  <div id="app">
    <first-component :data="head" :columns="rowInfos"></first-component>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import FirstComponent from './components/Firstcomponent'

export default {
  name: 'App',
  data(){
    return {
      head: ["姓名", "年龄"],
      rowInfos: [
        {age: 23, name: "Tom", region: "shandong"},
        {age: 24, name: "Tina", region: "hebei"},
        {age: 25, name: "Hobby", region: "guangdong"},
        {age: 16, name: "Anna", region: "shanghai"}
      ] }
  },
  components: {
    HelloWorld,
    FirstComponent
  }
}
</script>

<style>

</style>
