<template>
  <div>
    <div><input type="text" placeholder="请输入搜索内容" v-model="searchContent"></div>
    <table>
      <thead>
        <tr>
          <th v-for="column in header" @click="handleTitleClick(column)">{{column.title}}
            <span class="arrow" v-bind:class="{asc: column.isAsc, desc: column.isDesc}"></span>
          </th>
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
        "columns": Array
      },
      data(){
          return {
            searchContent: ""
          }
      },
      methods: {
        handleSearch(event){
         window.alert(event.target.value);
        },
        /* 可能是传入的参数不正确 */
        handleTitleClick(columnInfo){
          console.log("this column info is: " + columnInfo.isAsc);
          if (columnInfo.isAsc === false && columnInfo.isDesc === false){
            this.$set(columnInfo, "isAsc", true);
            console.log("asc is true");
          }else if (columnInfo.isAsc === true){
            this.$set(columnInfo, "isAsc", false);
            this.$set(columnInfo, "isDesc", true);
            console.log("desc is true");
          }else {
            this.$set(columnInfo, "isDesc", false);
            this.$set(columnInfo, "isAsc", true);
            console.log("asc is true");
          }
        }
      },
      computed: {
          filterColumns(){
              let filterDatas = Array();
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
          },
          header(){
            let headers = Array();
            for(let title of this.data){
               headers.push({
                  title: title,
                  isAsc: false,
                 isDesc: false
               });
            }
            return headers;
          }
      }

    }
</script>

<style scoped>
  table{
    border-collapse: separate; border: 2px solid #42b983;
  }
  th{
    background-color: #42b983;
    width: 200px;
    height: 1.5em;
    color: white;
  }
  td{
    background-color: lightgray;
    width: 200px;
    height: 1.5em;
  }
  .arrow{
    display: inline-block;
    vertical-align: middle;
    width: 0;
    height: 0;
    margin-left: 5px;
    opacity: 0.66;
  }
  .arrow.asc{
    border-left: 4px solid transparent;
    border-right: 4px solid transparent;
    border-bottom: 4px solid #fff;
  }
  .arrow.desc{
    border-left: 4px solid transparent;
    border-right: 4px solid transparent;
    border-top: 4px solid #fff;
  }


</style>
