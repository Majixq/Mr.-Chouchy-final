// Create floating particles
function createParticles() {
  const particles = document.querySelector('.particles');
  for (let i = 0; i < 50; i++) {
    const particle = document.createElement('div');
    particle.className = 'particle';
    particle.style.left = Math.random() * 100 + '%';
    particle.style.top = Math.random() * 100 + '%';
    particle.style.animationDelay = Math.random() * 6 + 's';
    particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
    particles.appendChild(particle);
  }
}

// Load project cards dynamically
function loadProjects() {
  const projects = [
    {
      title: "Portfolio Website",
      description: "Website ສ່ວນຕົວທີ່ສວຍງາມ ແລະ ຕອບສະໜອງໄດ້ ສ້າງດ້ວຍ HTML, CSS, JS",
      icon: "fas fa-globe",
      gradient: "linear-gradient(45deg, #ff6b6b, #4ecdc4)",
      link: "#"
    }
  ];

  const projectList = document.getElementById("project-list");
  projectList.innerHTML = '';

  projects.forEach((project, index) => {
    const col = document.createElement("div");
    col.className = "col-md-6 col-lg-4 animate-zoom-in";
    col.style.animationDelay = (index * 0.1) + 's';
    col.innerHTML = `
      <div class="card project-card h-100">
        <div class="project-image" style="background: ${project.gradient};">
          <i class="${project.icon}"></i>
        </div>
        <div class="card-body d-flex flex-column">
          <h5 class="card-title">
            <i class="fas fa-star" style="color: #ffd700; margin-right: 8px;"></i>
            ${project.title}
          </h5>
          <p class="card-text">${project.description}</p>
          <div class="mt-auto pt-3">
            <a href="${project.link}" class="btn btn-project" target="_blank" rel="noopener noreferrer">
              <i class="fas fa-external-link-alt"></i> ดูโปรเจกต์
            </a>
          </div>
        </div>
      </div>
    `;
    projectList.appendChild(col);
  });
}

function handleProfileImageError() {
  const profileImage = document.getElementById('profileImage');
  const parentContainer = profileImage.parentElement;
  profileImage.style.display = 'none';

  const fallbackIcon = document.createElement('i');
  fallbackIcon.className = 'fas fa-user';
  parentContainer.appendChild(fallbackIcon);
  console.warn('Profile image failed to load. Displaying fallback icon.');
}

// Init logic when DOM ready
window.addEventListener('DOMContentLoaded', () => {
  createParticles();
  loadProjects();

  const sections = document.querySelectorAll('section, header#top');
  const navLinks = document.querySelectorAll('.navbar-nav .nav-link');

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        navLinks.forEach(link => {
          link.classList.remove('active');
          if (link.getAttribute('href') === `#${entry.target.id}`) {
            link.classList.add('active');
          }
        });
      }
    });
  }, {
    root: null,
    rootMargin: '-50% 0px -49% 0px',
    threshold: 0
  });

  sections.forEach(section => observer.observe(section));

  const profileImage = document.getElementById('profileImage');
  if (profileImage) profileImage.addEventListener('error', handleProfileImageError);

  // Smooth scroll on nav click
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', e => {
      e.preventDefault();
      const targetId = anchor.getAttribute('href');
      const target = document.querySelector(targetId);
      const navHeight = document.querySelector('.navbar').offsetHeight;

      if (target) {
        window.scrollTo({
          top: target.offsetTop - navHeight - 20,
          behavior: 'smooth'
        });
        navLinks.forEach(link => link.classList.remove('active'));
        anchor.classList.add('active');
      }
    });
  });

  // Form validation
  const forms = document.querySelectorAll('.needs-validation');
  Array.from(forms).forEach(form => {
    form.addEventListener('submit', event => {
      event.preventDefault();
      event.stopPropagation();
      if (form.checkValidity()) {
        alert('ขอบคุณที่ติดต่อมาครับ! ผมจะติดต่อกลับไปโดยเร็ว ✨');
        form.reset();
        form.classList.remove('was-validated');
      }
      form.classList.add('was-validated');
    }, false);
  });
});
