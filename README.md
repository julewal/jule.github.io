your-cv-website/
│
├── index.html
├── style.css
├── script.js
└── assets/
    ├── your-photo.png
    └── favicon.png (optional)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jule Walsch</title>
  <link rel="stylesheet" href="style.css" />
  <script defer src="script.js"></script>
</head>

<body>
  <!-- HERO SECTION -->
  <section class="hero">
    <div class="hero-text">
      <h1>HI! NICE TO MEET YOU</h1>
    </div>
    <div class="hero-image">
      <img src="assets/your-photo.png" alt="Jule Walsch" />
    </div>
  </section>

  <!-- ABOUT -->
  <section class="about">
    <h2>About Me</h2>
    <p>
      I’m Jule Walsch, a student of International Business Studies at Universität Paderborn with a passion for creative marketing, international experiences, and content creation.
    </p>
  </section>

  <!-- EXPERIENCE -->
  <section class="experience">
    <h2>Work Experience</h2>

    <div class="job">
      <h3>Student Assistant – Universität Paderborn</h3>
      <p><i>Nov 2025 - Present</i></p>
      <ul>
        <li>Literature research and lecture material support.</li>
      </ul>
    </div>

    <div class="job">
      <h3>Global Campaign Management – AUDI AG</h3>
      <p><i>Mar 2025 - Aug 2025</i></p>
      <ul>
        <li>Development and implementation of global campaigns across TV, digital, and print.</li>
        <li>Coordinated agency meetings and creative briefings.</li>
      </ul>
    </div>

    <div class="job">
      <h3>Content Management – YAT Reisen</h3>
      <p><i>May 2023 - Jun 2024</i></p>
      <ul>
        <li>Developed content strategies and end-to-end campaign management.</li>
        <li>Created social media, blog, and video content.</li>
      </ul>
    </div>
  </section>

  <!-- EDUCATION -->
  <section class="education">
    <h2>Education</h2>
    <p><strong>International Business Studies</strong>, Universität Paderborn, GPA: 1.6 (3.4)</p>
    <p><strong>Study Abroad</strong>, Universitat de Valencia – Sep 2024 to Jan 2025</p>
    <p><strong>Abitur</strong>, Goerdeler Gymnasium Paderborn – Score: 1.3</p>
  </section>

  <!-- SKILLS & LANGUAGES -->
  <section class="skills">
    <h2>Skills & Languages</h2>
    <ul>
      <li><strong>Languages:</strong> German (native) | English (C1) | Spanish (B1.2) | French (B1+)</li>
      <li><strong>Tools:</strong> Microsoft Office, Hubspot, Wordpress, Cleverreach</li>
    </ul>
  </section>

  <!-- CONTACT -->
  <section class="contact">
    <h2>Contact</h2>
    <p><a href="mailto:jule.walsch@aol.com">jule.walsch@aol.com</a></p>
    <p>Ahornweg 29, 33178 Borchen, Germany</p>
  </section>
</body>
</html>
body {
  margin: 0;
  font-family: "Poppins", "Helvetica", sans-serif;
  background-color: #f8fafd;
  color: #333;
  line-height: 1.6;
}

/* HERO SECTION */
.hero {
  position: relative;
  text-align: center;
  padding-top: 4rem;
}

.hero-text h1 {
  font-size: 2.8rem;
  font-weight: 700;
  color: #2d6a7b;
  text-shadow: 2px 2px #f4b4d2;
  position: absolute;
  width: 100%;
  top: 20%;
  animation: fadeInDown 2s ease forwards;
  z-index: 1;
}

.hero-image img {
  width: 250px;
  border-radius: 8px;
  position: relative;
  z-index: 2;
  animation: popUp 2s ease forwards;
}

/* SECTIONS */
section {
  margin: 3rem auto;
  width: 80%;
  max-width: 800px;
}

h2 {
  color: #2d6a7b;
  border-bottom: 2px solid #f4b4d2;
  padding-bottom: 0.5rem;
}

.job {
  margin-bottom: 1.5rem;
}

a {
  color: #2d6a7b;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}

/* ANIMATIONS */
@keyframes fadeInDown {
  from { opacity: 0; transform: translateY(-40px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes popUp {
  from { opacity: 0; transform: scale(0.8); }
  to { opacity: 1; transform: scale(1); }
}
document.addEventListener("scroll", () => {
  const sections = document.querySelectorAll("section");
  sections.forEach(sec => {
    const top = sec.getBoundingClientRect().top;
    if (top < window.innerHeight - 120) {
      sec.classList.add("visible");
    }
  });
});
section {
  opacity: 0;
  transform: translateY(40px);
  transition: all 0.7s ease;
}
section.visible {
  opacity: 1;
  transform: translateY(0);
}
