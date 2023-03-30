<script setup>
import { ref } from 'vue'
const curr = ref(0)
</script>

<template>
    <!-- 外部容器 -->
    <div class="tab-wrapper">
        <!-- 选项卡头部 -->
        <header class="tab-head">
            <button @click="curr = 0" class="tab-button" :class="{ active: curr == 0 }">热门球员</button>
            <button @click="curr = 1" class="tab-button" :class="{ active: curr == 1 }">热门球队</button>
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
            <div v-show="curr == 0">
                <!-- 列表 -->
                <slot name="p"></slot>
            </div>

            <div v-show="curr == 1">
                <!-- 列表 -->
                <slot name="t"></slot>
            </div>
        </div>
    </div>
</template>

<style scoped>
.tab-wrapper {
    box-sizing: border-box;
    width: 800px;
    padding: 20px;
    background-color: rgb(45, 83, 211);
}

.tab-head {
    display: flex;
    border-radius: 10px;
    /* 
      子元素充满了父元素，会溢出使得圆角失效，
      设置overflow:hidden使之生效 
    */
    overflow: hidden;
}

.tab-button {
    font-size: 30px;
    padding: 10px 0;
    background-color: white;
    flex: auto;
    cursor: pointer;
    transition: 0.2s
}

/* 为不是active的button设置hover的字体颜色 */
.tab-button:not(.active):hover {
    color: rgb(187, 35, 2);

}

.active {
    background-color: rgb(187, 35, 2);
    color: white
}

.main {
    /* color:white;
    font-size: 20px; */
}
</style>