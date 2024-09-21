<template>
  <div class="page">
    <h1>About Me</h1>
    <vs-row>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
        <p class="intro">
          <span>
            I am a full stack web developer who is eager to contribute to
            team success through hard work, attention to detail and excellent
            communication skills.<br /><br />I am a detail oriented person and
            I keep my goals and tasks organized to maintain productivity.<br /><br />
            I would bring to table a wide range of software skills, ranging from design 
            and development to writing scripts for intelligent agents. I believe that the skills 
            that I have attained from the dynamic environment and competitive university life define me, <br /><br />
            I am looking forward to implementing and polishing them in any opportunity that I receive.<br />
          </span>
          <br />
          <span class="signature">
            Have a great {{ getDayOfWeek() }}
            <!-- <i>- Armin Varshokar</i> -->
          </span>
        </p>
      </vs-col>
    </vs-row>
    <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
      <div>
        <!-- <a
          class="resume"
          href="https://github.com/arminv/resume/blob/master/Armin_Varshokar_Resume.pdf"
          target="_blank"
          rel="noopener noreferrer"
        > -->
          <vs-button color="primary" type="filled" class="resume-button" @click="downloadResume"
            >Download Resume</vs-button
          >
        <!-- </a> -->
      </div>
    </vs-col>
    <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
      <h2>Tools I Use</h2>
    </vs-col>
    <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
      <div class="logo-container">
        <vs-row>
          <Logo
            src="https://img.icons8.com/color/96/000000/html-5.png"
            name="HTML"
          />
          <Logo
            src="https://img.icons8.com/color/96/000000/css3.png"
            name="CSS"
          />
          <Logo
            src="https://img.icons8.com/color/96/000000/javascript.png"
            name="JavaScript"
          />
          <Logo
            src="https://img.icons8.com/color/96/000000/git.png"
            name="Git"
          />
          <Logo
            src="https://img.icons8.com/color/96/000000/vue-js.png"
            name="Vue"
          />
          <Logo
            :src="imageSrc"
            name="Laravel"
          />
          <Logo
            :src="imagePHP"
            name="Php"
          />
          <Logo
            :src="imagesql"
            name="Mysql"
          />
          
        </vs-row>
        <!-- <vs-row>
          <vs-col
            vs-type="flex"
            vs-justify="center"
            vs-align="center"
            vs-w="12"
          >
            <span class="icon-credit"
              >icons by
              <a
                href="https://icons8.com/icon/24895/npm"
                target="_blank"
                rel="noopener noreferrer"
                >Icons8</a
              ></span
            >
          </vs-col>
        </vs-row> -->
      </div>
    </vs-col>
  </div>
</template>

<script>
import Logo from "../components/Logo";
export default {
  name: "Home",
  components: { Logo },
  data() {
    return {
      imageSrc: require('@/assets/lalabel.png'),
      imagePHP: require('@/assets/php.png'),
      imagesql: require('@/assets/mysql.png'),
    }
  },
  methods: {
    getDayOfWeek() {
      let today = new Date();
      let weekday = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ];
      return weekday[today.getDay()];
    },
    downloadResume() {
      // Path to the PDF file
      const pdfPath = '/jason_cv.pdf';

      // Fetch the PDF file
      fetch(pdfPath)
        .then(response => response.blob())
        .then(blob => {
          // Create a URL for the blob
          const url = URL.createObjectURL(blob);

          // Create an anchor element to initiate the download
          const a = document.createElement('a');
          a.href = url;
          a.download = 'Jason Resume.pdf'; // Change the filename if needed
          a.style.display = 'none';

          // Append the anchor element to the body
          document.body.appendChild(a);

          // Trigger a click event on the anchor element
          a.click();

          // Clean up
          document.body.removeChild(a);
          URL.revokeObjectURL(url);
        })
        .catch(error => {
          console.error('Error downloading resume:', error);
        });
    }
  }
};
</script>

<style lang="css" scoped>
h2 {
  font-size: 26px;
  color: var(--gold-color);
}
.intro {
  font-size: 22px;
  line-height: 1.5em;
  margin: 2.5rem 3.5rem 0rem 3.5rem;
  padding-bottom: 2em;
  max-width: 65%;
  color: var(--content-color);
  text-align: left;
  text-justify: inter-word;
}

.signature {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  text-align: left;
  text-justify: inter-word;
}

.logo-container {
  justify-content: center;
  align-content: center;
  margin: 2.5rem 3.5rem 2rem 3.5rem;
}

.icon-credit {
  margin-top: 3rem;
}

.resume-button {
  margin: 0rem 0rem 3rem 0rem;
}

.resume {
  color: var(--content-color);
}
</style>
