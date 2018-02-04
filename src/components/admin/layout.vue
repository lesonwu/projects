<template>
    <div class="tmpl">
        <!-- layout的职责就是编写 左边菜单 顶部导航栏-->
        <el-row>
        <!-- 左边菜单 -->
          <el-col :span="leftcol">
              <img src="../../../statics/imgs/logo.png" width="100%">
              <div class="layout menu">
                  <el-menu default-active="1-1" class="el-menu-vertical-demo" :collapse="isCollapse">
                      <!--购物商城-->
                      <el-submenu index="1">
                          <template slot="title">
                              <i class="el-icon-message"></i>
                              <span>购物商城</span>
                          </template>
                          <el-menu-item-group>
                              <router-link to="/admin/goodslist">
                                <el-menu-item index="1-1">内容管理</el-menu-item>
                              </router-link>
                              <el-menu-item index="1-2">类别管理</el-menu-item>
                              <el-menu-item index="1-3">评论管理</el-menu-item>
                          </el-menu-item-group>
                      </el-submenu>
                      <!--订单管理-->
                      <el-submenu index="2">
                          <template slot="title">
                              <i class="el-icon-message"></i>
                              <span>订单管理</span>
                          </template>
                          <el-menu-item-group>
                              <el-menu-item index="2-1">订单列表</el-menu-item>
                          </el-menu-item-group>
                      </el-submenu>
                  </el-menu>
              </div>
          </el-col>
          <!-- 右边区域 -->
          <el-col :span="rightcol">
            <!-- 右边区域：顶部栏 -->
            <el-row>
                <el-col :span="24">
                    <div class="topbg">
                        <el-row>
                            <!--图标点击收缩导航-->
                            <el-col :span="1">
                                <i  @click="showhide" class="el-icon-menu layout area"></i>
                            </el-col>
                            <el-col :span="23">
                                <span>欢迎xx登录</span>
                                <el-dropdown split-button type="primary">
                                    更多
                                    <el-dropdown-menu slot="dropdown">
                                        <el-dropdown-item>修改密码</el-dropdown-item>
                                        <el-dropdown-item>注销登录</el-dropdown-item>
                                    </el-dropdown-menu>
                                </el-dropdown>
                            </el-col>
                        </el-row>
                    </div>
                </el-col>
            </el-row>
            <!-- 右边区域：内容 -->
            <el-row>
                <el-col :span="24">
                    <router-view><div>内容</div></router-view>
                </el-col>
            </el-row>
          </el-col>
        </el-row>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                //默认菜单栏展开 isCollapse:fasle
                isCollapse:false,
                leftcol:4,
                rightcol:20
            }
        },
        methods: {
            showhide(){
                //console.log(1);
                this.isCollapse = !this.isCollapse;
                if(this.isCollapse){
                    this.leftcol=1,
                    this.rightcol=23
                }else{
                    this.leftcol=4,
                    this.rightcol=20
                }
            }
        }
    }
</script>
<style scoped>
</style>