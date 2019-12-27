<template>
  <div>
    <div><input type="text" placeholder="请输入搜索内容" v-model="searchContent"></div>
    <table>
      <thead>
        <tr>
          <th v-for="(column, index) in header" @click="handleTitleClick(header, index)">{{column.title}}
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
    <table id="table2">
      <tr><td>first</td><td>second</td><td id="sspecial-td">third</td></tr>
      <tr><td>first</td><td>second</td><td id="special-td">third</td></tr>
    </table>
    <div style="text-align: right;background-color: blue"><p style="width: 200px;background-color: cyan;">弄明白这个地方外边距合并的问题</p></div>
    <ul>
      <li>first</li>
      <li>second</li>
      <li>third</li>
      <li>four</li>
    </ul>
    <!-- <div style="float:left">This is a div element</div>
    <li style="float: left;">special</li> -->
    <li style="background-color: lightblue">This is li element.</li>
    <span>This is a span element.</span>
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
        handleTitleClick(headers, index){
          console.log("this column info is: " + headers[index].isAsc);
          if (headers[index].isAsc === false && headers[index].isDesc === false){
            /* let newInfo = headers[index];
            newInfo.isAsc = true;
            this.$set(headers[index], index, newInfo); */
            this.$set(this.header[index], "isAsc", true);

            console.log("asc is true");
          }else if (headers[index].isAsc === true){
            let newInfo = headers[index];
            newInfo.isAsc = false;
            newInfo.isDesc = true;
            this.$set(headers, index, newInfo);
            console.log("desc is true");
          }else {
            let newInfo = headers[index];
            newInfo.isAsc = true;
            newInfo.isDesc = false;
            this.$set(headers, index, newInfo);
            console.log("asc is true");
          }
          this.$forceUpdate();
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
  ul{
    background-color: lightyellow;
  }
  ul  li{
    background-color: lightblue;
  }
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
  table#table2{
    width: 900px;
    border-collapse: collapse;
  }
  table#table2 td {
    border: 1px solid black;
  }
  #special-td{
    width: 400px;
  }

</style>
