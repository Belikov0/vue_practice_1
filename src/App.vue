<script setup>
    import {ref, reactive} from 'vue'

    import TabItem from '../components/TabItem.vue';
    import TabList from '../components/TabList.vue';
    import Tab from '../components/Tab.vue';
    //创建一个变量记录选项卡的状态
    const curr = ref(0)


  // 假设获取到的数据还未排序，实际上在数据库操作时应该已经排序
    const playersArr = [
      {
        name: "梅西",
        ranking: 1,
        imgPath: "/images/messi.png",
        hot: 433760,
      },
      {
        name: "内马尔",
        ranking: 3,
        imgPath: "/images/neymar.png",
        hot: 133760,
      },
      {
        name: "C罗",
        ranking: 2,
        imgPath: "/images/ronaldo.png",
        hot: 235760,
      }
    ].sort((a, b) => b.hot-a.hot)

    const teamsArr = [
    {
        name: "法国",
        ranking: 1,
        imgPath: "/images/法国.jpg",
        hot: 433760,
      },
      {
        name: "荷兰",
        ranking: 3,
        imgPath: "/images/荷兰.jpg",
        hot: 133760,
      },
      {
        name: "巴西",
        ranking: 2,
        imgPath: "/images/巴西.jpg",
        hot: 235760,
      }
    ].sort((a, b) => b.hot-a.hot)

    //设置排名
    for (let i in playersArr){
      console.log(typeof(i))
      playersArr[i].ranking = parseInt(i)+1
      teamsArr[i].ranking = parseInt(i)+1
    }

    //设置为响应式对象
    const players = reactive(playersArr)
    const teams = reactive(teamsArr)

    //获取最大热度
    const  playerMaxHot = players[0].hot
    const teamMaxHot = teams[0].hot

</script>

<template>
  <!-- 外部容器 -->

      <Tab>
        <template v-slot:p>
          <TabList :item-list="players" :max-hot="playerMaxHot"></TabList>
        </template>
        <template v-slot:t>
          <TabList :item-list="teams" :max-hot="playerMaxHot"></TabList>
        </template>
      </Tab>
      

</template>


<style>
  *{
    padding: 0;
    margin: 0;
  }
</style>