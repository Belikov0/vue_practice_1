<script setup>
    import {computed} from 'vue'
    const props = defineProps(["hot", "maxHot"])
    const width = computed(() =>{
        return (props.hot/props.maxHot) * 100 + "%"
    })
</script>

<template>
    <div class="hot-bar">
        <div class="inner">
            {{ props.hot }}热度
        </div>
    </div>
</template>

<style scoped>
    .hot-bar{
        background-color: #bfa;
        border-radius: 20px;
        background-color: rgb(3,37,103);
        /* 缩进半个字的距离 */
        text-indent: 0.5em;
    }

    .inner{
        /* 设置进度 */
        width: v-bind(width);
        background-color: red;
        border-radius: 20px;
        background-image: linear-gradient(90deg,rgb(187,3,52) 50%, rgb(66,2,12));
        /* 禁止文字换行，使文字能够溢出 */
        white-space: nowrap;
    }
</style>