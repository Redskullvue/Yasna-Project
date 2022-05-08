<template>
  <div>
    <div class="category">
      <div class="img-container">
        <img
          :src="src"
          style="
            border-radius: 10px;
            width: 230px;
            height: 83px;
            object-fit: cover;
            opacity: 0.7;
          "
        />
        <span class="header-title">{{ title }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "src"],
};
</script>
<style>
.category {
  display: flex;
  justify-content: center;
  cursor: pointer;
}
.img-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.header-title {
  position: absolute;
  text-align: center;
  font-size: 35px;
  color: whitesmoke;
  padding: 20px;
}
</style>
