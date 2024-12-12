<script>
    import { onMount } from 'svelte';
  
    let html2pdf;
    
    onMount(async () => {
        const module = await import('html2pdf.js');
        html2pdf = module.default;
    });

    async function exportToPDF() {
        if (!html2pdf) return;
        
        const element = document.querySelector('.resume');
        const opt = {
        margin: 1,
        filename: 'resume-kate-zvereva.pdf',
        image: { type: 'jpeg', quality: 0.98 },
        html2canvas: { scale: 2 },
        jsPDF: { unit: 'cm', format: 'a4', orientation: 'portrait' }
        };

        await html2pdf().set(opt).from(element).save();
    }
    
    function getIcon(key) {
        const icons = {
            email: "📧",
            phone: "📱",
            location: "📍",
            instagram: "📸",
            behance: "🎨"
        };
        return icons[key] || "•";
    }

    const personalInfo = {
      name: "Екатерина Зверева",
      title: "Режиссер монтажа",
      contact: {
        email: "kate.zvereva@gmail.com",
        phone: "+7 (999) 123-45-67",
        location: "Москва",
        instagram: "@kate.editor",
        behance: "katezvereva"
      }
    };
  
    const skills = {
      technical: [
        { name: 'Adobe Premiere Pro', level: 95 },
        { name: 'DaVinci Resolve', level: 90 },
        { name: 'Final Cut Pro', level: 85 },
        { name: 'Adobe After Effects', level: 80 },
        { name: 'Adobe Audition', level: 75 },
        { name: 'Color Grading', level: 85 },
        { name: 'Sound Design', level: 80 }
      ],
      soft: [
        'Креативное мышление',
        'Работа в команде',
        'Управление проектами',
        'Внимание к деталям',
        'Работа в сжатые сроки'
      ]
    };

    const recommendations = [
        {
        name: "Андрей Петров",
        position: "Режиссер фильма «Лилия»",
        photo: "/images/petrov.jpg", // заглушка, нужно заменить на реальное фото
        quote: "Екатерина обладает исключительным чувством ритма и понимания драматургии. Её монтажные решения в фильме «Лилия» помогли создать именно то эмоциональное воздействие на зрителя, которого мы добивались.",
        contact: {
            email: "petrov@film.ru",
            phone: "+7 (999) XXX-XX-XX"
        }
        },
        {
        name: "Мария Соколова",
        position: "Режиссер фильма «ПВД»",
        photo: "/images/sokolova.jpg", // заглушка, нужно заменить на реальное фото
        quote: "Работа с Екатериной над «ПВД» была настоящим творческим союзом. Её способность чувствовать материал и предлагать неординарные монтажные решения сделала фильм гораздо глубже и интереснее.",
        contact: {
            email: "sokolova@film.ru",
            phone: "+7 (999) XXX-XX-XX"
        }
        }
    ];
  
    const portfolio = {
      films: [
        {
          title: 'Лилия',
          type: 'Короткометражный фильм',
          role: 'Режиссер монтажа',
          duration: '15 мин',
          year: '2023',
          description: 'Драматическая история о поиске себя. Участник фестиваля молодого кино.',
          preview: 'lilia-preview.jpg'
        },
        {
          title: 'ПВД',
          type: 'Короткометражный фильм',
          role: 'Режиссер монтажа',
          duration: '20 мин',
          year: '2023',
          description: 'Экспериментальное роуд-муви. Победитель в номинации "Лучший монтаж".',
          preview: 'pvd-preview.jpg'
        }
      ],
      digital: {
        reels: [
          {
            client: 'Fashion Brand X',
            views: '1.2M',
            engagement: '12%'
          },
          {
            client: 'Beauty Brand Y',
            views: '800K',
            engagement: '15%'
          }
        ],
        youtube: [
          {
            channel: 'Travel Vlog',
            subscribers: '500K',
            videos: 24
          },
          {
            channel: 'Cooking Show',
            subscribers: '300K',
            videos: 18
          }
        ]
      }
    };
  
    const education = [
      {
        school: 'Школа кино "Индустрия"',
        course: 'Режиссер видеомонтажа',
        year: '2022-2023',
        achievements: ['Диплом с отличием', 'Отлично за выпускной проект']
      },
    ];
  
    const awards = [
      {
        title: 'Молодой монтажер года',
        organization: 'Young Editors Award',
        year: '2023'
      },
      {
        title: 'Лучший монтаж',
        organization: 'Фестиваль студенческого кино',
        year: '2023',
        project: 'ПВД'
      }
    ];

    const tools = [
        {
        icon: "🎬",
        name: "Adobe Premiere Pro",
        expertise: 95,
        description: "Основной инструмент для монтажа, глубокое знание всех аспектов работы"
        },
        {
        icon: "🎨",
        name: "DaVinci Resolve",
        expertise: 90,
        description: "Профессиональная цветокоррекция и грейдинг"
        },
        {
        icon: "🎵",
        name: "Adobe Audition",
        expertise: 85,
        description: "Работа со звуком, создание звуковых ландшафтов"
        },
        {
        icon: "✨",
        name: "After Effects",
        expertise: 80,
        description: "Создание визуальных эффектов и анимации"
        }
    ];

    const genres = [
        {
        icon: "🎭",
        name: "Драматическое кино",
        description: "Создание эмоционального повествования через ритм и темп монтажа",
        examples: ["Лилия", "Короткий метр", "Социальные драмы"]
        },
        {
        icon: "📱",
        name: "Digital Content",
        description: "Динамичный монтаж для социальных сетей",
        examples: ["Reels", "YouTube", "TikTok"]
        },
        {
        icon: "🎬",
        name: "Рекламные ролики",
        description: "Создание запоминающихся коммерческих видео",
        examples: ["Бренд-контент", "Промо", "Презентации"]
        }
    ];

    const workflowSteps = [
        {
        title: "Погружение в материал",
        description: "Глубокий анализ отснятого материала, поиск ключевых моментов и эмоциональных точек"
        },
        {
        title: "Создание структуры",
        description: "Выстраивание драматургической линии, работа над ритмом и темпом повествования"
        },
        {
        title: "Техническая реализация",
        description: "Работа со звуком, цветокоррекция, визуальные эффекты"
        },
        {
        title: "Финальные штрихи",
        description: "Полировка деталей, создание особой атмосферы через тонкие монтажные решения"
        }
    ];
  
    const languages = [
      { name: 'Русский', level: 'Родной' },
      { name: 'Английский', level: 'B2 (Upper-Intermediate)' }
    ];
  
    const specializations = [
      'Нарративный монтаж',
      'Музыкальные клипы',
      'Рекламные ролики',
      'Документальное кино',
      'Fashion-видео'
    ];
  </script>
  
  <div class="export-button">
    <button on:click={exportToPDF}>
      <span class="icon">📥</span>
      Скачать PDF
    </button>
  </div>

  <div class="resume-container">
    <div class="resume">
      <!-- Header Section -->
      <header class="header">
        <div class="header-content">
          <h1>{personalInfo.name}</h1>
          <h2>{personalInfo.title}</h2>
          <div class="contact-info">
            {#each Object.entries(personalInfo.contact) as [key, value]}
              <div class="contact-item">
                <span class="icon">{getIcon(key)}</span>
                <span>{value}</span>
              </div>
            {/each}
          </div>
        </div>
        <div class="qr-code">
          <!-- QR код для портфолио -->
          <div class="qr-placeholder"></div>
          <span>QR код для портфолио</span>
        </div>
      </header>
  
      <!-- About Section -->
      <section class="about">
        <h3>О себе</h3>
        <p class="about-text">
          Креативный режиссер монтажа с опытом работы над разнообразными проектами: 
          от короткометражных фильмов до вирусных роликов. Специализируюсь на создании 
          динамичных визуальных историй с эмоциональным воздействием. Постоянно 
          развиваюсь и следую современным трендам в видеомонтаже.
        </p>
      </section>
  
      <!-- Portfolio Section -->
      <section class="portfolio">
        <h3>Портфолио</h3>
        <div class="portfolio-films">
          {#each portfolio.films as film}
            <div class="portfolio-item" style="background-image: url({film.preview})">
              <div class="portfolio-content">
                <h4>{film.title}</h4>
                <p class="type">{film.type}</p>
                <p class="description">{film.description}</p>
                <div class="meta">
                  <span>{film.duration}</span>
                  <span>{film.year}</span>
                </div>
              </div>
            </div>
          {/each}
        </div>
  
        <div class="portfolio-digital">
            <div class="digital-section">
              <h4>Digital Content</h4>
              <div class="digital-stats">
                <div class="stat">
                  <span class="number">2M+</span>
                  <span class="label">Общий охват</span>
                </div>
                <div class="stat">
                  <span class="number">42</span>
                  <span class="label">Проекта</span>
                </div>
                <div class="stat">
                  <span class="number">13.5%</span>
                  <span class="label">Engagement Rate</span>
                </div>
              </div>
              
              <!-- <div class="content-showcase">
                <div class="showcase-section">
                  <h5>Reels & Stories</h5>
                  <div class="project-grid">
                    <div class="project-card">
                      <div class="project-stats">
                        <span class="views">1.2M просмотров</span>
                        <span class="client">Fashion Brand X</span>
                      </div>
                      <div class="metrics">
                        <span>12% engagement</span>
                        <span>2.5K shares</span>
                      </div>
                    </div>
                    <div class="project-card">
                      <div class="project-stats">
                        <span class="views">800K просмотров</span>
                        <span class="client">Beauty Brand Y</span>
                      </div>
                      <div class="metrics">
                        <span>15% engagement</span>
                        <span>1.8K shares</span>
                      </div>
                    </div>
                  </div>
                </div>
          
                <div class="showcase-section">
                  <h5>YouTube</h5>
                  <div class="project-grid">
                    <div class="project-card">
                      <div class="project-stats">
                        <span class="channel">Travel Vlog</span>
                        <span class="numbers">500K подписчиков</span>
                      </div>
                      <div class="metrics">
                        <span>24 видео</span>
                        <span>Avg. 85K просмотров</span>
                      </div>
                    </div>
                    <div class="project-card">
                      <div class="project-stats">
                        <span class="channel">Cooking Show</span>
                        <span class="numbers">300K подписчиков</span>
                      </div>
                      <div class="metrics">
                        <span>18 видео</span>
                        <span>Avg. 50K просмотров</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div> -->
          </div>
      </section>
      
      <!-- Specialization Section -->
      <section class="specialization">
        <h3>Специализация и жанры</h3>
        <div class="genres-grid">
          {#each genres as genre}
            <div class="genre-card">
              <div class="genre-icon">{genre.icon}</div>
              <h4>{genre.name}</h4>
              <p>{genre.description}</p>
              <div class="genre-examples">
                {#each genre.examples as example}
                  <span class="example-tag">{example}</span>
                {/each}
              </div>
            </div>
          {/each}
        </div>
      </section>
      

      <!-- Skills Section -->
      <section class="tools">
        <h3>Навыки и инструменты</h3>
        <div class="tools-grid">
          {#each tools as tool}
            <div class="tool-card">
              <div class="tool-icon">{tool.icon}</div>
              <div class="tool-info">
                <h4>{tool.name}</h4>
                <div class="expertise-bar">
                  <div class="expertise-level" style="width: {tool.expertise}%"></div>
                </div>
                <p>{tool.description}</p>
              </div>
            </div>
          {/each}
        </div>
        <div class="skills-soft">
            <h4>Soft Skills</h4>
            <div class="soft-skills-grid">
              {#each skills.soft as skill}
                <div class="soft-skill">{skill}</div>
              {/each}
            </div>
          </div>
      </section>

      <!-- <section class="skills">
        <h3>Навыки</h3>
        <div class="skills-technical">
          {#each skills.technical as skill}
            <div class="skill-item">
              <span class="skill-name">{skill.name}</span>
              <div class="skill-bar">
                <div class="skill-level" style="width: {skill.level}%"></div>
              </div>
            </div>
          {/each}
        </div>
  
        <div class="skills-soft">
          <h4>Soft Skills</h4>
          <div class="soft-skills-grid">
            {#each skills.soft as skill}
              <div class="soft-skill">{skill}</div>
            {/each}
          </div>
        </div>
      </section> -->

      
  
    <!-- Education Section -->
    <section class="education">
        <h3>Образование</h3>
        {#each education as edu}
        <div class="education-item">
            <h4>{edu.school}</h4>
            <p class="course">{edu.course}</p>
            <p class="year">{edu.year}</p>
            <ul class="achievements">
            {#each edu.achievements as achievement}
                <li>{achievement}</li>
            {/each}
            </ul>
        </div>
        {/each}
    </section>

      <!-- Recommendations -->
      <section class="recommendations">
        <h2>Рекомендации</h2>
        <div class="recommendations-grid">
          {#each recommendations as rec}
            <div class="recommendation-card">
              <div class="quote-mark">❝</div>
              <div class="rec-quote">{rec.quote}</div>
              <div class="rec-footer">
                <div class="rec-author">
                  <div class="author-photo" style="background-image: url({rec.photo})">
                    <div class="author-photo-placeholder">{rec.name[0]}</div>
                  </div>
                  <div class="author-info">
                    <span class="author-name">{rec.name}</span>
                    <span class="author-position">{rec.position}</span>
                  </div>
                </div>
                <div class="rec-contacts">
                  <div class="contact-item">
                    <span class="icon">📧</span>
                    <span>{rec.contact.email}</span>
                  </div>
                  <div class="contact-item">
                    <span class="icon">📱</span>
                    <span>{rec.contact.phone}</span>
                  </div>
                </div>
              </div>
            </div>
          {/each}
        </div>
      </section>
      
      <section class="workflow">
        <h3>Мой творческий процесс</h3>
        <div class="workflow-timeline">
          {#each workflowSteps as step, i}
            <div class="workflow-step">
              <div class="step-number">{i + 1}</div>
              <div class="step-content">
                <h4>{step.title}</h4>
                <p>{step.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </section>
  
      <!-- Additional Info -->
      <section class="additional-info">
        <div class="languages">
          <h3>Языки</h3>
          {#each languages as lang}
            <div class="language-item">
              <span class="lang-name">{lang.name}</span>
              <span class="lang-level">{lang.level}</span>
            </div>
          {/each}
        </div>
  
        <div class="specializations">
          <h3>Специализация</h3>
          <div class="spec-grid">
            {#each specializations as spec}
              <div class="spec-item">{spec}</div>
            {/each}
          </div>
        </div>
      </section>
    </div>
  </div>
  
  <style>
    :global(body) {
      background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
      margin: 0;
      padding: 20px;
      font-family: 'Roboto', sans-serif;
    }

    .export-button {
      position: fixed;
      top: 20px;
      right: 20px;
      z-index: 1000;
    }

    button {
      background: linear-gradient(135deg, #3498db, #2980b9);
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 30px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
    }

    button:active {
      transform: translateY(0);
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .icon {
      font-size: 20px;
    }

    @media print {
      .export-button {
        display: none;
      }
    }
    
    .specialization {
        /* padding: 2rem; */
    }

    .genres-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 1.5rem;
        margin-top: 1.5rem;
    }

    .genre-card {
        background: linear-gradient(145deg, #ffffff, #f5f5f5);
        border-radius: 15px;
        padding: 1.5rem;
        text-align: center;
        transition: all 0.3s ease;
    }

    .genre-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 20px rgba(0,0,0,0.1);
    }

    .genre-icon {
        font-size: 2.5rem;
        margin-bottom: 1rem;
    }

    .genre-examples {
        display: flex;
        flex-wrap: wrap;
        gap: 0.5rem;
        justify-content: center;
        margin-top: 1rem;
    }

    .example-tag {
        background: rgba(52, 152, 219, 0.1);
        color: #3498db;
        padding: 0.3rem 0.8rem;
        border-radius: 15px;
        font-size: 0.9rem;
    }

    .tools {
        /* padding: 2rem; */
    }

    .tools-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 1.5rem;
        margin-top: 1.5rem;
    }

    .tool-card {
        background: white;
        border-radius: 15px;
        padding: 1.5rem;
        display: flex;
        align-items: flex-start;
        gap: 1rem;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        transition: transform 0.3s ease;
    }

    .tool-card:hover {
        transform: translateY(-5px);
    }

    .tool-icon {
        font-size: 2rem;
        background: #f8f9fa;
        padding: 1rem;
        border-radius: 12px;
    }

    .tool-info {
        flex: 1;
    }

    .expertise-bar {
        height: 6px;
        background: #ecf0f1;
        border-radius: 3px;
        margin: 0.5rem 0;
        overflow: hidden;
    }

    .expertise-level {
        height: 100%;
        background: linear-gradient(90deg, #3498db, #2ecc71);
        border-radius: 3px;
    }

    .workflow {
        padding: 2rem;
        background: linear-gradient(145deg, #ffffff, #f5f5f5);
        border-radius: 20px;
        margin: 2rem 0;
    }

    .workflow-timeline {
        position: relative;
        padding: 2rem 0;
    }

    .workflow-timeline::before {
        content: '';
        position: absolute;
        left: 2rem;
        top: 0;
        bottom: 0;
        width: 2px;
        background: linear-gradient(to bottom, #3498db 0%, #e74c3c 100%);
    }

    .workflow-step {
        display: flex;
        align-items: flex-start;
        margin-bottom: 2rem;
        padding-left: 4rem;
        position: relative;
    }

    .step-number {
        position: absolute;
        left: 1rem;
        width: 2rem;
        height: 2rem;
        background: #fff;
        border: 2px solid #3498db;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: bold;
        color: #3498db;
        transform: translateX(-50%);
    }

    .step-content {
        background: white;
        padding: 1.5rem;
        border-radius: 12px;
        box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        width: 100%;
    }

    .step-content h4 {
        color: #2c3e50;
        margin: 0 0 0.5rem;
    }

    .step-content p {
        color: #7f8c8d;
        margin: 0;
        line-height: 1.5;
    }

    .digital-section {
        background: linear-gradient(145deg, #ffffff, #f5f5f5);
        border-radius: 20px;
        padding: 2rem;
        margin-top: 2rem;
    }

    .content-showcase {
        margin-top: 2rem;
    }

    .showcase-section {
        margin-top: 1.5rem;
    }

    .showcase-section h5 {
        color: #2c3e50;
        font-size: 1.1rem;
        margin-bottom: 1rem;
    }

    .project-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 1rem;
    }

    .project-card {
        background: rgba(255,255,255,0.8);
        padding: 1.2rem;
        border-radius: 12px;
        border: 1px solid rgba(52, 152, 219, 0.2);
        transition: all 0.3s ease;
    }

    .project-card:hover {
        transform: translateY(-3px);
        box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }

    .project-stats {
        display: flex;
        justify-content: space-between;
        margin-bottom: 0.8rem;
        font-weight: 600;
    }

    .metrics {
        display: flex;
        justify-content: space-between;
        color: #7f8c8d;
        font-size: 0.9rem;
    }

    .views, .channel {
        color: #3498db;
    }

    .client, .numbers {
        color: #34495e;
    }
  
    .resume-container {
      max-width: 21cm;
      margin: 0 auto;
      background: white;
      box-shadow: 0 0 20px rgba(0,0,0,0.1);
      border-radius: 8px;
      overflow: hidden;
    }
  
    .resume {
      padding: 40px;
    }
  
    .header {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 40px;
    }
  
    .header-content h1 {
      font-size: 2.5em;
      color: #2c3e50;
      margin: 0;
    }
  
    .header-content h2 {
      font-size: 1.5em;
      color: #34495e;
      margin: 5px 0 15px;
    }
  
    .contact-info {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }
  
    .contact-item {
      display: flex;
      align-items: center;
      gap: 5px;
      font-size: 0.9em;
      color: #7f8c8d;
    }
  
    .qr-code {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  
    .qr-placeholder {
      width: 100px;
      height: 100px;
      background: #ecf0f1;
      border-radius: 8px;
    }
  
    section {
      margin-bottom: 40px;
    }
  
    h3 {
      color: #2980b9;
      border-bottom: 2px solid #3498db;
      padding-bottom: 10px;
      margin-bottom: 20px;
    }
  
    .about-text {
      font-size: 1em;
      line-height: 1.6;
      color: #34495e;
    }
  
    .portfolio-films {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }
  
    .portfolio-item {
      background-size: cover;
      background-position: center;
      height: 200px;
      border-radius: 8px;
      overflow: hidden;
      position: relative;
    }
  
    .portfolio-content {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: rgba(0,0,0,0.7);
      color: white;
      padding: 15px;
      /* transform: translateY(100%); */
      transition: transform 0.3s ease;
    }
  
    .portfolio-item:hover .portfolio-content {
      transform: translateY(0);
    }
  
    .portfolio-content h4 {
      margin: 0 0 5px;
    }
  
    .portfolio-content .type {
      font-size: 0.8em;
      opacity: 0.8;
    }
  
    .portfolio-content .description {
      font-size: 0.9em;
      margin: 10px 0;
    }
  
    .portfolio-content .meta {
      display: flex;
      justify-content: space-between;
      font-size: 0.8em;
      opacity: 0.8;
    }
  
    .digital-section {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      padding: 30px 20px;
      border-radius: 8px;
      margin-top: 20px;
    }

    .digital-section h4 {
        margin-top: 0;
    }
  
    .digital-stats {
      display: flex;
      justify-content: space-around;
      text-align: center;
    }
  
    .stat .number {
      font-size: 1.5em;
      font-weight: bold;
      display: block;
    }
  
    .stat .label {
      font-size: 0.8em;
      opacity: 0.8;
    }
  
    .skills-technical {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
    }
  
    .skill-item {
      background: #ecf0f1;
      padding: 10px;
      border-radius: 5px;
    }
  
    .skill-name {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }
  
    .skill-bar {
      height: 10px;
      background: #bdc3c7;
      border-radius: 5px;
      overflow: hidden;
    }
  
    .skill-level {
      height: 100%;
      background: linear-gradient(90deg, #3498db, #2980b9);
    }
  
    .soft-skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }
  
    .soft-skill {
      background: #3498db;
      color: white;
      padding: 5px 10px;
      border-radius: 15px;
      font-size: 0.9em;
    }
  
    .education {
        margin-bottom: 2rem;
    }

    .education h3 {
        font-size: 1.8rem;
        color: #2c3e50;
        margin-bottom: 1.5rem;
    }

    .education-item {
        background: linear-gradient(145deg, #ffffff, #f5f5f5);
        border-radius: 15px;
        padding: 1.5rem;
        margin-bottom: 1.5rem;
        box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        transition: all 0.3s ease;
    }

    .education-item:hover {
        transform: translateY(-3px);
        box-shadow: 0 8px 20px rgba(0,0,0,0.1);
    }

    .education-item h4 {
        font-size: 1.3rem;
        color: #3498db;
        margin: 0 0 0.5rem;
    }

    .course {
        font-size: 1.1rem;
        color: #34495e;
        margin-bottom: 0.5rem;
    }

    .year {
        font-size: 0.9rem;
        color: #7f8c8d;
        margin-bottom: 1rem;
    }

    .achievements {
        list-style-type: none;
        padding-left: 0;
    }

    .achievements li {
        position: relative;
        padding-left: 1.5rem;
        margin-bottom: 0.5rem;
        color: #34495e;
    }

    .achievements li::before {
        content: '✓';
        position: absolute;
        left: 0;
        color: #3498db;
        font-weight: bold;
    }
  
    .course, .year {
      font-size: 0.9em;
      color: #7f8c8d;
    }
  
    .achievements {
      margin: 10px 0 0;
      padding-left: 20px;
      font-size: 0.9em;
    }
  
    .additional-info {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }
  
    .language-item, .spec-item {
      background: #ecf0f1;
      padding: 10px;
      border-radius: 5px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
    }
  
    .spec-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 10px;
    }

    .recommendations {
    margin: 3rem 0;
  }

  .recommendations h2 {
    font-size: 1.8rem;
    color: #2c3e50;
    margin-bottom: 2rem;
    text-align: center;
  }

  .recommendations-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: 2rem;
    padding: 1rem;
  }

  .recommendation-card {
    position: relative;
    background: linear-gradient(145deg, #ffffff, #f5f5f5);
    border-radius: 20px;
    padding: 2rem;
    box-shadow: 
      0 10px 20px rgba(0,0,0,0.05),
      0 6px 6px rgba(0,0,0,0.1);
    transition: all 0.3s ease;
  }

  .recommendation-card:hover {
    transform: translateY(-5px);
    box-shadow: 
      0 15px 30px rgba(0,0,0,0.1),
      0 10px 10px rgba(0,0,0,0.05);
  }

  .quote-mark {
    position: absolute;
    top: -20px;
    left: 20px;
    font-size: 6rem;
    color: #3498db;
    opacity: 0.1;
    font-family: Georgia, serif;
  }

  .rec-quote {
    font-size: 1rem;
    line-height: 1.6;
    color: #34495e;
    margin-bottom: 2rem;
    position: relative;
    font-style: italic;
  }

  .rec-footer {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    border-top: 1px solid rgba(52, 152, 219, 0.2);
    padding-top: 1rem;
  }

  .rec-author {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .author-photo {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background-size: cover;
    background-position: center;
    position: relative;
    border: 3px solid #3498db;
  }

  .author-photo-placeholder {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #3498db;
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
    border-radius: 50%;
  }

  .author-info {
    display: flex;
    flex-direction: column;
  }

  .author-name {
    font-weight: 600;
    color: #2c3e50;
    font-size: 1.1rem;
  }

  .author-position {
    color: #7f8c8d;
    font-size: 0.9rem;
  }

  .rec-contacts {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #34495e;
    font-size: 0.9rem;
  }

  .icon {
    color: #3498db;
  }

  @media (max-width: 768px) {
    .recommendations-grid {
      grid-template-columns: 1fr;
    }

    .recommendation-card {
      padding: 1.5rem;
    }
  }

  @media print {
    .recommendations-grid {
      display: block;
    }

    .recommendation-card {
      page-break-inside: avoid;
      margin-bottom: 2rem;
    }
  }
  
    @media (max-width: 768px) {
      .resume {
        padding: 20px;
      }
  
      .header, .education-awards, .additional-info {
        flex-direction: column;
      }
  
      .qr-code {
        margin-top: 20px;
      }
  
      .portfolio-films {
        grid-template-columns: 1fr;
      }
  
      .skills-technical, .education-awards, .additional-info {
        grid-template-columns: 1fr;
      }
    }
  </style>
  