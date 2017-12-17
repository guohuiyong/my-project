<template>
  <div>
    <header class="header">
    	<div class="back iconfont">&#xe62c;</div>
    	<div class="search"><a href="#" class="search-cont"><i class="glass iconfont">&#xe63b;</i>输入城市/景点/游玩主题</a></div>
    	<div class="city">城市</div>
    </header>

    <swiper :options="swiperOption">
      <swiper-slide v-for="item in swiperInfo" :key="item.id">
        <div class="swiper-img-con">
          <img  class="swiper-img" :src="item.imgUrl"/>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>  	
    </swiper> 

     <swiper :options="iconOption">
      <swiper-slide v-for="(pageInfo, index) in pages" :key="index">
        <div class="icon-wrapper">
          <div v-for="item in pageInfo" :key="item.id" class="icon-item">
            <div class="icon-img-con">
              <img  class="icon-img" :src="item.imgUrl"/>
            </div>
            <div class="icon-name">{{item.name}}</div>
          </div>
        </div>
      </swiper-slide> 
      <div class="icon-pagination"  slot="pagination"></div> 
    </swiper> 
    
    <ul class="listen-con">
      <li class="listentrance-item border-left"><i class="localize iconfont">&#xe611;</i> 定位失败</li>
      <li class="listentrance-item"><i class="localize iconfont">&#xe600;</i> 5折泡温泉</li>
    </ul>
    <ul class="activity-con">
      <li class="activity-item" v-for="(item, index) in activityInfo" :key="index">
        <div class="activity-img-con">
          <img class="activity-img" :src="item.imgUrl"/>
        </div>
      </li>
    </ul>

    <div class="lazy-load" id="hot-sight">
      <h2 class="modtitle">热销推介</h2>
      <div class="hot-con">
        <ul class="hotList">
          <li class="hot-pron" v-for="(item, index) in hotListInfo" :key="index">
            <a href="">
              <div class="hotlist-img">
                <img class="Img" :src="item.imgUrl"/>
              </div>
              <div class="hotlist-infos">
                <div class="hotlist-title">{{item.title}}</div>
                <div class="hotlist-desc">{{item.desc}}</div>
              </div>
              <div class="price">
                ￥<em class="price-num">{{item.num}}</em>
                <span class="price-text">{{item.text}}</span>
              </div>
            </a>
          </li>
        </ul>
      </div>
      <div class="more">
        <a class="more-link" href="#">查看所有产品</a>
      </div>
    </div>

    <div class="lazy-load" id="weekend-trip">
      <h2 class="modtitle">周末去哪儿</h2>
      <div>
        <div class="product-list" v-for="(item, index) in productInfo" :key="index">
          <a class="productlink"  href="#">
            <div class="product-img-con">
              <img class="product-img" :src="item.imgUrl"/>
            </div>
            <div class="product-info">
              <p class="info-title">{{item.title}}</p>
              <p class="info-text">{{item.text}}</p>
            </div>
          </a>
        </div>
      </div>
    </div>

    <div class="price-reminding">
      <span class="reminding iconfont">&#xe61b;</span>
      <div class="reminding-text">
        <span class="bold">票面价</span>是指通过景区指定窗口售卖的纸质门票上标注的价格
      </div>
    </div>

    <footer class="footer">
      <div class="footer-nav">
        <ul class="nav-list">
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">机票</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">酒店</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">公寓地</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购好</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购好</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购好</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购好</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购好</div>
            </a>
          </li>
          <li class="list-son">
            <a href="#">
              <span class="list-son-icon iconfont">&#xe600;</span>
              <div class="list-son-desc">团购</div>
            </a>
          </li>
          <li class="tar toggle">
            <span class="tar-icon iconfont">&#xe600;</span>
            <div class="tar-desc">收起</div>
          </li>
        </ul>
      </div>
      <ul class="other-nav">
        <li>
          <a href="#">登录</a>
        </li>
        <li>
          <a href="#">我的订单</a>
        </li>
        <li>
          <a href="#">个人中心</a>
        </li>

        <li>
          <a href="#">最近浏览</a>
        </li>
        <li>
          <a href="#">关于我们</a>
        </li>
      </ul>
      <ul class="mobile-pc">
        <li><a href="">触屏版</a></li>
        <li><a href="">移动版</a></li>
      </ul>
      <div class="copyright">
        <span>Qunar 京ICP备05021087</span>
        <a href="">意见反馈</a>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      swiperInfo: [],
      iconInfo: [],
      activityInfo: [],
      hotListInfo: [],
      productInfo: [],
      swiperOption: {
        autoplay: 10000,
        direction: 'horizontal',
        pagination: '.swiper-pagination',
        loop: true
      },
      iconOption: {
        pagination: '.icon-pagination'
      }
    }
  },

  computed: {
    pages () {
      const pages = []
      this.iconInfo.forEach((value, index) => {
        let page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(value)
      })
      return pages
    }
  },

  methods: {
    getIndexData () {
      this.$http.get('/static/index.json')
        .then(this.handleGetDataSucc.bind(this))
    },

    handleGetDataSucc (res) {
      const body = res.body
      if (body && body.data && body.data.swiper) {
        this.swiperInfo = body.data.swiper
        this.iconInfo = body.data.icons
        this.activityInfo = body.data.activitys
        this.hotListInfo = body.data.hotLists
        this.productInfo = body.data.products
        console.log(this.productInfo)
      }
    }
  },

  created () {
    this.getIndexData()
  }
}
</script>

