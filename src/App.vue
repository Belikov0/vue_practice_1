<script setup>
    import {ref} from 'vue'
    //创建一个变量记录选项卡的状态
    const curr = ref(0)

</script>

<template>
  <!-- 外部容器 -->
  <div class="tab-wrapper">
    <!-- 选项卡头部 -->
      <header class="tab-head">
        <button @click="curr=0" class="tab-button" :class="{active:curr==0}">热门球员</button>

        <button @click="curr=1" class="tab-button" :class="{active:curr==1}">热门球队</button>
      </header>
    <!-- 选项卡主体 -->
      <div class="main">
        <!-- 
          curr == 0 显示球员
          curr == 1 显示球队
            v-show指令：条件满足显示，条件不满足不显示
            v-show的原理是通过设置display:none来控制元素的显示 
         -->
         <!-- 球员信息 -->
          <div v-show="curr === 0">
            <!-- 列表 -->
            <div class="tab-list">
              <div class="tab-item">
                <div class="photo"><img src="/images/messi.png" alt="messi"><span>1</span></div>
                <div class="desc">
                  <span class="name">梅西</span>
                  <div class="hot-bar">
                    <div class="inner">
                      433760热度
                    </div>
                  </div>
                </div>
              </div>
              <div class="tab-item">
                <div class="photo"><img src="/images/messi.png" alt="messi"><span>1</span></div>
                <div class="desc">
                  <span class="name">梅西</span>
                  <div class="hot-bar">
                    <div class="inner">
                      433760热度
                    </div>
                  </div>
                </div>
              </div>
              <div class="tab-item">
                <div class="photo"><img src="/images/messi.png" alt="messi"><span>1</span></div>
                <div class="desc">
                  <span class="name">梅西</span>
                  <div class="hot-bar">
                    <div class="inner">
                      433760热度
                    </div>
                  </div>
                </div>
              </div>
              
              
              
            </div>
          </div>
          <!-- 球队信息 -->
          <div v-show="curr === 1">

            <div class="tab-list">
              <div class="tab-item">
                <div class="photo">
                  <img src="/images/法国.jpg" alt="messi"><span>1</span></div>
                <div class="desc">
                  <span class="name">法国</span>
                  <div class="hot-bar">
                    <div class="inner">
                      433760热度
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
      </div>
  </div>
</template>

<style scoped>
  .tab-wrapper {
    box-sizing: border-box;
    width: 800px;
    padding: 20px;
    background-color:rgb(45, 83, 211);
  }
  .tab-head{
    display: flex;
    border-radius: 10px;
    /* 
      子元素充满了父元素，会溢出使得圆角失效，
      设置overflow:hidden使之生效 
    */
    overflow: hidden; 
  }

  .tab-button{
    font-size: 30px;
    padding: 10px 0;
    background-color: white;
    flex:auto;
    cursor:pointer;
    transition:0.2s
  }

/* 为不是active的button设置hover的字体颜色 */
  .tab-button:not(.active):hover{
    color:rgb(187,35,2) ;
  }

  .active{
    background-color: rgb(187,35,2);
    color:white
  }

  .main{
    /* color:white;
    font-size: 20px; */
  }

  .tab-list{
    margin: 20px;
  }

  .tab-item{
    display: flex;
    margin-bottom: 30px;
  }

  .photo{
    width: 150px;
    background-color: white;
    border-radius: 25px;
    overflow: hidden;
    position: relative;
  }

  .photo img{
    width:100%;
        /* 图片默认对齐方式为基线对齐，会出现一条缝 */
    vertical-align: top;
  }

  .photo span{
    position: absolute;
    top:0;
    left:0;
    width: 50px;
    height: 50px;
    color: white;
    background-color: orange;
    font-size: 25px;
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom-right-radius: 20px;
  }

  .desc{
    font-size: 30px;
    color:white;
    display: flex;
    flex-flow: column;
    flex:auto;
    justify-content: space-evenly;
    /* background-color: #bfa; */
    margin-left: 30px;
  }

  .hot-bar{
    background-color: #bfa;
    border-radius: 20px;
    background-color: rgb(3,37,103);
    /* 缩进半个字的距离 */
    text-indent: 0.5em;
  }

  .inner{
    background-color: red;
    border-radius: 20px;
    background-image: linear-gradient(90deg,rgb(187,3,52) 50%, rgb(66,2,12));
    /* 禁止文字换行，使文字能够溢出 */
    white-space: nowrap;
  }


</style>

<style>
  *{
    padding: 0;
    margin: 0;
  }
</style>