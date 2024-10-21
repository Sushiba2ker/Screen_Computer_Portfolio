<template>
  <div>
    <div v-if="!hideHeader" class="header">
      <img
        class="header-img"
        :src="getImageSrc('certifications.png', true)"
        alt="Certifications Image"
      />
      <h3 class="header-title">{{ headerTitle }}</h3>
      <h4 class="header-subtitle">{{ headerSubtitle }}</h4>
    </div>
    <hr />

    <div class="content-grid">
      <div
        class="content"
        v-for="(certification, index) in certifications"
        :key="index"
      >
        <!-- <a class="title" :href="certification.link" target="_blank">
          {{ certification.title }}
        </a> -->
        <a :href="certification.link" target="_blank">
          <img class="img" :src="getImageSrc(certification.image)" />
        </a>
        <div class="tags">
          <!-- <button v-for="(tags, tagIndex) in certification.tags" :key="tagIndex">
            <label>{{ tags }}</label>
          </button> -->
        </div>
        <!-- <ul class="desc">
          <li>Issued on: {{ certification.issuedOn }}</li>
          <li>Provided by: {{ certification.provider }}</li>
        </ul> -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    hideHeader: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      headerTitle: "Certifications",
      headerSubtitle: "A complete lists of my certifications and achievements",
      certifications: [
        {
          title:
            "Data Engineering using AWS Data Analytics",
          link: "https://www.udemy.com/certificate/UC-dbcb1dab-2e4b-45e5-8ea9-5504c044afb8/",
          image: "AWS.jpg",
          tags: ["Data Engineering", "AWS", "Data Analytics"],
          issuedOn: "20 July 2024",
          provider: "UDEMY",
        },
        {
          title: "C++ Certification",
          link: "https://www.udemy.com/certificate/UC-5f44d8a7-5060-4f21-8ef2-4cc296cd3744/",
          image: "C++.jpg",
          tags: ["C++", "Programming"],
          issuedOn: "20 July 2024",
          provider: "UDEMY",
        },
        {
          title: "Python for beginners - Learn all the basics of python",
          link: "https://www.udemy.com/certificate/UC-b398cb0c-5ba7-494a-9004-cde73e33aad7/",
          image: "Python.jpg",
          tags: ["Machine Learning", "Python"],
          issuedOn: "23 May 2024",
          provider: "UDEMY",
        },
        {
          title: "Object Oriented Programming in C++ & Interview Preparation",
          link: "https://www.udemy.com/certificate/UC-7c31aaee-911d-4a62-8b08-700ec98f3fae/",
          image: "OOP_C++.jpg",
          tags: ["C++", "Programming"],
          issuedOn: "20 May 2024",
          provider: "UDEMY",
        }
      ],
    };
  },
  methods: {
    getImageSrc(imageName, isHeaderImage = false) {
      let imagePath;
      if (isHeaderImage) {
        imagePath = require("@/assets/icons/win95/" + imageName);
      } else {
        imagePath = require("@/assets/images/certifications/" + imageName);
      }
      return imagePath;
    },
  },
};
</script>

<style scoped>
/* Content Grid */
.content-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  margin-inline: 20px;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

/* Content */
.title {
  text-align: center;
  font-weight: bold;
  font-size: 18px;
  margin-bottom: 10px;
}

.img {
  width: 300px;
  height: 150px;
  max-width: 200px;
  background-position: center center;
  background-size: cover;
  background-repeat: no-repeat;
  padding: 5px;
  border: 4px solid white;
  background: rgb(189, 190, 189);
  border-top: solid rgb(250, 250, 250) 4px;
  border-left: solid rgb(250, 250, 250) 4px;
  border-bottom: solid rgb(90, 90, 90) 4px;
  border-right: solid rgb(90, 90, 90) 4px;
  cursor: url("@/assets/cursor/pointer.cur"), auto !important;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
  margin-top: 10px;
}

.tags button {
  display: flex;
  align-items: center;
  padding: 5px;
  padding-bottom: 2.5px;
  height: 25px;
  margin: 5px;
  width: auto;
  border: 2px solid white;
  background: rgb(189, 190, 189);
  box-shadow: 1.5px 1.5px black;
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-bottom: solid rgb(90, 90, 90) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px;
}

.tags label {
  padding-top: 2px;
  font-size: 12px;
  padding-left: 3px;
}

.desc {
  font-size: 15px;
  line-height: 1.3;
  padding: 10px 0 20px 0;
}

.desc li {
  text-align: center;
  padding: 2px;
}
</style>
