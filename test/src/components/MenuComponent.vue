<template>
  <div class="leftBox">
    <h2 class="h2title">开发指南</h2>
    <ul class="uls">
      <li class="lis" @click="fun1(menuinfo[idx].src,idx)"  v-for="(m,idx) in menuinfo"><a href="#">{{m.title}}</a></li>
    </ul>
  </div>
</template>
<script>
    export default {
        name: "MenuComponent",
      props:["menuinfo","clicks"],
      data(){
        return {
          myTime:null
        }
      },
      methods:{
          fun1(p,idx){
            this.myTime=null
            localStorage.clear()
            showiframe.window.fun(p)
            this.clicks(idx)
          },
          mobileToPc(){

            this.myTime = setInterval(()=>{
              if(window.localStorage.name){
                this.clicks(window.localStorage.name)}
            },200)
        }
      },
      mounted(){

      },
      created(){
        this.mobileToPc()
      },
      destroyed(){
          this.myTime=null
          localStorage.clear()
      }
    }
</script>

<style scoped>
  .leftBox{
    width: 20%;
    float: left;
    height: 100%;
    overflow: auto;
  }
  .leftBox::-webkit-scrollbar{
    width: 8px;
    background: #ddd;
    height: 8px;
    border-radius:5px;
  }
  .leftBox::-webkit-scrollbar-thumb{
    background: #aaaaaa;
    border-radius: 5px;
  }
  .h2title{
    margin:100px 10px 10px;
    font-size: 18px;
    text-align: center;
  }
  .uls{
    border-right: 1px solid #eee;
    padding-bottom: 100px;
  }
  .lis{
    margin: 10px;
    text-align: center;
  }
  .lis a{
    color: rgb(68,68,68);
  }
  .lis a:hover{
    color: #0086b3;
  }
</style>
