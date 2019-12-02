<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-router" target="_blank" rel="noopener">router</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
    <h3>axios测试，热更新是什么功能</h3>
    <ul>
        <button @click="getAreaList">获取数据</button>
        <button @click="getAreaById">获取第一行数据</button>
        <button @click="addArea">添加一行数据</button>
        <button @click="modifyArea">更改数据</button>
        <button @click="deleteArea">删除数据</button>
    </ul>
  </div>

</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods:{
        getAreaList(){
            axios
                .get(
                    /*'http://localhost:8888/superadmin/listarea'*/
                    '/superadmin/listarea'
                )
                .then(function (response) {
                    console.log("请求正常");
                    console.log(response);
                })
                .catch(function (error) {
                    console.log("请求错误");
                    console.log(error);
                });
        },
        getAreaById(){
            axios
                .get(
                    /*'http://localhost:8888/superadmin/getareabyid',{*/
                    '/superadmin/getareabyid',{
                        params: {
                            areaId: 1
                        }
                    }
                )
                .then(function (response) {
                    console.log("请求正常");
                    console.log(response);
                })
                .catch(function (error) {
                    console.log("请求错误");
                    console.log(error);
                });
        },
        addArea(){
            axios.post(
                /*'http://localhost:8888/superadmin/addarea', {*/
                '/superadmin/addarea', {
                    areaName: 'ABC',
                    priority: '12'
                }
                )
                .then(function (response){
                    console.log("addArea正常");
                    console.log(response);
                })
                .catch(function (error){
                    console.log("addArea异常");
                    console.log(error);
                });
        },
        modifyArea(){
            axios.post(
                /*'http://localhost:8888/superadmin/modifyarea', {*/
                '/superadmin/modifyarea', {
                    areaId:10,
                    areaName: 'haha',
                    priority: '22'
                }
            ).then(function (response){
                console.log("modifyArea正常");
                console.log(response);
            }).catch(function (error){
                console.log("modifyArea异常");
                console.log(error);
            });
        },
        deleteArea(){
            /*axios.get('http://localhost:8888/superadmin/deletearea',{*/
            axios.get('/superadmin/deletearea',{
                        params: {
                            areaId: 10
                        }
                    }
            ).then(function (response){
                console.log("modifyArea正常");
                console.log(response);
            }).catch(function (error){
                console.log("modifyArea异常");
                console.log(error);
            });
        }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
