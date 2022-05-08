<template>
  <div class="main-box">
    <header>
      <span class="image-title"> {{ mainTitle }} </span>
      <img class="image-container" :src="imageSrc" alt="" />
    </header>
    <main>
      <div class="main-info">
        <div class="main-title">
          <h4>{{ mainTitle }}</h4>
        </div>
        <div class="main-des">{{ description }}</div>
      </div>
    </main>
    <footer>
      <div class="footer">
        <div class="footer-profile">
          <img :src="imageSrc" alt="image" class="profile-image" />
          <h5 class="footer-name">شایان افراسیابی</h5>
          <h6 class="profile-date">{{ dateInfo(dateData) }}</h6>
        </div>
        <div>
          <span class="footer-comment"
            ><i class="fa fa-comments"></i><span> ۵دیدگاه</span></span
          >
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "infoBox",
  props: ["mainTitle", "description", "imageSrc", "dateData"],
  methods: {
    dateInfo(date) {
      let today = new Date(date).toLocaleDateString("fa-IR");
      // console.log(today);
      return `${today}`;
    },
  },
};
</script>

<style>
.profile-image {
  border-radius: 100%;
  width: 25px;
  height: 25px;
}
.main-des {
  color: #5a5858;
  margin-top: 5px;
  padding: 0px 5px;
}
.main-title {
  padding: 0px 5px;
}
.image-container {
  width: 505px;
  height: 330px;
  padding-top: 5px;
  border-top-right-radius: 12px;
  border-top-left-radius: 12px;
  /* object-fit: fill; */
  object-fit: cover;
}
.main-box {
  display: grid;
  grid-template-rows: 330px 150px 100px;
  grid-gap: 20px;
  margin: 15px;
  margin-bottom: 40px;
}
.image-title {
  background-color: whitesmoke;
  margin-top: 20px;
  margin-right: 15px;
  position: absolute;
  border-radius: 2px;
  padding: 10px;
  text-align: center;
  border-radius: 5px;
}
.main-info {
  grid-row: 2/3;
  background-color: #fff;
  padding: 20px 10px;
  color: darkgray;
}
.fa-comments {
  font-size: 15px;
  margin-bottom: 20px;
}
.footer-comment {
  cursor: pointer;
}
.footer {
  grid-row: 3/4;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: end;
  padding: 10px;
  margin-top: 5px;
  margin-left: 10px;
  color: #5a5858;
}
.footer-profile {
  display: grid;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: 30px 30px;
  margin-top: 30px;
}
.profile-image {
  grid-row: 1/3;
  width: 48px;
  height: 48px;
  border-radius: 100%;
  justify-self: end;
  margin: 5px;
  object-fit: cover;
}
.profile-date {
  grid-row: 2/3;
  grid-column: 2/3;
  align-self: end;
  font-size: 14px;
  align-self: start;
  padding: 5px;
}
.footer-name {
  align-self: end;
  font-size: 14px;
}
</style>
