<template>
  <div>
    <h2>This is First Component</h2>
    <div><input type="text" placeholder="请输入搜索内容" v-model="searchContent"></div>
    <table>
      <thead>
        <tr>
          <th v-for="column in data">{{column}}</th>
        </tr>
      </thead>
      <tbody>
          <tr v-for="rowInfo in filterColumns">
            <td v-for="key in rowInfo"> {{key}}</td>
          </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
    export default {
        name: "FirstComponent",
      props:{
          "data": Array,
        "columns": Array,
        filterKey: String
      },
      data(){
          return {
            searchContent: ""
          } }, methods: {
          handleSearch(event){
            window.alert(event.target.value);
          }
      },
      computed: {
          filterColumns(){
              let filterDatas = Array();
              console.log(this.columns);
              for(let columnData of this.columns){
                let isIncludeSearch = false;
                for(let elementKey in  columnData){
                  let element = columnData[elementKey];
                  if (typeof element === "string" && element.indexOf(this.searchContent) !== -1){
                    isIncludeSearch = true;
                    break;
                  }
                }
                if (isIncludeSearch){
                  filterDatas.push(columnData);
                }
              }
              return filterDatas;
          }
      }

    }
</script>

<style scoped>
  table{
    border-collapse: separate; border: 2px solid lightgreen;
  }
  th{
    background-color: lightgreen;
    width: 200px;
    height: 1.5em;
    color: white;
  }
  td{
    background-color: lightgray;
    width: 200px;
    height: 1.5em;
  }
</style>
