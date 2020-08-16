<template>
  <view class="center">
    <!-- 头像 -->
    <view class="center-list">
      <view class="center-list-item border-bottom" @click="photoClick">
        <text class="list-text">头像</text>
        <view class="list-right">
          <!-- <text class="list-icon">&#xe614;</text> -->
          <image class="logo-img" :src="userInfo.img"></image>
          <text class="navigat-arrow">&#xe65e;</text>
        </view>
      </view>
    </view>

    <view class="center-list">
      <view class="center-list-item border-bottom" @click="nameClick">
        <text class="list-text">用户名</text>
        <view class="list-right">
          <!-- <text class="list-icon">&#xe614;</text> -->
          <text>{{userInfo.user}}</text>
          <text class="navigat-arrow">&#xe65e;</text>
        </view>
      </view>
    </view>
    <view class="center-list">
      <view class="center-list-item border-bottom" @click="moreClick">
        <text class="list-text">更多</text>
        <view class="list-right">
          <!-- <text class="list-icon">&#xe614;</text> -->
          <text class="navigat-arrow">&#xe65e;</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      userInfo: {}
    };
  },
  onLoad(options) {},
  onShow() {
    console.log("on show");
  },
  methods: {
    photoClick: function(event) {
      console.log("photoClick");
    },
    nameClick: function(event) {
      console.log("nameClick");
    },
    moreClick: function(event) {
      console.log("moreClick");
    },
  },
  onLoad(options) {
    this.userInfo = JSON.parse(decodeURIComponent(options.userInfo)) || {}
  }
};
</script>

<style lang="scss" scoped>

@font-face {
  font-family: texticons;
  font-weight: normal;
  font-style: normal;
  src: url("https://at.alicdn.com/t/font_984210_5cs13ndgqsn.ttf")
    format("truetype");
}

page,
view {
  display: flex;
}

page {
  background-color: #f8f8f8;
}

.center {
	flex-direction: column;
}

.center-list {
  background-color: #ffffff;
  margin-top: 20upx;
  width: 750upx;
  flex-direction: column;
}

.center-list-item {
  height: 90upx;
  width: 750upx;
  box-sizing: border-box;
  flex-direction: row;
  justify-content: space-between;
  padding: 0upx 20upx;
}

.border-bottom {
  border-bottom-width: 1upx;
  border-color: #c8c7cc;
  border-bottom-style: solid;
}

.list-icon {
  width: 40upx;
  height: 90upx;
  line-height: 90upx;
  font-size: 34upx;
  color: #4cd964;
  text-align: center;
  font-family: texticons;
  margin-right: 20upx;
}

.list-text {
  height: 90upx;
  line-height: 90upx;
  font-size: 34upx;
  color: #555;
  flex: 1;
  text-align: left;
}

.list-right {
  flex-direction: row;
  align-items: center;
  .logo-img {
    width: 72upx;
    height: 72upx;
    border-radius: 72upx;
  }
}

.navigat-arrow {
  height: 90upx;
  width: 40upx;
  line-height: 90upx;
  font-size: 34upx;
  color: #555;
  text-align: right;
  font-family: texticons;
}
</style>