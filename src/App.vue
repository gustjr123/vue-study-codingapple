<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <div class="bg-close-botten">
        <button
          @click="
            () => {
              isModalOpen = false;
            }
          "
        >
          X
        </button>
      </div>
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="i in menus" :key="i"> {{ i }} </a>
  </div>

  <div v-for="value in products" :key="value.product">
    <h4 @click="isModalOpen = true" :style="style">{{ value.product }}</h4>
    <p>{{ value.price }} 만원</p>
    <button @click="increase(value.product)">신고하기</button>
    <span>신고수 : {{ counts[value.product] }}</span>
  </div>
</template>

<script>
// 동적인 UI 만드는 법칙
// 1. UI의 현재 상태를 데이터로 저장해둠 -> isModalOpen
// 2. 데이터에 따라 UI가 어떻게보일지 작성 -> isModalOpen에 따라 보여주고 안보여주고
export default {
  name: "App",
  data() {
    return {
      isModalOpen: false,
      counts: {
        역삼동원룸: 0,
        천호동원룸: 0,
        마포구원룸: 0,
      },
      menus: ["Home", "Products", "About"],
      products: [
        { product: "역삼동원룸", price: 50 },
        { product: "천호동원룸", price: 60 },
        { product: "마포구원룸", price: 70 },
      ],
      style: "color: blue",
    };
  },
  methods: {
    increase(key) {
      this.counts[key] += 1;
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 100;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  position: fixed;
  padding: 20px;
  background: rgba(0, 0, 0, 0.5);
}
.white-bg {
  width: 60%;
  background: white;
  padding: 20px;
  border-radius: 8px;
  margin: auto;
}
.bg-close-botten {
  width: fit-content;
  margin-left: 95%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
