<template>
  <div id="app" dir="rtl">
    <div
      class="list-header"
      style="font-size: 28px; color: #4e4e4e; position: absolute"
    >
      دسته بندی ها
    </div>
    <div v-for="header in headeRes" :key="header.id">
      <Category
        class="grid-item"
        :title="header.title"
        src="https://tarkhineh-api.yasna.live/files/1643730124_6EsZ1Ds8jWmaawPj93YzAyXaZLLLAsOtKgaNqsSv_compress.png"
      />
    </div>
    <div v-for="api in apires" :key="api.id" class="box" :class="api.id">
      <Info-box
        :mainTitle="api.title"
        :description="api.synopsis"
        :imageSrc="api.image.link"
        :dateData="api.published_at"
      />
    </div>
  </div>
</template>

<script>
import Category from "./components/category.vue";
import InfoBox from "./components/infobox.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Category,
    InfoBox,
  },
  data() {
    return {
      apires: "",
      headeRes: "",
    };
  },
  created() {
    axios({
      method: "get",
      url: "http://localhost:8080/api/modular/v1/tagging-labels?slug=blog-category&including[]=image&including[]=title&including[]=slug",
      params: {
        limit: "6",
      },
    })
      .then((res) => (this.headeRes = res.data.results))
      .catch((err) => console.log(err));
    axios({
      method: "get",
      url: "http://localhost:8080/api/modular/v1/content-post-lists?type=blog&including[]=id&including[]=title&including[]=image&including[]=synopsis&including[]=published_at&including[]=tagging_labels:tags&including[]=url_encode&including[]=slug&limit=10&locale=fa",
      params: {
        limit: "8",
      },
    })
      .then((res) => (this.apires = res.data.results))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
@font-face {
  font-family: yekan;
  src: url("./assets/fonts/Yekan.ttf");
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: yekan;
  line-height: none;
}

#app {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: 150px repeat(3, 670px);
  grid-gap: 20px;
  padding: 100px;
  background-color: rgb(253, 253, 253);
}
.grid-item {
  grid-row: 1/2;
  margin-top: 50px;
}
.box {
  background-color: #fff;
  display: grid;
  grid-template-rows: repeat(2, 200px) 70px;
  grid-template-columns: 1fr;
  border-radius: 15px;
  margin: 5px 0px;
  box-shadow: 0px 1px 0px 0px lightgray;
  line-height: 1.4;
}
/* positioning information boxes  with their api ids*/
.YwjxK {
  grid-column: 1/3;
  grid-row: 2/3;
}
.jkamk {
  grid-column: 3/5;
  grid-row: 2/3;
}
.VLgjk {
  grid-column: 5/7;
  grid-row: 2/3;
}
.vKyBY {
  grid-column: 1/3;
  grid-row: 3/4;
}
.oLexk {
  grid-column: 3/5;
  grid-row: 3/4;
}
.lKoNL {
  grid-column: 5/7;
  grid-row: 3/4;
}
.vYQEY {
  grid-column: 1/3;
  grid-row: 4/5;
}
.xYVRY {
  grid-column: 3/5;
  grid-row: 4/5;
}
.wKjqL {
  grid-column: 5/7;
  grid-row: 4/5;
}
.ALvzL {
  grid-column: 1/3;
}
</style>
