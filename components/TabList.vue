<script setup>
import TabItem from './TabItem.vue';

const props = defineProps(["itemList", "maxHot"])
const itemList = props.itemList
</script>

<template>
    <!-- 列表 -->
    <div class="tab-list">
        <!-- v-for遍历数组 -->
        <TabItem v-for="item in itemList" :item="item" :max-hot="props.maxHot"></TabItem>
    </div>
</template>


<style scoped>
.tab-list {
    margin: 20px;
}
</style>