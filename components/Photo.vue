<script setup>
    import {computed} from 'vue'
    const props = defineProps([
        "src",
        "alt",
        "ranking"
    ])
    /**
     * 第一名： rgb(254, 45, 70)
     * 第二名： rgb(245, 102, 1)
     * 第三名： rgt(247, 169, 1)
     */

    const color = computed(() =>{
        if (props.ranking == 1)
            return "rgb(254, 45, 70)"
        else if (props.ranking == 2)
            return "rgb(245, 102, 1)" 
        else 
            return "rgb(247, 169, 1)"
    })
  
</script>

<template>
    <div class="photo">
            <img :src="props.src" :alt="props.alt">
            <span>{{ props.ranking }}</span>
        </div>
</template>

<style scoped>
    
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
    background-color: v-bind(color);
    top:0;
    left:0;
    width: 50px;
    height: 50px;
    color: white;
    font-size: 25px;
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom-right-radius: 20px;
  }
</style>