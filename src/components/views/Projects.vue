<template>
  <div>
    <div v-if="!hideHeader" class="header">
      <img
        class="header-img"
        :src="getImageSrc('projects.png', true)"
        alt="Projects Image"
      />
      <h3 class="header-title">{{ headerTitle }}</h3>
      <h4 class="header-subtitle" v-html="headerSubtitle"></h4>
    </div>
    <hr />

    <div class="tabs">
      <div
        class="tab"
        :class="{ 'active-tab': activeTab === 'data-analysis' }"
        @click="setActiveTab('data-analysis')"
      >
        Data & ML
      </div>
      <div
        class="tab"
        :class="{ 'active-tab': activeTab === 'web-dev' }"
        @click="setActiveTab('web-dev')"
      >
        Web Development
      </div>
      <div
        class="tab"
        :class="{ 'active-tab': activeTab === 'others' }"
        @click="setActiveTab('others')"
      >
        Others
      </div>
    </div>

    <div v-if="activeTab === 'featured'" class="content">
      <div v-for="(featured, index) in featureds" :key="index">
        <a class="title">
          {{ featured.title }}
        </a>
        <img :src="featured.imgSrc" class="img" />
        <div class="tags">
          <button v-for="(tags, tagIndex) in featured.tags" :key="tagIndex">
            <label>{{ tags }}</label>
          </button>
        </div>
        <p class="desc">{{ featured.desc }}</p>
        <div class="link">
          <button v-if="featured.showSite" @click="redirect(featured.siteLink)">
            <img src="@/assets/icons/win95/search.png" />
            <label>Site</label>
          </button>
          <button
            v-if="featured.showDocumentation"
            @click="openWindow(featured.windowId)"
          >
            <img src="@/assets/icons/win95/directory.png" />
            <label>Documentation</label>
          </button>
          <button @click="redirect(featured.githubLink)">
            <img src="@/assets/icons/social/github.png" />
            <label>GitHub</label>
          </button>
        </div>
        <hr />
      </div>
    </div>

    <div v-if="activeTab === 'data-analysis'" class="content">
      <div v-for="(data, index) in datas" :key="index">
        <a class="title">
          {{ data.title }}
        </a>
        <img :src="data.imgSrc" class="img" />
        <div class="tags">
          <button v-for="(tags, tagIndex) in data.tags" :key="tagIndex">
            <label>{{ tags }}</label>
          </button>
        </div>
        <p class="desc">{{ data.desc }}</p>
        <div class="link">
          <button v-if="data.showSite" @click="redirect(data.siteLink)">
            <img src="@/assets/icons/win95/search.png" />
            <label>Site</label>
          </button>
          <button
            v-if="data.showDocumentation"
            @click="openWindow(data.windowId)"
          >
            <img src="@/assets/icons/win95/directory.png" />
            <label>Documentation</label>
          </button>
          <button v-if="data.showGitHub" @click="redirect(data.githubLink)">
            <img src="@/assets/icons/social/github.png" />
            <label>GitHub</label>
          </button>
        </div>
        <hr />
      </div>
    </div>

    <div v-if="activeTab === 'web-dev'" class="content">
      <div v-for="(webdev, index) in webdevs" :key="index">
        <a class="title">
          {{ webdev.title }}
        </a>
        <img :src="webdev.imgSrc" class="img" />
        <div class="tags">
          <button v-for="(tags, tagIndex) in webdev.tags" :key="tagIndex">
            <label>{{ tags }}</label>
          </button>
        </div>
        <p class="desc">{{ webdev.desc }}</p>
        <div class="link">
          <button v-if="webdev.showSite" @click="redirect(webdev.siteLink)">
            <img src="@/assets/icons/win95/search.png" />
            <label>Site</label>
          </button>
          <button v-if="webdev.showGitHub" @click="redirect(webdev.githubLink)">
            <img src="@/assets/icons/social/github.png" />
            <label>GitHub</label>
          </button>
        </div>
        <hr />
      </div>
    </div>

    <div v-if="activeTab === 'others'" class="content">
      <div v-for="(other, index) in others" :key="index">
        <a class="title">
          {{ other.title }}
        </a>
        <img :src="other.imgSrc" class="img" />
        <div class="tags">
          <button v-for="(tags, tagIndex) in other.tags" :key="tagIndex">
            <label>{{ tags }}</label>
          </button>
        </div>
        <p class="desc">{{ other.desc }}</p>
        <div class="link">
          <button @click="redirect(other.githubLink)">
            <img src="@/assets/icons/social/github.png" />
            <label>GitHub</label>
          </button>
        </div>
        <hr />
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
      headerTitle: "Projects",
      headerSubtitle:
        'A complete lists of my projects. You can also see it in <a href="https://github.com/Sushiba2ker">GitHub</a>',
      activeTab: "datas",
      datas: [
        {
          title: "Stock Price Prediction using GRU",
          imgSrc: this.getImageSrc("predict.png"),
          tags: ["Python", "Machine Learning"],
          desc: "Predicting stock prices using GRU.",
          siteLink: "https://www.kaggle.com/code/sushiba/stock-price-prediction-using-gru",
          showSite: true,
        },
        {
          title: "🕷️Detection Malware Using Machine Learning Models",
          windowId: "",
          imgSrc: this.getImageSrc("detection.png"),
          tags: ["Machine Learning", "Python"],
          desc: "Developed a Python-based machine learning model to classify hand gesture images as rock, paper, or scissors.",
          siteLink: "https://www.kaggle.com/code/sushiba/detection-malware-using-machine-learning",
          showSite: true,
        },
      ],
      webdevs: [
        {
          title: "420Share",
          imgSrc: this.getImageSrc("detection.png"),
          tags: ["React", "Webtorrent"],
          desc: "A simple file sharing website using React and WebTorrent.",
          githubLink: "https://github.com/Sushiba2ker/420Share",
          siteLink: "https://four20share.onrender.com/",
          showSite: true,
          showGitHub: true,
        },
      ],
      others: [

      ],
    };
  },
  methods: {
    setActiveTab(tab) {
      this.activeTab = tab;
    },
    openWindow(windowId) {
      const payload = {
        windowState: "open",
        windowID: windowId,
      };
      this.$store.commit("setWindowState", payload);
    },
    getImageSrc(imageName, isHeaderImage = false) {
      let imagePath;
      if (isHeaderImage) {
        imagePath = require("@/assets/icons/win95/" + imageName);
      } else {
        imagePath = require("@/assets/images/projects/" + imageName);
      }
      return imagePath;
    },
    redirect(githubLink) {
      window.open(githubLink, "_blank");
    },
  },
};
</script>

