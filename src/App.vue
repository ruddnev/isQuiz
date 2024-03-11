<script>
export default {
  created() {
    window.addEventListener("resize", this.fitTo16by9);
  },
  destroyed() {
    window.removeEventListener("resize", this.fitTo16by9);
  },
  mounted() {
    this.fitTo16by9();
  },
  methods: {
    fitTo16by9(e) {
      if (window.innerWidth < 768) {return}; 

      var videoElement = document.getElementsByClassName("video")[0];
      videoElement.style.height = videoElement.clientWidth * 0.5625 + "px";
    }
  },
}


</script>

<template>
    <nav class="navbar">
      <div class="navbar__left">
        <a href="#"><img src="@/media/is.svg" alt="ITMO.STUDENTS" style="vertical-align: middle;"/></a>
      </div>
      <div class="navbar__right">
        <a href="https://vk.com/itmostudents"><img src="@/media/vk-icon.svg" alt="VK" /></a>
        <a href="https://t.me/itmoru"><img src="@/media/tg-icon.svg" alt="TG" /></a>
        <a href="https://student.itmo.ru/"><img src="@/media/www-icon.png" alt="WWW" style="filter: invert()" /></a>
      </div>
    </nav>

    <div class="video-with-quiz">
      <div class="video"><iframe src="https://www.youtube.com/embed/a2vE4aRogjI?rel=0&iv_load_policy=3&controls=0" width="560" height="315" title="A YouTube video" frameborder="0" allowfullscreen></iframe></div>
      <div class="quiz"><iframe src="https://play.myquiz.ru/p/00615924" frameborder="0" allow="autoplay; picture-in-picture"></iframe></div>
    </div>
</template>


<style>
  body {
    font-family: 'Roboto', sans-serif;
    color: white;
    background-color: #1e1e1e;
    margin: 0 10px;

  }

  .navbar {
    height: 5vh;
    max-height: 5vh;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2vh 15px 2vh 5px;

    .navbar__left img {
      width: 150px;
      height: 45px;
    }

    .navbar__right {
      a {
        margin-left: 20px;
      }

      img {
        height: 24px;
      }
    }
  }

  .video-with-quiz {
    display: flex; 
    flex-direction: row; 
    align-items: center; 
    justify-content: center; 
    height: 90vh;

    .video {
      width: 100%;
      height: 100%;
    }

    .quiz {
      min-width: 400px;
      
      height: 100%;
      border: none;
    }
  }

  iframe {
    width: 100%;
    height: 100%;
  }
  
  .container {
    max-width: 1200px;
    margin: 0 auto;
  }
  @media (max-width: 1025px) {
    body {
      margin: 0;
    }

    .navbar__left {
      margin-left: 10px
    }

    .container {
      width: 100%;
    }

    .video-with-quiz {
      flex-direction: column; 
      height: 90vh;

      .video {
        /* width: 100vw; */
        max-width: 100vw;
        height: 56.25vw !important;
      }

      .quiz {
        min-width: 100%;
        max-width: 100%;
        height: calc(100% - 56.25vw);
        border: none;
      }
    }
  }
</style>