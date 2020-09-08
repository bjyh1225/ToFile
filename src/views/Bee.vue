<template>
  <div class="body-back">
    <div class="index-top">
      <div class="index-top-box">
        <img class="index-top-logo" src="@/assets/img/icon.png" alt />
        <div class="index-top-right">
          <div
            v-for="(item, index) in indexTop"
            :key="index"
            :class="{ active: index == curryIndex }"
            @click="changeTab(index)"
          >
            <span>{{ item }}</span>
          </div>

          <!-- <div @click="selTab">产品与服务</div> -->
          <ul v-if="show" class="nav-sel">
            <li class="bold">产品推荐</li>
            <li>ePUBee魔方</li>
            <li>ePUBee电子书管理</li>
            <li>ePUBee智多星</li>
            <li>ePUBee豆瓣插件</li>
            <li>电子书转换器</li>
            <li class="bold">核心介绍</li>
            <li>如何使用send to kindle服务</li>
            <li class="bold">eCore电子书核心</li>
            <li>ePUBee DRM Rernoval</li>
            <li class="bold">其他转换服务</li>
            <li>Kindle转PDF</li>
            <li>Epub转PDF</li>
            <li>Epub转Mobi</li>
            <li>Txt转Epub</li>
          </ul>
        </div>
      </div>
    </div>
    <div class="fixed">切换旧版</div>

    <div class="index-cont">
      <div>
        <h2 class="index-cont-h2">小蜜蜂在线电子书转换器</h2>
        <h2>Online ebook converter</h2>
      </div>
      <div class="index-cont-p">
        <a href="javascript:;">点击下载桌面版,除了电子书转换、管理,还能给DRM脱壳</a>
        <div>
          <span>Cloud ID :</span>
          <span>47099723</span>
          <!-- <img src="@/assets/img/icon-cloud.png" /> -->
          <el-tooltip placement="top" effect="light" :visible-arrow="false">
            <div slot="content">
              "CloudID"用于管理上传和转换的电子书，进去后点击"后缀名"下载电子书，点"编辑"来编辑Meta元数据和转换电子书格式。
              <br />上传完成后会显示进度图片，鼠标移动至图片可以查看状态是"排队"还是"转换中"，排队加转换可能持续几个小时。如果关闭了网页，队
              <br />列会靠后，服务器也会继续执行，转换生成的文件会保存到ID里，点击CloudID可以查看并下载。
              <br />"下载"链接自显示后20分钟内有效，如果下载时出现"超时"，请到点击CloudID到电子书管理器里下载。
            </div>
            <img src="@/assets/img/icon-cloud.png" />
          </el-tooltip>
        </div>
      </div>
      <!-- 上传 -->
      <div class="index-cont-box">
        <!-- 上传选项 -->
        <div class="index-cont-box-sel">
          <div class="sel-cont">
            <img src="@/assets/img/icon-add.png" alt />
            <span>添加更多文件</span>
            <img src="@/assets/img/icon-del.png" alt />
            <span>清空列表</span>
          </div>
          <div>
            <span class="gap">全部转换为</span>
            <el-cascader
              :options="options"
              :show-all-levels="false"
              placeholder="EPUB"
              :visible-arrow="false"
            ></el-cascader>
            <!-- <span>epub</span> -->
            <!-- <img src="@/assets/img/icon-down.png" alt /> -->
          </div>
          <div class="btn">全部下载</div>
        </div>
        <!-- 上传区域 -->
        <div class="add-file">
          <el-upload
            class="upload-demo"
            drag
            action="https://jsonplaceholder.typicode.com/posts/"
            multiple
          >
            <img src="@/assets/img/icon-add-file.png" alt />
            <!-- <i class="el-icon-upload"></i> -->
            <div class="el-upload__text">拖拽或点击上传电子书</div>
          </el-upload>
          <!-- <img src="@/assets/img/icon-add-file.png" alt />
          <p>拖拽或点击上传电子书</p>-->
          <p>
            支持格式: AZW, PRC, MOBI, AZW3, AZW4, EPUB, TXT
            <span>可转换格式: PDF, EPUB, MOBI, TXT</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      indexTop: [
        '首页',
        '在线电子书转换器',
        '电子书制作',
        '产品与服务',
        '技术向导',
      ],
      curryIndex: 0,
      show: false,
      tips: '',

      options: [
        {
          value: 'picture',
          label: '图像',
          children: [
            {
              value: 'jpg',
              label: 'JPG',
            },
            {
              value: 'png',
              label: 'PNG',
            },
            {
              value: 'svg',
              label: 'SVG',
            },
          ],
        },
        {
          value: 'dianzishu',
          label: '电子书',
          children: [
            {
              value: 'epub',
              label: 'EPUB',
            },
            {
              value: 'mobl',
              label: 'MObl',
            },
            {
              value: 'pdf',
              label: 'PDF',
            },
            {
              value: 'pdfA6',
              label: 'PDF(A6)',
            },
            {
              value: 'docx',
              label: 'DOCX',
            },
          ],
        },
      ],
    }
  },
  methods: {
    changeTab(index) {
      this.curryIndex = index
      if (this.curryIndex == 3) {
        this.show = !this.show
      }
    },
  },
}
</script>

