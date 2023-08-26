<template>
  <transition name="fade">
    <div>
      <!-- banner -->
      <div class="banner-image">
          <img class="banner-image" :src="bannerImage"  width="100%" />
          <div class="banner-text-block">
              <h1 class="banner-text">Thanks for visiting!</h1>
          </div>
      </div>

      <div class="divider"></div>

      <!-- About -->
      <div class="container">
          <!-- About -->
          <div class="about-container">
              <div class="about-me">
                  <img class="avatar" :src="avatarImage" alt="Jake Young" />
                  <h2 class="name-text">Hey, I'm Jake!</h2>
                  <h3 class="typing">{{ subtitle }}</h3>
                  <h4 class="about-title">About<span class="highlight">Me</span></h4>
                  <p class="p-text">
                      Hi, I'm Jake Young! I am a third year Computer Science student based in Adelaide, Australia. I am interested in cloud technologies, development and web development. This is a website where you can view information about me.
                  </p>

                  <div class="divider"></div>
                  
                  <!-- Social Media Icons -->
                  <div class="social-media-icons">
                    <a href="https://www.facebook.com/JakeyTyler" target="_blank">
                      <i class="fab fa-facebook-f social-icon" :style="{ fontSize: '1em', margin: '0 20px' }"></i>
                    </a>
                    <a href="https://www.linkedin.com/in/jake-young-86440b11a/" target="_blank">
                      <i class="fab fa-linkedin-in social-icon" :style="{ fontSize: '1em', margin: '0 20px' }"></i>
                    </a>
                    <a href="https://github.com/JakeY92" target="_blank">
                      <i class="fab fa-github social-icon" :style="{ fontSize: '1em', margin: '0 20px' }"></i>
                    </a>
                  </div>
              </div>
          </div>
      </div>
    </div>
  </transition>
</template>

<script>
import BannerImage from '../assets/images/banner.jpg';
import AvatarImage from '../assets/images/avatar.jpg';
// import other images as necessary

export default {
  name: "HomePage",
  data() {
    return {
      bannerImage: BannerImage,
      avatarImage: AvatarImage,
      subtitle: '',
      // Subtitles to be typed and erased
      subtitles: ['Developer', 'Designer', 'Creator'],
      subtitleIndex: 0,
      eraseTimeout: 2000, // Time to wait before erasing subtitle
      typeTimeout: 100,   // Time to wait before typing next character
      erase: false,       // Are we erasing?
    };
  },

  methods: {
    typeSubtitle() {
      if (!this.erase) {
        if (this.subtitle.length < this.subtitles[this.subtitleIndex].length) {
          this.subtitle += this.subtitles[this.subtitleIndex].charAt(this.subtitle.length);
          setTimeout(this.typeSubtitle, this.typeTimeout);
        } else {
          // Start erasing after a pause
          setTimeout(() => {
            this.erase = true;
            this.typeSubtitle();
          }, this.eraseTimeout);
        }
      } else {
        if (this.subtitle.length > 0) {
          this.subtitle = this.subtitle.slice(0, -1);
          setTimeout(this.typeSubtitle, this.typeTimeout);
        } else {
          // Start typing next subtitle after erasing
          this.erase = false;
          this.subtitleIndex = (this.subtitleIndex + 1) % this.subtitles.length;
          this.typeSubtitle();
        }
      }
    },
  },
  mounted() {
    this.typeSubtitle();
  },
};
</script>

<style >

.container {
  display: grid;
  place-items: center;
  height: 0vh;
}

.about-container {
  text-align: left;
}

.about-me {
  width: 35%; 
  margin: 0 auto;
}

.about-title {
  font-size: 1.6em; 
  margin-bottom: 0; 
  text-align: left;
  font-family: 'Raleway', sans-serif; 
}

.p-text {
  text-align: left;
  margin-top: 0; 
}

h2.name-text {
  font-size: 2.5em;
  color: black;
  font-family: 'Raleway', sans-serif;
  margin-bottom: 0.1em; 
}

h3.typing {
  font-size: 1.5em;
  color: #0bceff;
  font-family: 'Raleway', sans-serif; 
  margin-top: 0.1em; 
  text-align: center;
}

h3 {
  text-align: left;
}

.highlight {
  color: #0bceff;
}

.social-links {
  display: flex;
  justify-content: start;
  gap: 20px; 
}

.social-links img {
  width: 30px; 
  height: 30px; 
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to  {
  opacity: 0;
}
.fade-leave, .fade-enter-to {
  opacity: 1;
}
</style>