<!-- Template with fade transition, Project name and descriptions, self typing/erasing subtitle -->
<template>
  <transition name="fade">
    <div class="container">
      <h3 class="typing">{{ subtitle }}</h3>
      <div class="divider"></div>
      <table class="table" v-if="!erase || showTable">
        <tr>
          <th>Project Name</th>
          <th>Description</th>
        </tr>
        <tr v-for="project in projects" :key="project.name">
          <td><a :href="project.link" target="_blank" class="project-link">{{ project.name }}</a></td>
          <td>{{ project.description }}</td>
        </tr>
      </table>
    </div>
  </transition>
</template>

<script>

export default {
  name: "ProjectsPage",
  data() {
    return {

      subtitle: '',
      subtitles: ['Projects.'],
      subtitleIndex: 0,
      eraseTimeout: 99999,
      typeTimeout: 100,
      erase: false,

      projects: [
      { 
          name: "Bank System", 
          description: "Standard bank transaction in C#", 
          link: "https://github.com/"
        },
        { 
          name: "Lost in Space", 
          description: "Space game developed in C++", 
          link: "https://github.com/JakeY92/Space-game"
        },
        { 
          name: "Dev@Deakin", 
          description: "Website developed using React", 
          link: "https://github.com/JakeY92/SIT-313-Deakin-Web-App"
        },
        
      ],

      eraseTimeoutId: null,
      typeTimeoutId: null,
    };
  },

  methods: {
    typeSubtitle() {
      this.typeInterval = setInterval(() => {
        if (!this.erase) {
          if (this.subtitle.length < this.subtitles[this.subtitleIndex].length) {
            this.subtitle += this.subtitles[this.subtitleIndex].charAt(this.subtitle.length);
          } else {
            clearInterval(this.typeInterval);
            this.eraseInterval = setTimeout(() => {
              this.erase = true;
              this.typeSubtitle();
            }, this.eraseTimeout);
          }
        } else {
          if (this.subtitle.length > 0) {
            this.subtitle = this.subtitle.slice(0, -1);
          } else {
            clearInterval(this.typeInterval);
            this.erase = false;
            this.showTable = true;
            this.subtitleIndex = (this.subtitleIndex + 1) % this.subtitles.length;
            this.typeSubtitle();
          }
        }
      }, this.typeTimeout);
    },
  },
  mounted() {
    this.typeSubtitle();
  },
  beforeUnmount() {
    // This method gets executed right before the component gets destroyed
    // Clear the interval and timeout to prevent memory leaks
    if (this.typeInterval) {
      clearInterval(this.typeInterval);
    }
    if (this.eraseInterval) {
      clearTimeout(this.eraseInterval);
    }
    },
};
</script>

<style >
.project-link {
  color: #0bceff;
  text-decoration: none;
  font-weight: bold;
  transition: color 0.3s ease;
}

.project-link:hover {
  color: #099abc;
}

table {
  width: 100%;
}
th, td {
  padding: 15px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

h3.typing {
  font-size: 2em;
  color: #0bceff;
  font-family: 'Raleway', sans-serif;
  margin-top: 0.0em;
  text-align: center;
}

h3 {
  text-align: left;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.fade-leave, .fade-enter-to {
  opacity: 1;
}
</style>
