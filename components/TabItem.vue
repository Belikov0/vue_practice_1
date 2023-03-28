<script setup>
    import { ref, reactive } from "vue"

    /*
        子组件中的数据通常不在子组件中直接定义，否则会导致数据耦合
        子组件中的数据通常在创建组件实例时确定

        父组件可以通过props来将数据传递给子组件***

        使用步骤
            - 在子组件中定义props, 可以在组合式API中直接使用
            - 
    */

    //宏指令
    //定义了属性item，item为属性名
    const props = defineProps(["item"])
    console.log(props.item)
</script>

<template>
    <div class="tab-item">
        <div class="photo">
            <img :src="props.item.imgPath" :alt="props.item.name">
            <span>{{ props.item.ranking }}</span>
        </div>
        <div class="desc">
            <span class="name">{{props.item.name}}</span>
            <div class="hot-bar">
                <div class="inner">
                    {{ props.item.hot }}热度
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
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