<style scoped>
.body-back {
  width: 1272px;
  background: url('../assets/img/Bg.png') no-repeat;
  background-position: right;
}
.index-top {
  width: 100%;
  height: 75px;
  background: rgba(255, 255, 255, 0.5);
  box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}
.index-top-box {
  width: 1272px;
  height: 75px;
  margin: 0 auto;
}
.index-top-logo {
  width: 129px;
  height: 67px;
  float: left;
}
.index-top-right {
  float: right;
}
.index-top-right div {
  display: inline-block;
  padding: 8px 32px;
  border-radius: 4px;
  margin-left: 40px;
  margin-top: 19px;
  text-align: center;
}
.active {
  background: #ffd657;
  box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.2);
  font-weight: bold;
}
.nav-sel {
  position: absolute;
  right: 168px;
  top: 83px;
}

ul {
  width: 215px;
  height: 388px;
  background: rgba(255, 255, 255, 0.5);
  box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.1);
  border-radius: 0px 0px 4px 4px;
  padding: 16px 0;
}
li {
  height: 26px;
  line-height: 26px;
  font-size: 14px;
  text-indent: 16px;
  font-weight: 400;
}
li:hover {
  background: rgba(0, 0, 0, 0.08);
}
.bold {
  font-weight: 600;
  line-height: 24px;
  height: 24px;
}
.fixed {
  width: 14px;
  height: 80px;
  padding: 12px;
  background: #ffffff;
  box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  font-size: 14px;
  line-height: 20px;
  position: fixed;
  right: 16px;
  top: 48%;
  z-index: 9;
}
.index-cont {
  width: 1272px;
  margin: 0 auto;
}
.index-cont-h2 {
  padding-top: 280px;
  width: 520px;
  font-size: 46px;
  font-family: PingFangSC-Semibold, PingFang SC;
  font-weight: 600;
  color: rgba(0, 0, 0, 0.8);
  line-height: 67px;
}
.index-cont h2:last-child {
  font-size: 42px;
  line-height: 0;
}

.index-cont-p {
  margin: 16px;
  height: 25px;
}
.index-cont-p a {
  float: left;
  height: 25px;
  font-size: 18px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: #007aff;
  line-height: 25px;
}
.index-cont-p div {
  float: right;
  width: 200px;
  font-size: 18px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(0, 0, 0, 0.8);
  line-height: 25px;
}
.index-cont-p div span:last-of-type {
  color: #007aff;
}
.index-cont-p div img {
  vertical-align: sub;
  margin-left: 2px;
}
.index-cont-box {
  width: 1272px;
  height: 522px;
  background: rgba(255, 255, 255, 0.9);
  box-shadow: 0px 2px 8px 0px rgba(0, 0, 0, 0.1);
  margin: 0 auto;
  padding-top: 8px;
  margin-bottom: 106px;
}
.index-cont-box-sel {
  width: 1256px;
  height: 70px;
  background: #ffd657;
  box-shadow: 0px -2px 8px 0px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.sel-cont {
  margin-left: 16px;
}
.sel-cont span {
  margin: 0 24px 0 4px;
}
.index-cont-box-sel img {
  vertical-align: sub;
}
.gap {
  margin-right: 16px;
}
/deep/.el-cascader .el-input .el-input__inner {
  text-overflow: clip;
}
/deep/ .el-input {
  width: 90px;
  height: 32px;
  line-height: 32px;
  border-radius: 4px;
  border: 1px solid rgba(0, 0, 0, 0.6);
  background-color: #ffd657;
}
/deep/.el-input__inner {
  width: 90px;
  height: 32px;
  border-radius: 4px;
  border: 1px solid rgba(0, 0, 0, 0.6);
  background-color: #ffd657;
  padding: 0 4px;
}
/deep/.el-input__icon {
  line-height: 32px;
  color: rgba(0, 0, 0, 0.6);
}

.btn {
  width: 136px;
  height: 38px;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 4px;
  text-align: center;
  line-height: 38px;
  margin-right: 16px;
}
.add-file {
  width: 1272px;
  height: 452px;
  background: rgba(255, 255, 255, 0.9);
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}
.add-file /deep/ .el-upload-dragger {
  width: 1240px;
  height: 380px;
  margin-top: 16px;
  border: 1px dashed #ffc100;
}
.add-file img {
  margin-top: 120px;
  width: 72px;
  height: 72px;
  background: #ffffff;
  box-shadow: 0px 2px 8px 0px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
}
.add-file /deep/.el-upload__text {
  font-size: 20px;
  font-family: PingFangSC-Regular, PingFang SC;
  font-weight: 400;
  color: rgba(0, 0, 0, 0.6);
  margin-top: 20px;
}
.add-file p {
  font-family: PingFangSC-Regular, PingFang SC;
  color: rgba(0, 0, 0, 0.6);
  font-size: 20px;
}
.add-file p span {
  margin-left: 16px;
}
.add-file p:last-child {
  bottom: 16px;
  position: absolute;
  padding: 0;
  margin: 0;
}
</style>
