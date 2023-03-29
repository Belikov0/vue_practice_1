<script setup>
    import { ref, reactive } from "vue"
    import Photo from "./Photo.vue";
    import HotBar from "./HotBar.vue";

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
    const props = defineProps(["item", "maxHot"])
    const item = props.item
</script>

<template>
    <div class="tab-item">
        <Photo :src="item.imgPath" :alt="item.name"
          :ranking="item.ranking"></Photo>
        <div class="desc">
            <span class="name">{{item.name}}</span>
            <HotBar :hot="item.hot" :max-hot="props.maxHot"></HotBar>
        </div>
    </div>
</template>

<style scoped>
.tab-item{
    display: flex;
    margin-bottom: 30px;
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

 
</style>