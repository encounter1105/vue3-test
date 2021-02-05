<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h2>欢迎来到太极开发者社区</h2>
  <div>
    请选择一个讨论组加入
  </div>
  <div>
    <button 
      v-for="(item,index) in forums" 
      :key="index"
      @click="selectForumFun(index)"
      >
        {{ index }} -{{ item }}
    </button>
  </div>
  <div>你选择了【 {{ selectForum }} 】讨论组加入！</div>
</template>

<script lang="ts">
import { 
  reactive, 
  toRefs,
  onMounted,
  onBeforeMount,
  onBeforeUpdate,
  onUpdated,
  onRenderTracked,
  onRenderTriggered,
  } from 'vue';

interface DataProps {
  forums: string[];
  selectForum: string;
  selectForumFun: (index: number) => void;
}


export default{
  name: 'App',
  setup() {
    console.log("1-开始创建组件-----setup()");
    const data: DataProps = reactive({
      forums: ["前端开发","大数据","微服务"],
      selectForum:"",
      selectForumFun: (index: number) => {
        data.selectForum= data.forums[index];
      }
    })

    const overText = ref("太极开发者社区")

    // 钩子函数模拟
    // onBeforeMount(() => {
    //   console.log("2-组件挂载到页面之前执行-----onBeforeMount()");
    // });

    // onMounted(() => {
    //   console.log("3-组件挂载到页面之后执行-----onMounted()");
    // });
    // onBeforeUpdate(() => {
    //   console.log("4-组件更新之前-----onBeforeUpdate()");
    // });

    // onUpdated(() => {
    //   console.log("5-组件更新之后-----onUpdated()");
    // });

    // onRenderTracked((event) =>{
    //   console.log('状态跟踪钩子函数--------------->')
    //   console.log(event)
    // })

    // onRenderTriggered((event) => {
    //   console.log('状态触发钩子函数--------------->')
    //   console.log(event)
    // })

  const refData = toRefs(data)
    // const forums = ref(["前端开发","大数据","微服务"]);
    // const selectForum = ref("");
    // const selectForumFun = (index: number) => {
    //   selectForum.value = forums.value[index];
    // }
    return {
      ...refData
    }
  },
  // beforeCreate() {
  //   console.log("1-组件创建之前-----beforeCreate()");
  // },
  // beforeMount() {
  //   console.log("2-组件挂载到页面之前执行-----BeforeMount()");
  // },
  // mounted() {
  //   console.log("3-组件挂载到页面之后执行-----Mounted()");
  // },
  // beforeUpdate() {
  //   console.log("4-组件更新之前-----BeforeUpdate()");
  // },
  // updated() {
  //   console.log("5-组件更新之后-----Updated()");
  // },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
