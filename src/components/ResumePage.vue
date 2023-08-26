<!-- Template with fade transition, resume information to fill into the cards/columns -->
<template>
    <transition name="fade">
    <div class="resume-page">
      <div class="column-wrapper">
        <ResumeColumn title="Work Experience." :items="workExperience" />
        <ResumeColumn title="Education." :items="education" />
      </div>
      <div class="button-wrapper">
        <a href="../assets/JakeYoung_resume.pdf" download class="download-button">Download Resume</a>
      </div>
    </div>
</transition>
  </template>
  
  <script>
  import ResumeColumn from './ResumeColumn.vue';
  
  export default {
    components: {
      ResumeColumn
    },
    data() {
      return {
      workExperience: [
  {
    year: 'December 2022 - Present',
    title: 'TELECOMMUNICATIONS DESIGNER',
    company: 'GENUS SERVICES PTY LTD',
    description: [
      'Designing complex end-to-end projects utilizing software such as AutoCAD',
      'Working on multiple projects simultaneously, ensuring timely delivery and client satisfaction',
      'Collaborating with multidisciplinary teams to achieve project goals',
    ],
  },
  {
    year: 'September 2022 – December 2022',
    title: 'SERVICE DESK AGENT',
    company: 'Datacom, Modbury, Adelaide',
    description: [
      'Resolved IT-related service desk requests efficiently and effectively',
      'Provided exceptional customer service experience to Medibank employees',
      'Utilized Citrix, remote desktops, and various Medibank-related applications',
      'Managed ticketing systems, problem-solving, and phone calls concurrently',
    ],
  },
  {
    year: 'September 2016 - June 2021',
    title: 'FIXED NETWORK DESIGN (WIDEBAND)',
    company: 'Ventia Pty Ltd, North Plympton, Adelaide',
    description: [
      'Created comprehensive internal & external optical fibre network designs for businesses',
      'Exceled in working quickly and logically in high-pressure environments',
      'Mastered a wide variety of computer software and databases',
      'Developed strong problem-solving and interpersonal skills',
      'Gained experience in CAD, Microsoft Office, and Visio',
    ],
  },
  {
    year: 'June 2014 - June 2016',
    title: 'TELECOMMUNICATIONS TECHNICIAN',
    company: 'Telstra (Traineeship), Netley, Adelaide',
    description: [
      'Conducted optical fibre splicing and joint making',
      'Handled HFC cable faults and construction',
      'Managed copper cable jointing and faults',
      'Practiced manual handling and safe working techniques',
      'Delivered excellent customer service and resolved customer complaints',
    ],
  },
],
education: [
  {
    year: 'June 2021 - Present',
    title: 'Bachelor of Computer Science',
    company: 'DEAKIN UNIVERSITY, Melbourne, Victoria',
    description: [],
  },
  {
    year: 'June 2014 – June 2016',
    title: 'Certificate III in Telecommunications',
    company: 'RAMSDEN TELECOMMUNICATIONS TRAINING',
    description: [],
  },
  {
    year: 'January 2011 - November 2011',
    title: 'South Australian Certificate of Education',
    company: 'ST COLUMBA COLLEGE, Adelaide, South Australia',
    description: [],
          },
        ],
      };
    },
  }
  
  </script>
  
  <style>

.resume-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start; 
  padding-top: 1px; 
}

.column-wrapper {
  display: flex;
  justify-content: space-around;
  width: 80%;
  margin: auto;
  padding: 20px;
}

.resume-item {
  transition: background-color 0.5s ease;
}

.resume-item:hover {
  background-color: #0bceff;
  color: #fff;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: 'Raleway', sans-serif;
}

.title {
  font-family: 'Raleway', sans-serif;
}

.button-wrapper {
  display: flex;
  justify-content: center;
  width: 100%;
  padding: 20px;
}

.download-button {
  display: inline-block;
  background-color: #0bceff;
  color: white;
  padding: 10px 20px;
  text-decoration: none;
  font-weight: bold;
  border-radius: 50px;
  transition: background-color 0.3s ease, transform 0.3s ease;
  font-size: 1.2rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.download-button:hover {
  background-color: #09b8da;
  transform: scale(1.05);
}

/* Media queries for responsiveness */

/* For screens with a maximum width of 768px */
@media (max-width: 768px) {
  .column-wrapper {
    flex-direction: column;
    width: 90%;
    padding: 10px;
  }

  .resume-item {
    margin-bottom: 20px;
  }

  .button-wrapper {
    padding: 10px;
  }
}

/* For screens with a maximum width of 480px */
@media (max-width: 480px) {
  .column-wrapper {
    width: 100%;
  }

  .download-button {
    font-size: 1rem;
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
}
</style>