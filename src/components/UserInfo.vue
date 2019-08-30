<template>
    <div class="UserInfo">
        <div class="loading" v-if="isLoading">
            <img src="../assets/loading.gif" >
        </div>
        <div class="userInfomation" v-else>
            <section>
                <img :src="userinfo.avatar_url" >
                <span>{{userinfo.loginname}}</span>
                <p>
                    {{userinfo.score}}积分
                </p>
                <p>
                注册时间：{{userinfo.create_at | formatDate}}
                </p>
            </section>
           <div class="replies">
               <p>回复的主题</p>
               <ul>
                   <li v-for="item in userinfo.recent_replies">
                       <router-link :to="{
                           name:'post_content',
                           params:{
                               id:item.id
                           }
                       }">
                        {{item.title}}
                       </router-link>
                   </li>
               </ul>
               <div class="topic">
                   <p>创建的主题</p>
                   <ul>
                       <li v-for="item in userinfo.recent_topics">
                           <router-link :to="{
                               name:'post_content',
                               params:{
                                   id:item.id
                               }
                           }">
                           {{item.title}}
                           </router-link>
                       </li>
                   </ul>
               </div>
           </div>
        </div>
    </div>
</template>

<script>
 export default {
        name: "UserInfo",
      data(){
          return {
            isLoading:false,
            userinfo:{}
          }
      },
      methods:{
          getData(){
              this.$http.get(`https://cnodejs.org/api/v1/user/${this.$route.params.name}`)
                .then(res=>{
                  this.isLoading = false; //加载成功，去除动画
                  this.userinfo = res.data.data;
                })
                .catch(function (err) {
                  //处理返回失败后的问题
                  console.log(err)
                })
          }
      },
      beforeMount(){
          this.isLoading = true;
          this.getData();
      }
 }
</script>
<style  scoped>
img{
    width: 40px;
    height: 40px;
    padding-top: 10px;
}
 .userInfomation {
    background: white;
    width: 75%;
    margin: 10px auto;
  }
 .userInfomation section {
    padding: 12px;
  }
  .userInfomation .replies,
  .userInfomation .topics {
    font-size: 0.9rem;
    border-top: 10px #DDDDDD solid;
  }

  .userInfomation > div ul li a {
    color: #094E99;
    text-decoration: none;
  }
  .userInfomation > div  p {
    padding: 12px 0 12px 12px;
    background-color: rgba(212, 205, 205, 0.17);
    font-size: 1rem;
    margin: 0;
  }
</style>