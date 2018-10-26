<template>
  <div id="app"  @click="clickTips">

    <img src="./assets/logo.png">
    <router-view/>

  </div>
</template>

<script>
  const arr = [
    "黑儿子",
    "民主",
    "文明",
    "和谐",
    "自由",
    "平等",
    "公正",
    "法治",
    "爱国",
    "敬业",
    "诚信",
    "友善"
  ];
  const setStyle = (obj, json) => {
    for (var i in json) {
      obj.style[i] = json[i];
      console.log(i);
      // console.log(json[i]);
    }
  };
  let index = 0 ;
  export default {
    name: 'App',
    methods:{
      // Event事件
      clickTips: function(event) {
        if (index >= arr.length) {
          index = 0;
        }
        // console.log(window);
        // console.log(event);
        let newA = document.createElement("a");
        newA.className = "click_tips";
        let styles = {
          //es6 模板语法
          left: `${event.pageX}px`,
          top: `${event.pageY - 20}px`
        };
        newA.innerHTML = arr[index];
        setStyle(newA, styles);
        document.getElementById("app").appendChild(newA);
        index++;
        // animationend 事件在 CSS 动画完成后触发。
        newA.addEventListener("animationend", () => {
          document.getElementById("app").removeChild(newA);
        });
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .click_tips {
    color: red;
    position: absolute;
    transition: all 0.3s;
    animation: click_translateTop 1s;
  }
  @keyframes click_translateTop {
    0%,
    100% {
      opacity: 0;
    }
    10% {
      opacity: 1;
    }
    100% {
      transform: translateY(-30px);
    }
  }

</style>
