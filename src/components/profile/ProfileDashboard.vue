<template>
  <div class="profile-dashboard">
    <div class="dashboard-container">
      <div class="inner-block">
        <header class="profile-header">
          <div class="logo">AKASH K B</div>
          <nav class="navigation">
            <span :class="{ active: tab === 'projects' }" @click="scroll('projects')">Projects</span>
            <span :class="{ active: tab === 'about' }" @click="scroll('skills')">Skills</span>
            <span :class="{ active: tab === 'contact' }" @click="scroll('contacts')">Contact</span>
          </nav>
          <div class="socials">
            <a href="https://github.com/akashkb45" target="_blank" aria-label="GitHub">
              <i class="fab fa-github"></i>
            </a>
            <a href="https://www.linkedin.com/in/akash-k-b-744169283?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app" target="_blank" aria-label="LinkedIn">
              <i class="fab fa-linkedin-in"></i>
            </a>
            <a href="https://www.instagram.com/_ak_a__sh_?igsh=cHBieDd2bXY4amsx" target="_blank" aria-label="Instagram">
              <i class="fab fa-instagram"></i>
            </a>
            <a href="https://x.com/akashkb_45?t=GF4AhK6-gYOlN4T4g0JdZQ&s=09" target="_blank" aria-label="Twitter">
              <i class="fab fa-x-twitter"></i>
            </a>
            <a href="https://www.facebook.com/akash.aachi.1" target="_blank" aria-label="Facebook">
              <i class="fab fa-facebook"></i>
            </a>
          </div>
        </header>

        <div class="profile-content">
          <h1>
            My name is Akash K B, <br />
            I work as a Front-end Developer
          </h1>

          <p>I build modern, responsive, and user-friendly websites with a focus on clean design and efficient code.</p>
        </div>

        <TechnicalSkills ref="skills"></TechnicalSkills>

        <FeaturedProjects ref="projects"></FeaturedProjects>

        <ContactSection ref="contacts"></ContactSection>

        <!-- <div class="project-container">
          <div class="project-header">
            <h4>MY PROJECTS</h4>
          </div>

          <div class="project-content">
            <div class="project-card" v-for="(project, index) in 5" :key="index">
              <h1>Choclate Cake</h1>
            </div>
          </div>
        </div> -->
      </div>
    </div>
  </div>
</template>

<script>
import ContactSection from "../ContactSection.vue";
import FeaturedProjects from "../FeaturedProjects.vue";
import TechnicalSkills from "../TechnicalSkills.vue";

export default {
  name: "ProfileDashboard",
  components: { TechnicalSkills, FeaturedProjects, ContactSection },
  data() {
    return {
      tab: "",
    };
  },
  methods: {
    scroll(sectionName) {
      const sectionComponent = this.$refs[sectionName];
      const domElement = sectionComponent?.$el || sectionComponent;

      if (domElement && domElement.scrollIntoView) {
        domElement.scrollIntoView({ behavior: "smooth" });
      } else {
        console.warn("DOM element not found for:", sectionName);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
html {
  scroll-behavior: smooth;
}

section {
  scroll-margin-top: 80px; /* match navbar height if fixed */
}
.profile-dashboard {
  .dashboard-container {
    padding: 50px;
    .inner-block {
      display: flex;
      flex-direction: column;
      row-gap: 40px;
      .profile-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        .logo {
          font-size: 2rem;
          font-weight: 700;
          color: #ffffff;
        }
        .navigation {
          display: flex;
          justify-content: center;
          gap: 20px;
          span {
            margin: 0 15px;
            font-size: 1.2rem;
            // font-weight: 600;
            cursor: pointer;
            text-align: center;
            position: relative;
            padding-bottom: 5px;
            &::after {
              content: "";
              position: absolute;
              width: 0;
              height: 2px;
              bottom: 0;
              left: 0;
              background: #00f9ff;
              transition: width 0.3s ease;
            }
            &:hover::after {
              width: 100%;
            }
            &:hover {
              color: #00f9ff;
            }
          }
          .selected {
            color: #00f9ff;

            &::after {
              content: "";
              position: absolute;
              width: 0;
              height: 2px;
              bottom: 0;
              left: 0;
              background: #00f9ff;
              transition: width 0.3s ease;
              width: 100%;
            }
          }
        }

        .socials {
          display: flex;
          gap: 15px;

          a {
            color: #ffffff;
            font-size: 1.2rem;
            transition: color 0.3s;

            &:hover {
              color: #00f9ff;
            }
          }
        }
        .profile-pages {
          display: flex;
          gap: 25px;
          i {
            font-size: 1.4rem;
            margin: 0 5px;
            cursor: pointer;
            &:hover {
              color: #00f9ff;
            }
          }
        }
      }

      .profile-content {
        margin: 30px 0;
        height: 400px;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        h1 {
          font-size: 4rem;
          text-align: center;
          color: #fff;
          animation: fadeInSlideUp 2s ease-out;
        }
        p {
          margin: 0;
          font-size: 1.8rem;
          animation: fadeInSlideUp 3s ease-out;
        }
        @keyframes fadeInSlideUp {
          0% {
            opacity: 0;
            transform: translateY(20px); /* Starts 20px below */
          }
          100% {
            opacity: 1;
            transform: translateY(0); /* Ends at the original position */
          }
        }
      }
      .project-container {
        .project-header {
          width: 100%;
          position: relative;
          h4 {
            font-size: 2.5rem;
            padding: 15px 0;
            color: #00f9ff;
            &::after {
              content: "";
              position: absolute;
              width: 0;
              height: 2px;
              bottom: 0;
              left: 0;
              background: #00f9ff;
              animation: slideInBorder 1s ease forwards;
              width: 100%;
            }
          }
        }

        .project-content {
          display: flex;
          gap: 15px;
          .project-card {
            padding: 10px;
            // background: #fff;
            background-color: rgba(0, 0, 0, 0.229);
            background-image: url("../../assets/images/chocolate_fog.jpg");
            background-blend-mode: overlay;

            background-size: contain;
            width: 300px;
            border-radius: 20px;
            height: 460px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            filter: grayscale(100%);
            h1 {
              text-transform: uppercase;
              font-size: 2rem;
            }

            &:hover {
              transform: scale(1.1);
              transition: 0.5s ease-in-out;
              background-color: rgba(0, 0, 0, 0.7);
              filter: grayscale(0%);
            }
            // box-shadow: 0 4px 10px rgba(255, 255, 255, 0.1), 0 6px 15px rgba(50, 50, 50, 0.2);
          }
        }

        @keyframes slideInBorder {
          0% {
            width: 0; /* Start with no border */
          }
          100% {
            width: 100%; /* Ends with full-width border */
          }
        }
      }
    }
  }
}
</style>