<style scoped>
  .header {
    display: flex;
    background: #05bad5;
    color: #fff;
  }
  .back {
  	width: .64rem;
  	line-height: .86rem;
    text-align: center;
  }
  .search {
  	flex: 1;
  	margin: 0.14rem 0.18rem;
  	background: #fff;
  	border-radius: 0.1rem;
  }
  .search-cont {
    color: #e4e7ea;
    font-size:0.28rem;
    line-height: 0.6rem;
  }
  .glass {
    margin:0 0.15rem;
    line-height: 0.6rem;
  }
  .city {
  	width: 1.14rem;
  	line-height: 0.86rem;
  	text-align: left;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .city::after{
    content:"";
    display: block;
    width: 0px;
    height: 0px;
    border: 0.1rem solid #fff;
    border-color: white transparent transparent transparent;
    position: absolute;
    right: 0.3rem;
    top: 0.36rem;
  }
  .swiper-img-con {
    overflow: hidden;
  	width: 100%;
    height: 0;
    padding-bottom: 31.25%;
  }
  .swiper-img {
  	width: 100%;
  }
  .icon-wrapper {

  }
  .icon-item {
    box-sizing: border-box;
    float: left;
    width: 25%;
    padding-top: .4rem;
    text-align: center;
  }
  .icon-img-con {
    display: inline-block;
    width: 0.66rem;
    height: 0.66rem;
  }
  .icon-img {
    width: 100%;
  }
  .icon-name {
    /* box-sizing: border-box; */
    margin-top: .2rem;
    font-size:.28rem;
    color: #212121;
  }
  .icon-pagination {
    padding: .3rem 0 .12rem 0;
    text-align: center;
  }
  .listen-con {
    display: flex;
    justify-content: space-around;
  }
  .listentrance-item {
    flex: 1;
    height: .98rem;
    line-height: .98rem;
    text-align: center;
    font-size: .28rem;
    color: #212121;
    border-top: 1px solid #e0e0e0; 
  }
  .listen-con::after{
    content: "";
    height: 0.98rem;
    width: 1px;
    position: absolute;
    background: #e0e0e0;
  }
  .activity-con {
    display: flex;
    justify-content: space-around;
    background: #f5f5f5;
    padding-top: .2rem;
  }
  .activity-item {
    flex: 1;
    height: 1.6rem;
    border-top: 1px solid #e0e0e0;
  }
  .activity-con::after{
    content: "";
    height: 1.6rem;
    width: 1px;
    position: absolute;
    background: #e0e0e0;
  }
  .activity-img-con {
    height: 1.6rem;
  }
  .activity-img {
    width: 100%;
    height: 100%;
    background: #fff;
  }
  #hot-sight {
    flex: 1;
  }
  .modtitle {
    height: 0.8rem;
    line-height: 0.8rem;
    background: #f5f5f5;
    color: #212121;
    padding-left: 0.26rem;
  }
  .hot-pron {
    height: 1.4rem;
    padding: 0.24rem;
    border-bottom: 1px solid #e0e0e0;
  }
  .hotlist-img {
    float: left;
    width: 1.4rem;
    height: 1.4rem;
  }
  .Img {
    width: 100%;
    height: 100%;
  }
  .hotlist-infos {
    margin-left: 1.6rem;
  }
  .hotlist-title {
    overflow: hidden;
    font-size: 0.3rem;
    margin: 0.04rem 0 0.1rem 0 ;
    color: #212121;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
  .hotlist-desc {
    overflow: hidden;
    margin-top: 0.1rem;
    height: 0.4rem;
    line-height: 0.4rem;
    color: #9e9e9e;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
  .price {
    margin-left: 1.6rem;
    margin-top: 0.1rem;
    color: #ef8a33;
    font-size: 0.24rem;
  }
  .price-num {
    font-size: 0.36rem;
  }
  .price-text {
    font-size: 0.24rem;
    color: #9e9e9e;
  }
  .more {
    height: 0.88rem;
    color: #00afc7;
    line-height: 0.88rem;
    text-align: center;
  }
  .product-list {
    padding-bottom: 0.1rem;
    background: #f5f5f5;
  }
  .productlink {
    display: block;
    width: 100%;
    height: 100%;
  }
  .product-img-con {
    overflow: hidden;
    height: 0;
    padding-bottom: 37.33%;
  }
  .product-img {
    width: 100%;
  }
  .product-info {
    background: #fff;
    padding: .14rem .2rem .2rem .2rem;
  }
  .info-title {
    color: #212121;
    font-size: 0.28rem;
    line-height: 0.48rem;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
  .info-text {
    color: #616161;
    font-size: 0.24rem;
    line-height: 0.42rem;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
  .price-reminding {
    margin: 0.14rem 0.1rem;
    font-size: 0.24rem;
    color: #616161;
    height: 0.32rem;
  }
  .reminding {
    display: block;
    float: left;
    font-size: 0.2rem;
    line-height: 0.32rem;
    margin-right: 0.1rem;
  }
  .reminding-text {
    float: left;
    line-height: 0.32rem;
  }
  .bold {
    font-weight: 900;
  }
  .footer {
    overflow: hidden;
    background: #f5f5f5;
  }
  .nav-list {
    width: 6rem;
    height: 2.2rem;
    margin: 0 auto;
    padding: .2rem .2rem 0 .2rem;
    position: relative;
  }
  .list-son {
    float: left;
    height: 0.62rem;
    width: 1.3rem;
    margin-left: .2rem;
  }
  .list-son-icon {
    display: block;
    float: left;
    color: #9e9e9e;
  }
  .list-son-desc {
    float: left;
    font-size: 0.24rem;
    color: #9e9e9e;
    margin: .06rem 0 0 .1rem;
    border-bottom: 1px solid #9e9e9e;
  }
  .tar {
    position: absolute;
    top: 2rem;
    right: 0.6rem;
  }
   .tar-icon {
    display: block;
    float: left;
    color: #9e9e9e;
  }
  .tar-desc {
    float: left;
    font-size: 0.24rem;
    color: #9e9e9e;
    margin: .06rem 0 0 .1rem;
    border-bottom: 1px solid #9e9e9e;
  }
  .other-nav {
    width: 100%;
    height: .78rem;
    border-bottom: 1px solid #9e9e9e;
    line-height: .78rem;
  }
  .other-nav li {
    float: left;
    padding-left: .4rem;
  }
  .other-nav li a {
    font-size: .28rem;
  }
  .mobile-pc {
    padding-top: .2rem;
    text-align: center;
  }
  .mobile-pc li {
    display: inline-block;
    margin: 0 0.3rem;
  }
  .mobile-pc li a {
    font-size: .28rem;
  }
  .copyright {
    padding:.2rem;
    text-align: center;
    font-size: .28rem;
    color: #9e9e9e;
  }
  .copyright a {
    color: #9e9e9e;
  }
</style>