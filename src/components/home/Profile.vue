<template>
  <div>
    <!-- 头像 -->
    <el-row>
      <el-col :span="24">
        <img class="account-picture" src="../../assets/img/picture.jpg" />
      </el-col>
    </el-row>
    <!-- 名称 -->
    <el-row style="margin-top: 3px;">
      <el-col :span="24">
        <span style="color: #000000;font-weight: 900;font-family: 'microsoft yahei';">{{this.accountName}}</span>
      </el-col>
    </el-row>
    <el-row style="margin-top: 15px;">
      <el-col :span="24">
        <el-button-group>
          <el-button size="mini" @click="edit">编辑</el-button>
          <el-button size="mini" @click="logout">注销</el-button>
        </el-button-group>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: 'Profile',
    props: {
      accountName: String
    },
    methods: {
      edit() {

      },
      logout() {
        this.$alert('确定退出吗？', '注销', {
          confirmButtonText: '确定',
          callback: action => {
            this.axios.get(this.Common.httpUrl+'/logout')
            .then((response) =>{
              // 判断是否登录成功并存在Session
              if(response.data.data){
                this.$router.push({
                  name: 'Login'});
              }
            })
          }
        });
      }
    }
  }
</script>

<style>
  .account-picture {
    width: 80px;
    height: 80px;
    margin-top: 30px;
    border-radius: 50%;
    -webkit-border-radius: 50%;
    -moz-border-radius: 50%;
    border: 2px solid #409EFF;
  }
</style>
