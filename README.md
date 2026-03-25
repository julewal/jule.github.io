<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="utf-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Jule Walsch — Graphic Designer</title>
  <script src="https://cdn.tailwindcss.com?plugins=forms"></script>
  <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;600;700;800;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200&display=swap" rel="stylesheet"/>
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          colors: {
            primary: '#135973',
            'primary-dark': '#0e4559',
            'primary-container': '#d7f1ff',
            'on-primary': '#ffffff',
            secondary: '#72556e',
            'secondary-container': '#fad4f3',
            'on-secondary': '#ffffff',
            tertiary: '#5b4f5b',
            surface: '#f8f9fb',
            'surface-bright': '#ffffff',
            'surface-container': '#eceef0',
            'surface-container-low': '#f2f4f6',
            'surface-container-high': '#e7e8ea',
            'surface-container-lowest': '#ffffff',
            'on-surface': '#191c1e',
            'on-surface-variant': '#40484c',
            'outline-variant': '#c0c8cd',
            outline: '#70787d',
          },
          fontFamily: {
            headline: ['Manrope', 'sans-serif'],
            body: ['DM Sans', 'sans-serif'],
          },
          borderRadius: {
            xl: '0.75rem',
            '2xl': '1.25rem',
          }
        }
      }
    }
  </script>
  <style>
    :root {
      --primary: #135973;
      --secondary: #72556e;
      --surface: #f8f9fb;
    }

    * { box-sizing: border-box; }

    body {
      background-color: var(--surface);
      font-family: 'DM Sans', sans-serif;
      color: #191c1e;
    }

    .material-symbols-outlined {
      font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24;
    }

    /* Nav blur */
    .nav-blur {
      background: rgba(248, 249, 251, 0.82);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border-bottom: 1px solid rgba(192, 200, 205, 0.2);
    }

    /* Bento card hover */
    .bento-card {
      transition: transform 0.28s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.28s ease;
    }
    .bento-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 16px 40px -8px rgba(19, 89, 115, 0.12);
    }

    /* Animated underline for nav links */
    .nav-link {
      position: relative;
    }
    .nav-link::after {
      content: '';
      position: absolute;
      bottom: -3px;
      left: 0;
      width: 0;
      height: 2px;
      background: var(--primary);
      transition: width 0.25s ease;
    }
    .nav-link:hover::after, .nav-link.active::after {
      width: 100%;
    }
    .nav-link.active {
      color: var(--primary);
    }

    /* Floating label inputs */
    .float-group { position: relative; }
    .float-group input,
    .float-group textarea {
      background: transparent;
      border: none;
      border-bottom: 1.5px solid #c0c8cd;
      padding: 20px 0 8px 0;
      width: 100%;
      font-size: 0.9rem;
      color: #191c1e;
      font-family: 'DM Sans', sans-serif;
      transition: border-color 0.2s;
      outline: none;
    }
    .float-group input:focus,
    .float-group textarea:focus {
      border-bottom-color: var(--primary);
    }
    .float-group label {
      position: absolute;
      left: 0;
      top: 18px;
      font-size: 0.7rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: rgba(64,72,76,0.5);
      transition: top 0.2s, font-size 0.2s, color 0.2s;
      pointer-events: none;
    }
    .float-group input:focus ~ label,
    .float-group input:not(:placeholder-shown) ~ label,
    .float-group textarea:focus ~ label,
    .float-group textarea:not(:placeholder-shown) ~ label {
      top: 2px;
      font-size: 0.6rem;
      color: var(--primary);
    }

    /* Page load fade-in stagger */
    .fade-in { opacity: 0; transform: translateY(22px); animation: fadeUp 0.6s ease forwards; }
    .fade-in:nth-child(1) { animation-delay: 0.05s; }
    .fade-in:nth-child(2) { animation-delay: 0.15s; }
    .fade-in:nth-child(3) { animation-delay: 0.25s; }
    .fade-in:nth-child(4) { animation-delay: 0.35s; }
    .fade-in:nth-child(5) { animation-delay: 0.45s; }

    @keyframes fadeUp {
      to { opacity: 1; transform: translateY(0); }
    }

    /* Headshot image */
    .headshot-ring {
      background: linear-gradient(135deg, #135973 0%, #72556e 100%);
      padding: 2px;
      border-radius: 999px;
      display: inline-block;
    }

    /* Icon interest cards */
    .interest-icon {
      font-size: 2rem !important;
    }

    /* Submit button shimmer */
    .btn-submit {
      background: var(--primary);
      color: #fff;
      font-family: 'Manrope', sans-serif;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      font-size: 0.78rem;
      border: none;
      border-radius: 0.75rem;
      padding: 1rem;
      width: 100%;
      cursor: pointer;
      transition: background 0.22s, transform 0.12s;
      position: relative;
      overflow: hidden;
    }
    .btn-submit:hover { background: #0e4559; }
    .btn-submit:active { transform: scale(0.98); }

    /* Video bg card effect */
    .media-card {
      position: relative;
      overflow: hidden;
    }
    .media-card .bg-icon {
      position: absolute;
      right: -24px;
      bottom: -24px;
      opacity: 0.08;
      font-size: 8rem !important;
      pointer-events: none;
    }
  </style>
</head>
<body>

<!-- ─── Navigation ─── -->
<nav class="fixed top-0 w-full z-50 nav-blur">
  <div class="max-w-7xl mx-auto px-6 md:px-10 py-4 flex justify-between items-center">
    <span class="font-headline font-extrabold text-xl text-primary tracking-tight">Jule Walsch</span>
    <div class="hidden md:flex gap-8 items-center">
      <a href="#" class="nav-link text-sm font-semibold font-headline tracking-tight text-slate-600 hover:text-primary transition-colors">Experience</a>
      <a href="#" class="nav-link text-sm font-semibold font-headline tracking-tight text-slate-600 hover:text-primary transition-colors">Education</a>
      <a href="#" class="nav-link active text-sm font-semibold font-headline tracking-tight transition-colors">About</a>
      <a href="#" class="nav-link text-sm font-semibold font-headline tracking-tight text-slate-600 hover:text-primary transition-colors">Contact</a>
      <button class="w-9 h-9 flex items-center justify-center rounded-full hover:bg-[#fad4f3]/40 transition-all duration-300 active:scale-90">
        <span class="material-symbols-outlined text-primary" style="font-size:1.3rem">mail</span>
      </button>
    </div>
    <!-- Mobile hamburger (cosmetic) -->
    <button class="md:hidden w-9 h-9 flex flex-col justify-center gap-[5px] items-end pr-0.5">
      <span class="block h-[2px] w-6 bg-primary rounded-full"></span>
      <span class="block h-[2px] w-4 bg-primary rounded-full"></span>
    </button>
  </div>
</nav>

<!-- ─── Main ─── -->
<main class="pt-28 pb-24 px-6 md:px-10 max-w-7xl mx-auto">

  <!-- Header -->
  <header class="mb-14">
    <span class="inline-block bg-secondary-container text-secondary px-3 py-1 text-[10px] tracking-[0.12em] font-bold uppercase font-body mb-5 rounded-full">The Designer Behind the Work</span>
    <h1 class="text-5xl md:text-7xl font-headline font-black tracking-tighter text-primary leading-[1.05] max-w-3xl">
      Turning curiosity<br class="hidden md:block"/> into visual<br class="hidden md:block"/> narratives.
    </h1>
  </header>

  <!-- Bento Grid -->
  <div class="grid grid-cols-1 md:grid-cols-12 gap-5 fade-in" style="animation-delay:0.1s;opacity:0">

    <!-- ── About Me ── -->
    <section class="md:col-span-8 bento-card bg-surface-container-lowest border border-outline-variant/20 rounded-2xl p-8 md:p-12 flex flex-col justify-between min-h-[400px]">
      <div class="max-w-xl">
        <p class="text-[10px] font-bold tracking-[0.22em] uppercase text-secondary font-body mb-7">Personal Narrative</p>
        <p class="text-lg md:text-xl text-on-surface-variant leading-relaxed font-body">
          Based in <span class="text-primary font-semibold">Borchen, Germany</span>, I blend technical precision with creative intuition. My journey is defined by a pursuit of "intentional design"—where every element serves a functional purpose while maintaining an aesthetic soul.
        </p>
        <p class="mt-5 text-on-surface-variant/75 leading-relaxed text-base">
          I believe the best work happens at the intersection of diverse interests, from the rhythmic strategy of team sports to the quiet, focused meditation of drawing.
        </p>
      </div>
      <div class="mt-10 flex items-center gap-4">
        <div class="headshot-ring">
          <img
            src="https://lh3.googleusercontent.com/aida-public/AB6AXuD_WqXCAs8f3W_7gKCmDk1BTdIWv14h05N_6s1TdKgBC9J-JxEHAVFxsTo_XK654IsN04GVX_Kig7-m4_5Vqpfv3MR80qW1kk1mvyR0e-yLU9D4QOtNlM1GjAhwUJ8CvO_jLdxt_IGK7Tv3S6G3T5ZJIb-ZpFuWUGypo1roRWX9d3T-qG_U4o7Vsz1zCJQzPEvRwQYrlveCRkiQbvJuVdb9IkTuak74V9DO878EIlsfdZ_GF6RkewlgNe0iWl4t6wkO_2e-WznbIWA"
            alt="Jule Walsch"
            class="w-14 h-14 rounded-full object-cover grayscale hover:grayscale-0 transition-all duration-500 block"
          />
        </div>
        <div>
          <p class="font-headline font-bold text-primary">Jule Walsch</p>
          <p class="text-[10px] uppercase tracking-widest text-on-surface-variant/55 font-body mt-0.5">Graphic Designer</p>
        </div>
      </div>
    </section>

    <!-- ── Contact Info Card ── -->
    <section class="md:col-span-4 bento-card bg-primary text-white rounded-2xl p-8 flex flex-col justify-between">
      <div>
        <p class="text-[10px] font-bold tracking-[0.22em] uppercase opacity-55 font-body mb-7">Direct Access</p>
        <div class="space-y-6">
          <div class="group">
            <p class="text-[9px] uppercase tracking-widest opacity-50 mb-1">Email</p>
            <a href="mailto:jule.walsch@aol.com" class="font-headline font-semibold text-base border-b border-transparent group-hover:border-white transition-all pb-0.5">jule.walsch@aol.com</a>
          </div>
          <div class="group">
            <p class="text-[9px] uppercase tracking-widest opacity-50 mb-1">Phone</p>
            <a href="tel:+4915157471814" class="font-headline font-semibold text-base border-b border-transparent group-hover:border-white transition-all pb-0.5">+49 1515 7471814</a>
          </div>
          <div>
            <p class="text-[9px] uppercase tracking-widest opacity-50 mb-1">Location</p>
            <p class="font-headline font-semibold text-base">Borchen, Germany</p>
          </div>
        </div>
      </div>
      <div class="pt-7 border-t border-white/10 mt-8 flex gap-4">
        <span class="material-symbols-outlined opacity-55 cursor-pointer hover:opacity-100 transition-opacity">share</span>
        <span class="material-symbols-outlined opacity-55 cursor-pointer hover:opacity-100 transition-opacity">language</span>
      </div>
    </section>

    <!-- ── Interests Grid ── -->
    <div class="md:col-span-7 grid grid-cols-2 md:grid-cols-3 gap-4">

      <!-- Soccer -->
      <div class="col-span-2 md:col-span-1 bento-card bg-secondary-container rounded-2xl p-6 flex flex-col justify-between aspect-square md:aspect-auto cursor-default">
        <span class="material-symbols-outlined interest-icon text-secondary mb-3" style="font-size:2.2rem">sports_soccer</span>
        <p class="font-headline font-bold text-secondary text-lg">Soccer</p>
      </div>

      <!-- Basketball/Volleyball -->
      <div class="bento-card bg-surface-container-low rounded-2xl p-6 flex flex-col justify-between cursor-default">
        <span class="material-symbols-outlined text-primary mb-3" style="font-size:1.8rem;font-variation-settings:'FILL' 1,'wght' 400,'GRAD' 0,'opsz' 24">sports_basketball</span>
        <p class="font-body font-medium text-xs uppercase tracking-tight text-on-surface-variant leading-snug">Uni Sports:<br/>Basketball &amp; Volleyball</p>
      </div>

      <!-- Drawing -->
      <div class="bento-card bg-surface-container-low rounded-2xl p-6 flex flex-col justify-between cursor-default">
        <span class="material-symbols-outlined text-primary mb-3" style="font-size:1.8rem">draw</span>
        <p class="font-headline font-bold text-primary">Drawing</p>
      </div>

      <!-- Creating Videos — wide -->
      <div class="col-span-2 media-card bento-card bg-surface-container-high rounded-2xl p-6 flex flex-col md:flex-row items-center gap-4 cursor-default">
        <div class="relative z-10">
          <p class="text-[10px] font-bold uppercase tracking-[0.2em] text-primary mb-1">Media</p>
          <h3 class="text-2xl font-headline font-extrabold tracking-tight text-primary">Creating Videos</h3>
        </div>
        <span class="material-symbols-outlined bg-icon text-primary">videocam</span>
      </div>

      <!-- Traveling -->
      <div class="bento-card bg-primary-container rounded-2xl p-6 flex flex-col justify-between cursor-default">
        <span class="material-symbols-outlined text-primary mb-3" style="font-size:1.8rem">flight_takeoff</span>
        <p class="font-headline font-bold text-primary">Traveling</p>
      </div>

    </div>

    <!-- ── Contact Form ── -->
    <section class="md:col-span-5 bento-card bg-surface-container-low rounded-2xl p-8 md:p-10">
      <h3 class="font-headline font-bold text-2xl text-primary mb-1">Let's connect.</h3>
      <p class="text-on-surface-variant/65 text-sm mb-8">Whether it's a project inquiry or just a hello, I'd love to hear from you.</p>
      <form class="space-y-6" onsubmit="handleSubmit(event)">
        <div class="float-group">
          <input type="text" id="name" placeholder=" " autocomplete="off"/>
          <label for="name">Name</label>
        </div>
        <div class="float-group">
          <input type="email" id="email" placeholder=" " autocomplete="off"/>
          <label for="email">Email Address</label>
        </div>
        <div class="float-group">
          <textarea id="message" placeholder=" " rows="3" style="resize:none"></textarea>
          <label for="message">Your Message</label>
        </div>
        <button type="submit" class="btn-submit" id="sendBtn">Send Message</button>
      </form>
    </section>

  </div>
</main>

<!-- ─── Footer ─── -->
<footer class="border-t border-slate-100 bg-[#f8fafb] py-12">
  <div class="max-w-7xl mx-auto px-6 md:px-10 flex flex-col md:flex-row justify-between items-center gap-6">
    <p class="text-xs uppercase tracking-widest font-medium text-slate-400 font-body">© 2024 Jule Walsch — Built with Intention</p>
    <div class="flex gap-7">
      <a href="#" class="text-xs uppercase tracking-widest font-medium text-slate-400 hover:text-primary transition-all duration-200 hover:-translate-y-0.5 font-body">LinkedIn</a>
      <a href="#" class="text-xs uppercase tracking-widest font-medium text-slate-400 hover:text-primary transition-all duration-200 hover:-translate-y-0.5 font-body">GitHub</a>
      <a href="#" class="text-xs uppercase tracking-widest font-medium text-slate-400 hover:text-primary transition-all duration-200 hover:-translate-y-0.5 font-body">Dribbble</a>
      <a href="#top" class="text-xs uppercase tracking-widest font-medium text-slate-400 hover:text-primary transition-all duration-200 hover:-translate-y-0.5 font-body">↑ Top</a>
    </div>
  </div>
</footer>

<script>
  function handleSubmit(e) {
    e.preventDefault();
    const btn = document.getElementById('sendBtn');
    btn.textContent = 'Sent ✓';
    btn.style.background = '#2a8c5a';
    setTimeout(() => {
      btn.textContent = 'Send Message';
      btn.style.background = '';
      e.target.reset();
    }, 2800);
  }

  // Staggered entrance animation
  document.addEventListener('DOMContentLoaded', () => {
    const header = document.querySelector('header');
    header.style.opacity = 0;
    header.style.transform = 'translateY(24px)';
    header.style.transition = 'opacity 0.65s ease, transform 0.65s ease';
    requestAnimationFrame(() => {
      header.style.opacity = 1;
      header.style.transform = 'translateY(0)';
    });
  });
</script>

</body>
</html>
