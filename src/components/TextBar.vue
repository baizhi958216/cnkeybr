<template>
  <div class="cn">
    <div class="cna" v-for="(a, index) in taList" :key="index">
      <span>
        {{ a.pn }}
      </span>
      <span>
        {{ a.val }}
      </span>
    </div>
  </div>
  <input
    type="text"
    style="
      border: none;
      outline: none;
      height: 40px;
      font-size: 40px;
      font-family: 'misans';
      width: 1000px;
      margin: 0 auto;
    "
    autoFocus
    v-model="ivalue"
    maxlength="10"
  />
</template>

<script setup lang="ts">
import { ref, toRaw } from "vue";
import { pinyin } from "pinyin-pro";

const keyList = "qwertyuiopasdfghjklzxcvbnm ".split("");

const tex =
  "一般来说想到这里我的心在流血我的穿山甲到底说了什么在一定程度上会影响了周围\
穿山甲到底说了什么因何而发生就我个人来说穿山甲到底说了什么对我的意义不能不说非常重大\
黑格尔说过一句著名的话只有永远躺在泥坑里的人才不会再掉进坑里这句话语虽然很短但令我浮想联翩\
这里留给我了很多成长的脚印留给我了很多感动的画面留给我了很多悔恨的泪水更留给我了很多从做人到做事的经验和教训\
斯宾诺莎曾经提到过最大的骄傲于最大的自卑都表示心灵的最软弱无力这启发了我\
爱迪生在不经意间这样说过失败也是我需要的它和成功对我一样有价值\
这句话把我们带到了一个新的维度去思考这个问题问题的关键究竟为何\
所谓穿山甲到底说了什么关键是穿山甲到底说了什么需要如何写\
迈克尔F斯特利说过一句富有哲理的话最具挑战性的挑战莫过于提升自我\
这句话看似简单但其中的阴郁不禁让人深思普列姆昌德说过一句富有哲理的话\
希望的灯一旦熄灭生活刹那间变成了一片黑暗这句话看似简单但其中的阴郁不禁让人深思\
不知世间的人是否与我一样有这种恍惚的感觉经过上述讨论这里留给我了很多成长的脚印\
留给我了很多感动的画面留给我了很多悔恨的泪水更留给我了很多从做人到做事的经验和教训\
可是即使是这样穿山甲到底说了什么的出现仍然代表了一定的意义穿山甲到底说了什么\
到底应该如何实现带着这些问题我们来审视一下穿山甲到底说了什么就我个人来说\
穿山甲到底说了什么对我的意义不能不说非常重大奥普拉温弗瑞在不经意间这样说过你相信什么\
你就成为什么样的人这启发了我穿山甲到底说了什么到底应该如何实现关于这次穿山甲到底说了什么的原因\
显然是有主观态度上的行为反映出我观念不够先进因此我们不能奢求人生不能抱怨生活\
相反我们要以感恩的心态来对待这并不算漫长的人生了解清楚穿山甲到底说了什么到底是一种怎么样的存在\
是解决一切问题的关键在这种困难的抉择下本人思来想去寝食难安穿山甲到底说了什么到底应该如何实现\
在这个以和谐为主题的社会里人与人就应该和谐相处和谐发展易卜生曾经说过伟大的事业需要决心能力\
组织和责任感这似乎解答了我的疑惑那么所谓穿山甲到底说了什么关键是穿山甲到底说了什么需要如何写\
我从思想上没有把穿山甲到底说了什么的方式方法重视起来穿山甲到底说了什么因何而发生我们一般认为\
抓住了问题的关键其他一切则会迎刃而解这条路很长有时候走着走着不经意发现自己迷了路\
每个人都是独立的个体有属于自我发展的空间和方向穿山甲到底说了什么发生了会如何不发生又会如何\
要反思穿山甲到底说了什么行为此时此刻我对自己的内心进行了很多的思考种下什么样的因就会得出什么样的果\
如果认真一些就能得到好结果在这种困难的抉择下本人思来想去寝食难安种下什么样的因就会得出什么样的果\
如果认真一些就能得到好结果我的穿山甲到底说了什么在一定程度上会影响了周围因此我们不能奢求人生\
不能抱怨生活相反我们要以感恩的心态来对待这并不算漫长的人生这条路很长有时候走着走着不经意发现自己迷了路\
每个人都是独立的个体有属于自我发展的空间和方向我的穿山甲到底说了什么在一定程度上会影响了周围希腊曾经提到过\
最困难的事情就是认识自己这不禁令我深思文森特皮尔说过一句富有哲理的话改变你的想法你就改变了自己的世界";

const listv = ref<string[]>();

const listn = ref<string[]>();

const ivalue = ref<string[]>();

const taList = ref<{ pn: string; val: string }[]>([]);

const splittex = () => {
  const texarr = tex.split("");
  return texarr[Math.floor(Math.random() * texarr.length)];
};
const getList = () => {
  let list: string[] = [];
  for (let i = 0; i <= 9; i++) {
    list.push(splittex());
  }
  listv.value = list;
  listn.value = pinyin(list.toString(), { type: "array" })
    .toString()
    .split(",,,");

  listv.value.forEach(async (element, index) => {
    taList.value!.push({
      pn: listn.value![index],
      val: element,
    });
  });
};
getList();

document.addEventListener("keyup", (e: KeyboardEvent) => {
  if (ivalue.value?.length === listv.value?.length) {
    const inv = toRaw(ivalue.value)?.toString();
    const origin = toRaw(listv.value)?.toString();
    if (inv?.split("").toString() === origin?.split(",").toString()) {
      getList();
      ivalue.value = [];
    }
  }
});
</script>

<style scoped>
.cn {
  display: flex;
  justify-content: center;
}
.cna {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  margin: 15px;
  font-family: "misans";
}
</style>
