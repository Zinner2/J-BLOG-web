<template>
  <el-container>
    <el-header style="z-index: 10">
      <el-row v-if="blogInfo.blogId !== 33">
        <el-col :span="16">
          <div>
            <el-page-header @back="goBack"
                            :content="blogInfo.blogTitle">
            </el-page-header>

          </div>

        </el-col>
        <el-col :span="4">
          <el-divider direction="vertical"></el-divider>
          <el-link @click="getBlogByTag(blogInfo.blogCategoryName)">{{
            blogInfo.blogCategoryName
          }}</el-link>


        </el-col>
        <el-col :span="2" v-if="blogStatus == '' || blogStatus == null">
          <i class="el-icon-view">{{ blogInfo.blogViews }}</i> 浏览量
        </el-col>
      </el-row>
    </el-header>
    <el-main>
      <el-container>
        <el-aside>
          <el-tag
              v-for="item in blogInfo.tagNames"
              effect="dark">
            {{ item }}
          </el-tag>
        </el-aside>
        <el-main style="width: 1000px; margin-left: 180px">
          <el-row>
            <mavon-editor
              v-model="blogInfo.blogContent"
              :subfield="false"
              :editable="false"
              :scrollStyle="false"
              defaultOpen="preview"
              :toolbarsFlag="false"
              fontSize="16px"
            ></mavon-editor>
          </el-row>
        </el-main>

        <el-footer style="width: 1000px; margin-left: 180px">
          <el-row>
            <div class="blog">
              <p>
                本站文章除注明转载/出处外，皆为作者原创，欢迎转载，但未经作者同意必须保留此段声明，且在文章页面明显位置给出原文连接，否则保留追究法律责任的权利。
              </p>
            </div>
          </el-row>
          <el-row v-if="blogInfo.blogId !== 33">

            <el-button round style="margin-left: 350px;margin-bottom: 20px" type="info" @click="likeBlog()" v-if="blogLikeStatusDto.likeStatus === 0">
              <svg t="1649343941014" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2695" width="16" height="16"><path d="M939.358251 423.424662c-23.01825-37.252439-62.924121-60.779272-107.019409-63.209624-2.755764-0.38681-5.510504-0.579191-8.347109-0.579191l-152.202471-0.121773c6.649444-28.975938 10.015098-58.653865 10.015098-88.657202 0-28.223808-3.213181-57.139372-9.556657-85.952604-0.447185-2.043542-1.098008-4.006244-1.932002-5.866614-15.820314-57.302077-67.37755-96.841605-127.282918-96.841605-72.827679 0-132.081201 59.254545-132.081201 132.081201 0 3.334955 0.132006 6.66991 0.406253 10.015098-2.196015 57.211003-32.108279 109.947088-80.269162 141.363611-14.447037 9.42465-18.524912 28.773324-9.099239 43.220361 9.414417 14.437827 28.752858 18.535145 43.220361 9.099239 65.811892-42.925648 106.429984-115.325585 108.656699-193.684234 0.030699-1.332345-0.010233-2.663666-0.14224-3.996011-0.203638-2.012843-0.304945-4.016477-0.304945-6.019087 0-38.381146 31.233352-69.614497 69.614497-69.614497 32.57593 0 60.474326 22.204721 67.824735 53.997821 0.356111 1.534959 0.823761 3.019777 1.402953 4.453429 4.696975 22.814612 7.076162 45.579081 7.076162 67.743894 0 37.485753-6.222725 74.352405-18.494213 109.592001-3.324722 9.546424-1.819438 20.111037 4.02671 28.345582 5.856381 8.245801 15.332197 13.146415 25.448602 13.156648l193.226816 0.101307c1.423419 0.264013 2.857071 0.426719 4.300956 0.477884 24.116257 0.9967 45.935192 13.614066 58.603723 34.090423 7.838525 12.31242 11.438517 26.800389 10.431583 41.939181-0.080841 0.945535-0.121773 1.911536-0.11154 2.877537 0 0.854461 0.040932 1.697665 0.11154 2.53166 0.010233 0.335644-0.030699 0.661056-0.11154 0.976234-0.101307 0.376577-0.193405 0.772596-0.284479 1.159406l-74.972529 330.391802c-0.914836 1.281179-1.738597 2.6432-2.449795 4.046153-5.937223 11.762905-14.660908 21.48329-25.346271 28.172643-10.746762 6.812149-23.059182 10.614755-35.757388 11.06194-0.854461-0.061398-513.766226-0.224104-513.766226-0.224104-0.467651-0.020466-0.935302-0.030699-1.402953-0.030699 0 0-111.01542 0.172939-112.718201 0.457418-1.932002 0-3.446495-1.50426-3.446495-3.415796l0.299829-416.334173c0-1.901303 1.545192-3.446495 3.01466-3.456728l1.245364 0.121773c1.174756 0.132006 2.653433 0.284479 3.52836 0.193405l83.82822-0.222057 0 339.367221c0 17.253966 13.979386 31.233352 31.233352 31.233352s31.233352-13.979386 31.233352-31.233352L281.009092 435.350273c0-1.778506 0-8.631588 0-10.411117 0-17.253966-13.979386-30.928407-31.233352-30.928407-1.50426 0-117.547183 0.304945-119.402437 0.304945-36.34272 0-65.913199 29.566386-65.913199 65.893756l-0.299829 416.334173c0 36.337603 29.571503 65.902966 65.913199 65.902966 2.541893 0 111.406323-0.457418 111.406323-0.457418 0.457418 0.020466 0.925069 0.030699 1.382487 0.030699 0 0 511.458671 0.274246 512.505513 0.274246 25.469068 0 50.296523-7.197936 71.647807-20.73116 19.612687-12.281721 35.777855-29.881564 46.839795-50.967812 3.660366-5.622044 6.435573-11.875468 8.256034-18.615986 0.11154-0.416486 0.213871-0.823761 0.304945-1.240247l74.881454-330.340637c1.596358-6.212492 2.257413-12.586666 2.00261-18.992563C960.892707 473.366098 953.948551 446.331371 939.358251 423.424662z" p-id="2696"></path><path d="M450.027553 518.650467c-17.253966 0-31.233352 13.979386-31.233352 31.233352l0 30.470989c0 17.253966 13.979386 31.233352 31.233352 31.233352 17.253966 0 31.233352-13.979386 31.233352-31.233352l0-30.470989C481.260905 532.629853 467.281519 518.650467 450.027553 518.650467z" p-id="2697"></path><path d="M693.805696 518.650467c-17.253966 0-31.233352 13.979386-31.233352 31.233352l0 30.470989c0 17.253966 13.979386 31.233352 31.233352 31.233352 17.253966 0 31.233352-13.979386 31.233352-31.233352l0-30.470989C725.039048 532.629853 711.058638 518.650467 693.805696 518.650467z" p-id="2698"></path><path d="M648.940882 660.09492c-14.304797-9.393951-33.592073-5.398964-43.159986 8.763594-0.132006 0.193405-13.614066 19.754926-34.171264 19.754926-19.98824 0-32.423457-18.09717-33.266661-19.368116-9.17087-14.427594-28.254507-18.809391-42.834574-9.770528-14.650675 9.109472-19.155269 28.366048-10.055007 43.016723 11.214413 18.047028 41.96988 48.588625 86.156242 48.588625 43.962258 0 75.104535-30.318516 86.572728-48.222281C667.404396 688.461991 663.216004 669.500127 648.940882 660.09492z" p-id="2699"></path></svg>
              {{blogLikeStatusDto.blogLikes}}
            </el-button>
            <el-button round style="margin-left: 350px;margin-bottom: 20px" type="danger" @click="likeBlog()" v-else>
              <svg t="1649343941014" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2695" width="16" height="16"><path d="M939.358251 423.424662c-23.01825-37.252439-62.924121-60.779272-107.019409-63.209624-2.755764-0.38681-5.510504-0.579191-8.347109-0.579191l-152.202471-0.121773c6.649444-28.975938 10.015098-58.653865 10.015098-88.657202 0-28.223808-3.213181-57.139372-9.556657-85.952604-0.447185-2.043542-1.098008-4.006244-1.932002-5.866614-15.820314-57.302077-67.37755-96.841605-127.282918-96.841605-72.827679 0-132.081201 59.254545-132.081201 132.081201 0 3.334955 0.132006 6.66991 0.406253 10.015098-2.196015 57.211003-32.108279 109.947088-80.269162 141.363611-14.447037 9.42465-18.524912 28.773324-9.099239 43.220361 9.414417 14.437827 28.752858 18.535145 43.220361 9.099239 65.811892-42.925648 106.429984-115.325585 108.656699-193.684234 0.030699-1.332345-0.010233-2.663666-0.14224-3.996011-0.203638-2.012843-0.304945-4.016477-0.304945-6.019087 0-38.381146 31.233352-69.614497 69.614497-69.614497 32.57593 0 60.474326 22.204721 67.824735 53.997821 0.356111 1.534959 0.823761 3.019777 1.402953 4.453429 4.696975 22.814612 7.076162 45.579081 7.076162 67.743894 0 37.485753-6.222725 74.352405-18.494213 109.592001-3.324722 9.546424-1.819438 20.111037 4.02671 28.345582 5.856381 8.245801 15.332197 13.146415 25.448602 13.156648l193.226816 0.101307c1.423419 0.264013 2.857071 0.426719 4.300956 0.477884 24.116257 0.9967 45.935192 13.614066 58.603723 34.090423 7.838525 12.31242 11.438517 26.800389 10.431583 41.939181-0.080841 0.945535-0.121773 1.911536-0.11154 2.877537 0 0.854461 0.040932 1.697665 0.11154 2.53166 0.010233 0.335644-0.030699 0.661056-0.11154 0.976234-0.101307 0.376577-0.193405 0.772596-0.284479 1.159406l-74.972529 330.391802c-0.914836 1.281179-1.738597 2.6432-2.449795 4.046153-5.937223 11.762905-14.660908 21.48329-25.346271 28.172643-10.746762 6.812149-23.059182 10.614755-35.757388 11.06194-0.854461-0.061398-513.766226-0.224104-513.766226-0.224104-0.467651-0.020466-0.935302-0.030699-1.402953-0.030699 0 0-111.01542 0.172939-112.718201 0.457418-1.932002 0-3.446495-1.50426-3.446495-3.415796l0.299829-416.334173c0-1.901303 1.545192-3.446495 3.01466-3.456728l1.245364 0.121773c1.174756 0.132006 2.653433 0.284479 3.52836 0.193405l83.82822-0.222057 0 339.367221c0 17.253966 13.979386 31.233352 31.233352 31.233352s31.233352-13.979386 31.233352-31.233352L281.009092 435.350273c0-1.778506 0-8.631588 0-10.411117 0-17.253966-13.979386-30.928407-31.233352-30.928407-1.50426 0-117.547183 0.304945-119.402437 0.304945-36.34272 0-65.913199 29.566386-65.913199 65.893756l-0.299829 416.334173c0 36.337603 29.571503 65.902966 65.913199 65.902966 2.541893 0 111.406323-0.457418 111.406323-0.457418 0.457418 0.020466 0.925069 0.030699 1.382487 0.030699 0 0 511.458671 0.274246 512.505513 0.274246 25.469068 0 50.296523-7.197936 71.647807-20.73116 19.612687-12.281721 35.777855-29.881564 46.839795-50.967812 3.660366-5.622044 6.435573-11.875468 8.256034-18.615986 0.11154-0.416486 0.213871-0.823761 0.304945-1.240247l74.881454-330.340637c1.596358-6.212492 2.257413-12.586666 2.00261-18.992563C960.892707 473.366098 953.948551 446.331371 939.358251 423.424662z" p-id="2696"></path><path d="M450.027553 518.650467c-17.253966 0-31.233352 13.979386-31.233352 31.233352l0 30.470989c0 17.253966 13.979386 31.233352 31.233352 31.233352 17.253966 0 31.233352-13.979386 31.233352-31.233352l0-30.470989C481.260905 532.629853 467.281519 518.650467 450.027553 518.650467z" p-id="2697"></path><path d="M693.805696 518.650467c-17.253966 0-31.233352 13.979386-31.233352 31.233352l0 30.470989c0 17.253966 13.979386 31.233352 31.233352 31.233352 17.253966 0 31.233352-13.979386 31.233352-31.233352l0-30.470989C725.039048 532.629853 711.058638 518.650467 693.805696 518.650467z" p-id="2698"></path><path d="M648.940882 660.09492c-14.304797-9.393951-33.592073-5.398964-43.159986 8.763594-0.132006 0.193405-13.614066 19.754926-34.171264 19.754926-19.98824 0-32.423457-18.09717-33.266661-19.368116-9.17087-14.427594-28.254507-18.809391-42.834574-9.770528-14.650675 9.109472-19.155269 28.366048-10.055007 43.016723 11.214413 18.047028 41.96988 48.588625 86.156242 48.588625 43.962258 0 75.104535-30.318516 86.572728-48.222281C667.404396 688.461991 663.216004 669.500127 648.940882 660.09492z" p-id="2699"></path></svg>
             {{blogLikeStatusDto.blogLikes}}
            </el-button>

            <el-button round style="margin-left: 50px;margin-bottom: 20px" type="danger">
              <svg t="1649416743874" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2210" width="16" height="16"><path d="M512 96c229.76 0 416 186.24 416 416S741.76 928 512 928 96 741.76 96 512 282.24 96 512 96z m0 64C317.589333 160 160 317.589333 160 512S317.589333 864 512 864 864 706.410667 864 512 706.410667 160 512 160z m32 97.216l0.021333 75.477333c73.706667 9.152 126.101333 48.853333 128.64 105.6l0.106667 4.373334h-64c0-24.661333-36.266667-48-98.133333-48-62.912 0-98.133333 19.712-98.133334 48 0 25.386667 30.741333 46.592 91.946667 47.914666l6.186667 0.085334c96.469333 0 162.133333 43.541333 162.133333 112 0 64.512-52.693333 101.994667-128.746667 110.250666l-0.021333 76.544h-64V712.96c-75.114667-8.533333-128.810667-48.533333-131.392-105.962667l-0.085333-4.373333h64c0 24.661333 36.309333 48.021333 98.133333 48.021333 62.890667 0 98.133333-19.733333 98.133333-48 0-25.386667-30.72-46.592-91.925333-47.936l-12.458667-0.128c-93.056-1.856-155.882667-44.992-155.882666-111.936 0-65.301333 53.973333-102.890667 131.498666-110.549333l-0.021333-74.901333h64z" fill="#1677FF" p-id="2211"></path></svg>   打赏
            </el-button>
          </el-row>
          <el-row v-if="blogInfo.blogId !== 33">
            <el-col :span="1">
              <div>
                <el-avatar :src="imgUrl"></el-avatar>
              </div>
            </el-col>
            <el-col :span="23">
              <el-input
                type="textarea"
                :rows="4"
                placeholder="请输入内容"
                v-model="textarea"
              >
              </el-input>
            </el-col>
          </el-row>
          <el-row v-if="blogInfo.blogId !== 33">
            <el-col :push="22" :span="2">
              <el-button type="primary" @click="create()">评论</el-button>
            </el-col>
          </el-row>
          <el-row v-if="blogInfo.blogId !== 33">
            <el-col>
              <el-divider content-position="left"
                ><i class="el-icon-chat-line-square"></i>全部评论</el-divider
              >
            </el-col>
          </el-row>
          <div v-for="comment in commentList" v-if="blogInfo.blogId !== 33">
            <el-row>
              <el-col :span="2">
                <div>
                  <el-avatar :src="imgUrl"></el-avatar>
                </div>
              </el-col>
              <el-col :span="4">
                <div>
                  <span>{{ comment.commentator }}</span>
                </div>
              </el-col>
            </el-row>
            <el-row>
              <el-col :span="4" :push="2">
                <span>{{ comment.commentBody }}</span>
              </el-col>
              <el-col :span="4" :push="18">
                <span>{{ comment.commentCreateTime | moment }}</span>
              </el-col>
            </el-row>
            <el-row>
              <el-col :span="4" :push="2">
                <el-popover placement="bottom" width="400" trigger="click">
                  <el-input
                    type="textarea"
                    :rows="4"
                    placeholder="请输入内容"
                    v-model="replyBody"
                  >
                  </el-input>
                  <el-row v-if="blogInfo.blogId !== 33">
                    <el-col :push="20" :span="2">
                      <el-button
                        type="primary"
                        @click="reply(comment.commentId)"
                        >回复</el-button
                      >
                    </el-col>
                  </el-row>
                  <el-link slot="reference">回复</el-link>
                </el-popover>
              </el-col>
            </el-row>
            <el-row>
              <el-col :span="4" :push="2">
                <span>{{ comment.replyBody }}</span>
              </el-col>
              <el-col :span="4" :push="18">
                <span>{{comment.replyCreateTime | moment}}</span>
              </el-col>
            </el-row>
            <el-row>
              <el-col>
                <el-divider content-position="left"></el-divider>
              </el-col>
            </el-row>
          </div>
        </el-footer>
      </el-container>
    </el-main>
  </el-container>