<style scoped>
/* Content */
.content {
  border-top: solid rgb(250, 250, 250) 3px;
  border-left: solid rgb(250, 250, 250) 3px;
  border-bottom: solid rgb(90, 90, 90) 3px;
  border-right: solid rgb(90, 90, 90) 3px;
  padding: 10px;
  margin-top: -3px;
  position: relative;
  z-index: 1;
  overflow: overlay;
}

.title {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  text-decoration: none;
  color: inherit;
  font-weight: bold;
  font-size: 16px;
  margin-top: 30px;
}

.img {
  display: flex;
  width: 320px;
  height: 180px;
  flex-direction: column;
  align-items: center;
  margin-left: auto;
  margin-right: auto;
  margin-top: 20px;
  margin-bottom: 10px;
  padding: 5px;
  border: 4px solid white;
  background: rgb(189, 190, 189);
  border-top: solid rgb(250, 250, 250) 4px;
  border-left: solid rgb(250, 250, 250) 4px;
  border-bottom: solid rgb(90, 90, 90) 4px;
  border-right: solid rgb(90, 90, 90) 4px;
}

iframe {
  display: flex;
  align-items: center;
  margin-left: auto;
  margin-right: auto;
  width: 80%;
  height: 300px;
  margin-top: 20px;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
  margin-bottom: 20px;
}

.tags button {
  display: flex;
  align-items: center;
  padding: 5px;
  padding-bottom: 2.5px;
  height: 25px;
  margin: 10px 5px 2px 5px;
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
  text-align: center;
  margin: 15px 0 0 0;
}

.link {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
}

.link button {
  display: flex;
  align-items: center;
  padding: 5px;
  padding-bottom: 2.5px;
  height: 30px;
  margin: 10px 5px 30px 5px;
  width: auto;
  border: 2px solid white;
  background: rgb(189, 190, 189);
  box-shadow: 1.5px 1.5px black;
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-bottom: solid rgb(90, 90, 90) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px;
  cursor: url("@/assets/cursor/pointer.cur"), auto !important;
}

.link img {
  height: 22px;
  padding-bottom: 2px;
  cursor: url("@/assets/cursor/pointer.cur"), auto !important;
}

.link label {
  padding-top: 2px;
  padding-left: 5px;
  font-size: 13px;
  cursor: url("@/assets/cursor/pointer.cur"), auto !important;
}

.link button:hover {
  background-color: darkgray;
}

/* Media query */
@media screen and (max-width: 1024px) {
  /* Content */
  .content {
    border-top: solid rgb(250, 250, 250) 2px;
    border-left: solid rgb(250, 250, 250) 2px;
    border-bottom: solid rgb(90, 90, 90) 2px;
    border-right: solid rgb(90, 90, 90) 2px;
    padding: 10px;
    margin-top: -2px;
    position: relative;
    z-index: 1;
  }

  .desc {
    margin-top: 20px;
    padding: 5px;
  }

  iframe {
    height: 200px;
  }
}
</style>
