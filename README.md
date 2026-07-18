<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Student Portfolio</title>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;scroll-behavior:smooth;font-family:'Segoe UI',Arial,sans-serif;}

#particles-canvas{position:fixed;top:0;left:0;width:100%;height:100%;z-index:-1;pointer-events:none;}

body{background:#0f0c29;color:#fff;}

.navbar{background:rgba(15,12,41,0.85);backdrop-filter:blur(20px);box-shadow:0 4px 30px rgba(124,58,237,0.3);border-bottom:1px solid rgba(124,58,237,0.2);}
.navbar-brand{font-weight:900;font-size:28px;background:linear-gradient(45deg,#7C3AED,#4F46E5); -webkit-background-clip:text; -webkit-text-fill-color:transparent;}
.nav-link{font-weight:600;color:#ccc!important;transition:.3s;position:relative;}
.nav-link::after{content:'';position:absolute;bottom:-4px;left:0;width:0;height:2px;background:linear-gradient(45deg,#7C3AED,#4F46E5);transition:.3s;}
.nav-link:hover::after{width:100%;}
.nav-link:hover{color:#fff!important;}

.hero{min-height:100vh;display:flex;align-items:center;background:linear-gradient(135deg,rgba(124,58,237,0.15),rgba(79,70,229,0.15));position:relative;overflow:hidden;}
.hero::before{content:'';position:absolute;width:600px;height:600px;background:radial-gradient(circle,rgba(124,58,237,0.2),transparent 70%);top:-100px;right:-100px;border-radius:50%;animation:pulse 4s ease-in-out infinite;}
.hero::after{content:'';position:absolute;width:400px;height:400px;background:radial-gradient(circle,rgba(79,70,229,0.2),transparent 70%);bottom:-100px;left:-100px;border-radius:50%;animation:pulse 4s ease-in-out infinite reverse;}
@keyframes pulse{0%,100%{transform:scale(1);opacity:0.5;}50%{transform:scale(1.2);opacity:1;}}

.hero h1{font-size:56px;font-weight:900;color:#fff;line-height:1.2;}
.hero h1 span{background:linear-gradient(45deg,#A78BFA,#818CF8);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.hero h4{margin-top:15px;color:#A78BFA;font-size:22px;font-weight:600;}
.hero p{margin-top:20px;font-size:17px;line-height:30px;color:#ccc;}

.profile-img{width:300px;height:300px;border-radius:50%;object-fit:cover;border:5px solid transparent;background:linear-gradient(white,white) padding-box,linear-gradient(135deg,#7C3AED,#4F46E5,#A78BFA) border-box;box-shadow:0 0 40px rgba(124,58,237,0.6),0 0 80px rgba(124,58,237,0.3);transition:.5s;animation:float 3s ease-in-out infinite;}
.profile-img:hover{transform:scale(1.08);box-shadow:0 0 60px rgba(124,58,237,0.9);}
@keyframes float{0%,100%{transform:translateY(0);}50%{transform:translateY(-15px);}}

.btn-custom{background:linear-gradient(45deg,#7C3AED,#4F46E5);padding:14px 35px;font-weight:bold;border-radius:50px;transition:.4s;color:#fff;border:none;box-shadow:0 5px 25px rgba(124,58,237,0.5);position:relative;overflow:hidden;}
.btn-custom::before{content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;background:linear-gradient(45deg,transparent,rgba(255,255,255,0.2),transparent);transition:.5s;}
.btn-custom:hover::before{left:100%;}
.btn-custom:hover{transform:translateY(-5px);box-shadow:0 10px 35px rgba(124,58,237,0.7);color:#fff;}
.btn-outline-custom{border:2px solid #7C3AED;padding:12px 30px;font-weight:bold;border-radius:50px;transition:.4s;color:#A78BFA;background:transparent;}
.btn-outline-custom:hover{background:linear-gradient(45deg,#7C3AED,#4F46E5);color:#fff;transform:translateY(-5px);}

.section-title{font-weight:900;font-size:42px;margin-bottom:15px;background:linear-gradient(45deg,#7C3AED,#4F46E5);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.section-subtitle{color:#A78BFA;margin-bottom:50px;font-size:16px;}
.section-divider{width:80px;height:4px;background:linear-gradient(45deg,#7C3AED,#4F46E5);border-radius:10px;margin:10px auto 40px;}

.glass-card{background:rgba(255,255,255,0.05);backdrop-filter:blur(20px);border:1px solid rgba(124,58,237,0.3);border-radius:24px;padding:30px;transition:.4s;position:relative;overflow:hidden;}
.glass-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,#7C3AED,#4F46E5,transparent);opacity:0;transition:.4s;}
.glass-card:hover::before{opacity:1;}
.glass-card:hover{transform:translateY(-12px);border-color:rgba(124,58,237,0.7);box-shadow:0 20px 50px rgba(124,58,237,0.3);}

.skill-badge{display:inline-block;padding:12px 26px;margin:8px;background:rgba(124,58,237,0.15);color:#A78BFA;font-weight:700;border-radius:50px;transition:.4s;border:1px solid rgba(124,58,237,0.4);cursor:default;}
.skill-badge:hover{background:linear-gradient(45deg,#7C3AED,#4F46E5);color:#fff;transform:scale(1.12) translateY(-3px);box-shadow:0 8px 25px rgba(124,58,237,0.5);border-color:transparent;}

.skill-bar{background:rgba(255,255,255,0.1);border-radius:10px;height:8px;overflow:hidden;}
.skill-progress{height:100%;border-radius:10px;background:linear-gradient(90deg,#7C3AED,#4F46E5);animation:fillBar 2s ease forwards;width:0;}
@keyframes fillBar{to{width:var(--width);}}

.stat-box{text-align:center;padding:20px;}
.stat-number{font-size:42px;font-weight:900;background:linear-gradient(45deg,#7C3AED,#4F46E5);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.stat-label{color:#aaa;font-size:14px;margin-top:5px;}

.form-control-glass{background:rgba(255,255,255,0.07);border:1px solid rgba(124,58,237,0.3);border-radius:15px;padding:15px;color:#fff;transition:.3s;}
.form-control-glass::placeholder{color:#aaa;}
.form-control-glass:focus{background:rgba(124,58,237,0.1);border-color:#7C3AED;box-shadow:0 0 20px rgba(124,58,237,0.3);color:#fff;outline:none;}

footer{background:linear-gradient(135deg,rgba(124,58,237,0.2),rgba(79,70,229,0.2));border-top:1px solid rgba(124,58,237,0.3);color:white;padding:50px 0 30px;}
.social a{display:inline-flex;align-items:center;justify-content:center;width:45px;height:45px;border-radius:50%;background:rgba(124,58,237,0.2);color:white;font-size:20px;margin:8px;transition:.4s;border:1px solid rgba(124,58,237,0.3);}
.social a:hover{background:linear-gradient(45deg,#7C3AED,#4F46E5);transform:translateY(-5px) rotate(10deg);box-shadow:0 8px 20px rgba(124,58,237,0.5);}

.reveal{opacity:0;transform:translateY(40px);transition:.8s ease;}
.reveal.active{opacity:1;transform:translateY(0);}

#backTop{position:fixed;bottom:30px;right:30px;width:48px;height:48px;border-radius:50%;background:linear-gradient(45deg,#7C3AED,#4F46E5);color:#fff;border:none;font-size:20px;display:none;align-items:center;justify-content:center;cursor:pointer;box-shadow:0 5px 20px rgba(124,58,237,0.6);z-index:999;transition:.3s;}
#backTop:hover{transform:translateY(-4px);}

.edu-icon{font-size:50px;margin-bottom:15px;display:block;}
.bg-dark-section{background:rgba(0,0,0,0.2);}
</style>
</head>
<body>

<canvas id="particles-canvas"></canvas>
<button id="backTop" onclick="window.scrollTo({top:0,behavior:'smooth'})"><i class="bi bi-arrow-up"></i></button>
<nav class="navbar navbar-expand-lg fixed-top">
<div class="container">
<a class="navbar-brand" href="#">✦ My Portfolio</a>
<button class="navbar-toggler border-0" data-bs-toggle="collapse" data-bs-target="#menu" style="filter:invert(1)">
<span class="navbar-toggler-icon"></span>
</button>
<div class="collapse navbar-collapse" id="menu">
<ul class="navbar-nav ms-auto gap-2">
<li class="nav-item"><a class="nav-link" href="#home">Home</a></li>
<li class="nav-item"><a class="nav-link" href="#education">Education</a></li>
<li class="nav-item"><a class="nav-link" href="#skills">Skills</a></li>
<li class="nav-item"><a class="nav-link" href="#projects">Projects</a></li>
<li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
</ul>
</div>
</div>
</nav>

<section id="home" class="hero py-5">
<div class="container">
<div class="row align-items-center">
<div class="col-lg-6 reveal">
<p style="color:#A78BFA;font-size:16px;letter-spacing:3px;text-transform:uppercase;margin-bottom:10px;">Welcome to my Portfolio</p>
<h1>Hello, I'm <br><span id="typed-name">Karthika M</span></h1>
<h4><span id="typing-role"></span></h4>
<p>I am a passionate Computer Science Engineering student specializing in Artificial Intelligence and Machine Learning. I have a strong interest in Web Development, Programming, and AI-based technologies. I enjoy building responsive websites with clean and user-friendly interfaces using HTML, CSS, Bootstrap, and JavaScript. I am continuously learning and exploring new technologies to enhance my skills in software development and artificial intelligence.</p>
<div class="d-flex gap-3 flex-wrap mt-4">
<a href="#contact" class="btn btn-custom">Contact Me <i class="bi bi-arrow-right"></i></a>
<a href="#projects" class="btn btn-outline-custom">My Projects</a>
</div>
<div class="row mt-5">
<div class="col-4 stat-box"><div class="stat-number">3+</div><div class="stat-label">Projects</div></div>
<div class="col-4 stat-box"><div class="stat-number">10+</div><div class="stat-label">Skills</div></div>
<div class="col-4 stat-box"><div class="stat-number">1+</div><div class="stat-label">Years Study</div></div>
</div>
</div>
<div class="col-lg-6 text-center mt-5 mt-lg-0 reveal">
<div style="position:relative;display:inline-block;">
<img src="prof.jpg.png" class="profile-img">
<div style="position:absolute;top:-20px;right:-20px;width:80px;height:80px;background:linear-gradient(45deg,#7C3AED,#4F46E5);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:30px;animation:float 2s ease-in-out infinite;">💻</div>
<div style="position:absolute;bottom:-10px;left:-20px;width:60px;height:60px;background:linear-gradient(45deg,#4F46E5,#7C3AED);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:24px;animation:float 2.5s ease-in-out infinite reverse;">🎨</div>
</div>
</div>
</div>
</div>
</section>

<section id="education" class="py-5 bg-dark-section">
<div class="container">
<div class="text-center reveal">
<h2 class="section-title">Education</h2>
<div class="section-divider"></div>
<p class="section-subtitle">My academic journey</p>
</div>
<div class="row g-4">
<div class="col-md-4 reveal">
<div class="glass-card text-center h-100">
<span class="edu-icon">🎓</span>
<h4 style="color:#A78BFA">B.E Computer Science (AIML)</h4>
<p style="color:#aaa;margin:10px 0;">Sri Venkateswaraa College of Technology</p>
<span style="background:linear-gradient(45deg,#7C3AED,#4F46E5);padding:6px 20px;border-radius:20px;font-size:14px;font-weight:700;">2026 - 2029</span>
</div>
</div>
<div class="col-md-4 reveal">
<div class="glass-card text-center h-100">
<span class="edu-icon">📚</span>
<h4 style="color:#A78BFA">Higher Secondary</h4>
<p style="color:#aaa;margin:10px 0;">Holy Queen Matric Higher Secondary School</p>
<span style="background:linear-gradient(45deg,#059669,#0D9488);padding:6px 20px;border-radius:20px;font-size:14px;font-weight:700;">2023 - 2025</span>
</div>
</div>
<div class="col-md-4 reveal">
<div class="glass-card text-center h-100">
<span class="edu-icon">🏆</span>
<h4 style="color:#A78BFA">SSLC</h4>
<p style="color:#aaa;margin:10px 0;">Holy Queen Matric Higher Secondary School</p>
<span style="background:linear-gradient(45deg,#E11D48,#FB7185);padding:6px 20px;border-radius:20px;font-size:14px;font-weight:700;">2022 - 2023</span>
</div>
</div>
</div>
</div>
</section>

<section id="skills" class="py-5">
<div class="container">
<div class="text-center reveal">
<h2 class="section-title">My Skills</h2>
<div class="section-divider"></div>
<p class="section-subtitle">Technologies I work with</p>
</div>
<div class="text-center reveal mb-5">
<span class="skill-badge">HTML</span>
<span class="skill-badge">CSS</span>
<span class="skill-badge">Bootstrap5</span>
<span class="skill-badge">JavaScript</span>
<span class="skill-badge">C Programming</span>
<span class="skill-badge">C++</span>
<span class="skill-badge">Python</span>
<span class="skill-badge">Java</span>
<span class="skill-badge">MySQL</span>
<span class="skill-badge">MongoDB</span>
</div>
<div class="row g-4 reveal">
<div class="col-md-6"><div class="glass-card"><div class="d-flex justify-content-between mb-2"><span style="color:#A78BFA;font-weight:700;">HTML & CSS</span><span style="color:#aaa;">90%</span></div><div class="skill-bar"><div class="skill-progress" style="--width:90%"></div></div></div></div>
<div class="col-md-6"><div class="glass-card"><div class="d-flex justify-content-between mb-2"><span style="color:#A78BFA;font-weight:700;">JavaScript</span><span style="color:#aaa;">75%</span></div><div class="skill-bar"><div class="skill-progress" style="--width:75%"></div></div></div></div>
<div class="col-md-6"><div class="glass-card"><div class="d-flex justify-content-between mb-2"><span style="color:#A78BFA;font-weight:700;">Python</span><span style="color:#aaa;">80%</span></div><div class="skill-bar"><div class="skill-progress" style="--width:80%"></div></div></div></div>
<div class="col-md-6"><div class="glass-card"><div class="d-flex justify-content-between mb-2"><span style="color:#A78BFA;font-weight:700;">MySQL & MongoDB</span><span style="color:#aaa;">70%</span></div><div class="skill-bar"><div class="skill-progress" style="--width:70%"></div></div></div></div>
</div>
</div>
</section>

<section id="projects" class="py-5 bg-dark-section">
<div class="container">
<div class="text-center reveal">
<h2 class="section-title">My Projects</h2>
<div class="section-divider"></div>
<p class="section-subtitle">What I've built</p>
</div>
<div class="row g-4">
<div class="col-md-4 reveal">
<div class="glass-card h-100 text-center">
<div style="font-size:60px;margin-bottom:20px;">🛍️</div>
<h4 style="color:#A78BFA;margin-bottom:15px;">Skincare Website</h4>
<p style="color:#aaa;">A modern skincare shopping website with elegant product cards, attractive designs, and a responsive user-friendly layout.</p>
<div class="mt-3">
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">HTML</span>
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">CSS</span>
</div>
</div>
</div>
<div class="col-md-4 reveal">
<div class="glass-card h-100 text-center">
<div style="font-size:60px;margin-bottom:20px;">🌐</div>
<h4 style="color:#A78BFA;margin-bottom:15px;">Campus Ambassador</h4>
<p style="color:#aaa;">A campus ambassador role focused on promoting Elite Coders programs, connecting with students, and enhancing communication and leadership skills.</p>
<div class="mt-3">
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">Leadership</span>
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">Communication</span>
</div>
</div>
</div>
<div class="col-md-4 reveal">
<div class="glass-card h-100 text-center">
<div style="font-size:60px;margin-bottom:20px;">👩‍💻</div>
<h4 style="color:#A78BFA;margin-bottom:15px;">Portfolio Website</h4>
<p style="color:#aaa;">A responsive personal portfolio website designed using HTML, CSS and Bootstrap with a modern user interface.</p>
<div class="mt-3">
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">HTML</span>
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">CSS</span>
<span style="background:rgba(124,58,237,0.2);color:#A78BFA;padding:4px 12px;border-radius:20px;font-size:12px;margin:3px;display:inline-block;">Bootstrap</span>
</div>
</div>
</div>
</div>
</div>
</section>

<section id="contact" class="py-5">
<div class="container">
<div class="text-center reveal">
<h2 class="section-title">Contact Me</h2>
<div class="section-divider"></div>
<p class="section-subtitle">Let's connect and build something amazing!</p>
</div>
<div class="row justify-content-center">
<div class="col-lg-7 reveal">
<div class="glass-card p-4">
<form>
<div class="mb-3"><input type="text" class="form-control form-control-glass" placeholder="✦ Your Name" required></div>
<div class="mb-3"><input type="email" class="form-control form-control-glass" placeholder="✦ Your Email" required></div>
<div class="mb-3"><textarea class="form-control form-control-glass" rows="5" placeholder="✦ Write your message..." required></textarea></div>
<button type="submit" class="btn btn-custom w-100 btn-lg"><i class="bi bi-send-fill me-2"></i> Send Message</button>
</form>
</div>
</div>
</div>
</div>
</section>

<footer>
<div class="container text-center">
<h2 class="fw-bold mb-2" style="background:linear-gradient(45deg,#7C3AED,#4F46E5);-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Karthika M</h2>
<p style="color:#aaa;margin-bottom:25px;">AIML Engineering Student | Frontend Developer | Web Developer</p>
<div class="social mb-4">
<a href="#"><i class="bi bi-github"></i></a>
<a href="#"><i class="bi bi-linkedin"></i></a>
<a href="#"><i class="bi bi-instagram"></i></a>
<a href="#"><i class="bi bi-facebook"></i></a>
<a href="mailto:karthika6870@gmail.com"><i class="bi bi-envelope-fill"></i></a>
</div>
<p style="color:#aaa;"><i class="bi bi-envelope-fill me-2" style="color:#7C3AED;"></i>karthika6870@gmail.com</p>
<p style="color:#aaa;"><i class="bi bi-telephone-fill me-2" style="color:#7C3AED;"></i>+91 7358298318</p>
<hr style="border-color:rgba(124,58,237,0.3);margin:25px 0;">
<p style="color:#666;">© 2026 Karthi. All Rights Reserved. Made with 🤍</p>
</div>
</footer>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
<script>

const canvas=document.getElementById('particles-canvas');
const ctx=canvas.getContext('2d');
canvas.width=window.innerWidth;canvas.height=window.innerHeight;
window.addEventListener('resize',()=>{canvas.width=window.innerWidth;canvas.height=window.innerHeight;});
const particles=[];
for(let i=0;i<80;i++){particles.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*2+0.5,dx:(Math.random()-0.5)*0.5,dy:(Math.random()-0.5)*0.5,alpha:Math.random()*0.5+0.2});}
function drawParticles(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles.forEach(p=>{ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);ctx.fillStyle=`rgba(124,58,237,${p.alpha})`;ctx.fill();p.x+=p.dx;p.y+=p.dy;if(p.x<0||p.x>canvas.width)p.dx*=-1;if(p.y<0||p.y>canvas.height)p.dy*=-1;});
  for(let i=0;i<particles.length;i++){for(let j=i+1;j<particles.length;j++){const dist=Math.hypot(particles[i].x-particles[j].x,particles[i].y-particles[j].y);if(dist<120){ctx.beginPath();ctx.moveTo(particles[i].x,particles[i].y);ctx.lineTo(particles[j].x,particles[j].y);ctx.strokeStyle=`rgba(124,58,237,${0.15*(1-dist/120)})`;ctx.lineWidth=0.5;ctx.stroke();}}}
  requestAnimationFrame(drawParticles);
}
drawParticles();

const roles=['Engineering Student','Frontend Developer','Web Developer','AIML Enthusiast'];
let ri=0,ci=0,deleting=false;
function typeRole(){
  const el=document.getElementById('typing-role');
  const current=roles[ri];
  if(!deleting){el.textContent=current.slice(0,ci+1);ci++;if(ci===current.length){deleting=true;setTimeout(typeRole,1500);return;}}
  else{el.textContent=current.slice(0,ci-1);ci--;if(ci===0){deleting=false;ri=(ri+1)%roles.length;}}
  setTimeout(typeRole,deleting?60:100);
}
typeRole();


const revealEls=document.querySelectorAll('.reveal');
const observer=new IntersectionObserver(entries=>{entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('active');});},{threshold:0.1});
revealEls.forEach(el=>observer.observe(el));


const backTop=document.getElementById('backTop');
window.addEventListener('scroll',()=>{backTop.style.display=window.scrollY>400?'flex':'none';});
</script>
</body>
</html>