</template>

<script>
import { getBlogInfo } from "@/api/blogmanager/blog";
import qs from "qs";
import BlogComment from "./BlogComment";
import comment from "bright-comment";
import { pageComment } from "@/api/blogmanager/blogComment";
import { blogDetail } from "@/api/front/blogView";
import { createComment, replyComment } from "../../api/blogmanager/blogComment";
import {getCurrentLikeStatus, likeBlog} from "../../api/front/blogView";
export default {
  name: "BlogDetail",
  components: {
    BlogComment,
    comment,
  },
  data() {
    return {
      blogInfo: {},
      textarea: "",
      commentList: [],
      imgUrl: this.$store.state.userUrl,
      blogStatus: this.$route.query.blogStatus,
      replyBody: "",
      blogLikeStatusDto: {}
    };
  },
  created() {
    this.getBlogInfo();
    this.getLikeStatus();
  },
  methods: {
    getLikeStatus(){
      const _this = this;
      getCurrentLikeStatus(qs.stringify({
        blogId: this.$route.query.blogId
      })).then((res) =>{
          if(res.code === 2000){
            _this.blogLikeStatusDto = res.data;
            _this.blogInfo.blogLikes = _this.blogLikeStatusDto.blogLikes;
          }
      })
    },
    likeBlog(){
      const _this = this;
      likeBlog(qs.stringify({
        blogId: this.blogInfo.blogId
      })).then((res) =>{
        if(res.code === 2000){
          /*
          _this.$message({
            showClose: true,
            message: "点赞成功",
            type: "success",
          });*/
          _this.getLikeStatus();
        }
      })
    },
    reply(commentId) {
      const _this = this;
      replyComment(
        qs.stringify({
          commentId: commentId,
          replyBody: this.replyBody,
        })
      ).then((res) => {
        if (res.code == 2000) {
          _this.$message({
            showClose: true,
            message: "回复成功",
            type: "success",
          });
          pageComment(
            qs.stringify({
              pageNum: 1,
              pageSize: 5,
              blogId: _this.$route.query.blogId,
            })
          ).then((res) => {
            _this.commentList = res.data;
          });
        } else if (res.code == 5002) {
          _this.$message({
            showClose: true,
            message: res.message,
            type: "warning",
          });
        } else {
        }
      });
    },
    create() {
      const _this = this;
      createComment(
        qs.stringify({
          blogId: this.blogInfo.blogId,
          commentBody: this.textarea,
        })
      ).then((res) => {
        if (res.code == 2000) {
          _this.$message({
            showClose: true,
            message: "评论成功",
            type: "success",
          });
          pageComment(
            qs.stringify({
              pageNum: 1,
              pageSize: 5,
              blogId: _this.$route.query.blogId,
            })
          ).then((res) => {
            _this.commentList = res.data;
          });
        } else if (res.code == 5002) {
          _this.$message({
            showClose: true,
            message: res.message,
            type: "warning",
          });
        } else {
        }
      });
    },
    getBlogByTag(blogCategoryName) {
      this.$router.push({
        path: "index",
        query: {
          blogCategoryName: blogCategoryName,
        },
      });
    },
    goBack() {
      this.$router.push({
        path: "/index",
      });
    },
    getBlogInfo() {
      blogDetail(
        qs.stringify({
          blogId: this.$route.query.blogId,
        })
      ).then((res) => {
        this.blogInfo = res.data;
      });
      pageComment(
        qs.stringify({
          pageNum: 1,
          pageSize: 5,
          blogId: this.$route.query.blogId,
        })
      ).then((res) => {
        this.commentList = res.data;
      });
    },
  },
};
</script>

<style scoped>
.el-container {
  display: flex;
}
.blog {
  padding-top: 5px;
  padding-right: 10px;
  padding-bottom: 10px;
  padding-left: 15px;
  font-family: 微软雅黑;
  font-size: 12px;
}
</style>
