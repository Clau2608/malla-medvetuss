<html class="light" lang="es"><head>
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>EduPath Academic | Malla Curricular Veterinaria</title>
<script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&amp;display=swap" rel="stylesheet"/>
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet"/>
<script id="tailwind-config">
      tailwind.config = {
        darkMode: "class",
        theme: {
          extend: {
            "colors": {
                    "on-secondary-fixed": "#00210f",
                    "primary-container": "#1a5f7a",
                    "surface-container-highest": "#d3e4fe",
                    "inverse-surface": "#213145",
                    "on-surface": "#0b1c30",
                    "surface-container-lowest": "#ffffff",
                    "surface": "#f8f9ff",
                    "primary-fixed-dim": "#92cfee",
                    "outline-variant": "#c0c8cd",
                    "on-tertiary": "#ffffff",
                    "secondary-fixed": "#9af6b8",
                    "surface-tint": "#236580",
                    "secondary-container": "#97f3b5",
                    "tertiary-container": "#7d4e00",
                    "surface-container-low": "#eff4ff",
                    "surface-container": "#e5eeff",
                    "primary": "#00475e",
                    "secondary": "#006d3d",
                    "on-secondary-container": "#057240",
                    "surface-dim": "#cbdbf5",
                    "on-tertiary-fixed": "#2a1700",
                    "on-primary-fixed-variant": "#004d66",
                    "inverse-primary": "#92cfee",
                    "primary-fixed": "#c0e8ff",
                    "on-surface-variant": "#40484d",
                    "secondary-fixed-dim": "#7ed99e",
                    "error": "#ba1a1a",
                    "on-secondary": "#ffffff",
                    "on-error": "#ffffff",
                    "on-secondary-fixed-variant": "#00522d",
                    "tertiary": "#5d3900",
                    "surface-bright": "#f8f9ff",
                    "outline": "#70787d",
                    "tertiary-fixed": "#ffddb8",
                    "on-primary-container": "#9bd7f7",
                    "on-primary": "#ffffff",
                    "error-container": "#ffdad6",
                    "background": "#f8f9ff",
                    "on-background": "#0b1c30",
                    "on-error-container": "#93000a",
                    "surface-container-high": "#dce9ff",
                    "on-tertiary-container": "#ffc47d",
                    "inverse-on-surface": "#eaf1ff"
            },
            "borderRadius": {
                    "DEFAULT": "0.125rem",
                    "lg": "0.25rem",
                    "xl": "0.5rem",
                    "full": "0.75rem"
            },
            "spacing": {
                    "unit": "4px",
                    "margin-page": "320px",
                    "card-padding": "12px",
                    "gutter": "16px",
                    "column-width-min": "32px"
            },
            "fontFamily": {
                    "display": ["Inter"],
                    "body-base": ["Inter"]
            }
          },
        },
      }
    </script>
<style>
        .material-symbols-outlined {
            font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 20;
            display: inline-block;
            vertical-align: middle;
        }
        .semester-scroll {
            scrollbar-width: thin;
            scrollbar-color: #c0c8cd transparent;
        }
        .semester-scroll::-webkit-scrollbar {
            height: 10px;
        }
        .semester-scroll::-webkit-scrollbar-thumb {
            background-color: #c0c8cd;
            border-radius: 10px;
        }
        
        .course-card {
            transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
            user-select: none;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(0,0,0,0.1);
            min-height: 84px;
            z-index: 20;
        }

        .course-card.locked { 
            background-color: #BDBDBD !important;
            color: #000000 !important;
            opacity: 0.7;
            cursor: not-allowed;
        }
        .course-card.available { 
            background-color: #949494 !important;
            color: #F4F4F4 !important;
            cursor: pointer;
        }
        .course-card.enrolled { 
            background-color: #102B42 !important;
            color: #ffffff !important;
            cursor: pointer;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        .course-card.approved { 
            background-color: #CFB479 !important;
            color: #000000 !important;
            cursor: pointer;
            border-color: rgba(0,0,0,0.2);
        }

        .course-card:hover:not(.locked) {
            transform: translateY(-2px);
            filter: brightness(1.05);
            z-index: 40;
        }

        #connections-svg {
            pointer-events: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 10;
        }
        .connection-line {
            fill: none;
            stroke: #000000;
            stroke-width: 1.5;
            transition: opacity 0.3s ease;
            stroke-linecap: round;
            stroke-linejoin: round;
            opacity: 0.25;
        }
        .connection-line.active {
            opacity: 1;
            stroke-width: 2;
        }

        .tab-active {
            border-bottom: 3px solid #236580;
            color: #236580;
            font-weight: 700;
        }

        .semester-column {
            display: flex;
            flex-direction: column;
            gap: 48px;
        }
    </style>
</head>
<body class="bg-[#f0f4f8] text-on-background min-h-screen flex flex-col font-body-base">
<header class="sticky top-0 z-50 flex flex-col md:flex-row justify-between items-center w-full px-margin-page py-3 bg-primary text-on-primary shadow-lg">
<div class="flex items-center gap-3 mb-2 md:mb-0">
<img alt="Logo" class="h-10 w-10 rounded-full object-cover border border-white/20 shadow-sm" src="https://lh3.googleusercontent.com/aida-public/AB6AXuBiE3Tuh02g_etutTG-Mt3FUHpGSssu1soHenaDp7DZwX54EFZJHO2p_h-BiF5XO3yuVcP8wGPCczlAl4PBo6IdNS0mrec52MnJA-hHmXBI_bg8hiSFrWFenKgViv41-kf9oQramIwRM89yrkcPbTG8DqM4BZAPHpDYRlGLJF4H3rone325dXN3qmsb8bZlVXP3Qh28CQocECHhMUOVg9Elbsv9aIEPeKraxmfvxZhIqlGAfFq_DfXnu47bxnD82QcUmQQ"/>
<span class="font-display text-xl font-bold tracking-tight">Claudia Garcia González / Lilith psique</span>
</div>
<div class="flex flex-wrap justify-center gap-6 text-[10px] font-bold uppercase tracking-wider items-center">
<div class="flex items-center gap-2">
<span class="w-3 h-3 rounded-sm bg-[#BDBDBD] border border-black/10"></span>
<span>Bloqueado</span>
</div>
<div class="flex items-center gap-2">
<span class="w-3 h-3 rounded-sm bg-[#949494] border border-black/10"></span>
<span>Disponible</span>
</div>
<div class="flex items-center gap-2">
<span class="w-3 h-3 rounded-sm bg-[#102B42] border border-white/20"></span>
<span>Inscrito</span>
</div>
<div class="flex items-center gap-2">
<span class="w-3 h-3 rounded-sm bg-[#CFB479] border border-black/10"></span>
<span>Aprobado</span>
</div>
</div>
</header>
<main class="flex-1 w-full max-w-none overflow-x-hidden flex flex-col p-6 md:p-10 relative">
<div class="mb-10 w-full">
<div class="flex flex-col lg:flex-row justify-between items-start lg:items-center gap-6 mb-8">
<div>
<h1 class="text-4xl font-extrabold text-primary mb-1 tracking-tight">Medicina Veterinaria</h1>
<p class="text-on-surface-variant font-medium">Malla Curricular Plan de Estudios 2025 • Universidad San Sebastián</p>
</div>
<div class="bg-white p-5 rounded-2xl shadow-xl border border-outline-variant min-w-[320px]">
<div class="flex justify-between items-end mb-3">
<div>
<span class="text-xs font-bold text-on-surface-variant block uppercase opacity-70">Progreso Académico</span>
<span class="text-3xl font-black text-primary" id="progress-text">0%</span>
</div>
<div class="text-right">
<span class="text-lg font-bold text-secondary" id="credits-total">0 / 300</span>
<span class="text-[10px] font-bold text-on-surface-variant block uppercase opacity-70">Créditos SCT</span>
</div>
</div>
<div class="w-full h-3 bg-surface-container rounded-full overflow-hidden border border-outline-variant/30">
<div class="h-full bg-secondary transition-all duration-1000" id="progress-bar" style="width: 0%;"></div>
</div>
</div>
</div>
<div class="flex items-center gap-4 border-b border-outline-variant overflow-x-auto pb-0" id="path-tabs">
<span class="text-[11px] font-black text-primary uppercase tracking-widest px-2 whitespace-nowrap">Vía de Titulación:</span>
<button class="px-6 py-3 text-sm transition-all whitespace-nowrap tab-active" data-path="tesina">Vía C: Tesina</button>
<button class="px-6 py-3 text-sm transition-all hover:text-primary whitespace-nowrap text-on-surface-variant" data-path="practica">Vía A: Práctica Avanzada</button>
<button class="px-6 py-3 text-sm transition-all hover:text-primary whitespace-nowrap text-on-surface-variant" data-path="clinico">Vía B: Internado Clínico</button>
</div>
</div>
<!-- Container for curriculum -->
<div class="relative w-full pb-20 pt-4 overflow-x-auto semester-scroll">
<svg id="connections-svg">
<defs>
<marker id="arrowhead" markerheight="6" markerwidth="6" orient="auto" refx="5" refy="3">
<path d="M0,0 L6,3 L0,6 Z" fill="#000000"></path>
</marker>
</defs>
</svg>
<!-- Full-width flex container for semesters -->
<div class="flex min-w-full items-start relative z-20 gap-16 lg:gap-24 xl:gap-32 px-4" id="curriculum-container">
<!-- Content dynamically rendered here -->
</div>
</div>
</main>
<script>
    const curriculumData = [
        {
            sem: 1, courses: [
                { id: 'MEVE_AA01', name: 'Introducción a la Medicina Veterinaria', credits: 5, area: 'basic', prereqs: [] },
                { id: 'DBIO_1084', name: 'Biología Celular', credits: 5, area: 'basic', prereqs: [] },
                { id: 'FORI_0001', name: 'Antropología', credits: 3, area: 'general', prereqs: [] },
                { id: 'MEVE_AA02', name: 'Conservación Silvestre', credits: 5, area: 'basic', prereqs: [] },
                { id: 'MEVE_AA03', name: 'Zoología Vet', credits: 5, area: 'basic', prereqs: [] },
                { id: 'DQUI_1050', name: 'Química Gral', credits: 7, area: 'basic', prereqs: [] }
            ]
        },
        {
            sem: 2, courses: [
                { id: 'MEVE_BA01', name: 'Embrio-Histología', credits: 6, area: 'basic', prereqs: ['MEVE_AA01'] },
                { id: 'MEVE_BA02', name: 'Bioquímica', credits: 5, area: 'basic', prereqs: ['DQUI_1050', 'DBIO_1084'] },
                { id: 'FORI_0002', name: 'Ética', credits: 3, area: 'general', prereqs: ['FORI_0001'] },
                { id: 'MEVE_BA03', name: 'Anatomía Vet Gral', credits: 5, area: 'basic', prereqs: ['MEVE_AA03'] },
                { id: 'DCEX_0027', name: 'Física Médica', credits: 7, area: 'basic', prereqs: [] },
                { id: 'MEVE_BB01', name: 'Una Salud', credits: 4, area: 'public-health', prereqs: ['MEVE_AA01'] }
            ]
        },
        {
            sem: 3, courses: [
                { id: 'MEVE_CA01', name: 'Inmunología Veterinaria', credits: 5, area: 'pathology', prereqs: ['MEVE_BA01'] },
                { id: 'MEVE_CA02', name: 'Fisiología Vet', credits: 6, area: 'basic', prereqs: ['MEVE_BA02', 'DCEX_0027'] },
                { id: 'MEVE_CA03', name: 'Microbiología', credits: 6, area: 'pathology', prereqs: ['DBIO_1084'] },
                { id: 'MEVE_CA04', name: 'Reprod y Mejoramiento', credits: 5, area: 'production', prereqs: ['MEVE_BA02', 'MEVE_BA03'] },
                { id: 'MEVE_CA05', name: 'Anatomía Comparada', credits: 4, area: 'basic', prereqs: ['MEVE_BA03'] },
                { id: 'ELECDGEE01', name: 'Gestión Personal', credits: 4, area: 'management', prereqs: [] }
            ]
        },
        {
            sem: 4, courses: [
                { id: 'MEVE_DB01', name: 'Fisiopatología', credits: 4, area: 'pathology', prereqs: ['MEVE_CA02'] },
                { id: 'MEVE_DA02', name: 'Enfermedades Inf.', credits: 4, area: 'clinical', prereqs: ['MEVE_CA03', 'MEVE_CA01'] },
                { id: 'MEVE_DA03', name: 'Enf Parasitarias', credits: 5, area: 'clinical', prereqs: ['MEVE_CA03'] },
                { id: 'MEVE_DA04', name: 'Gineco-Obstetricia', credits: 6, area: 'clinical', prereqs: ['MEVE_CA04'] },
                { id: 'MEVE_DB02', name: 'Ecología', credits: 7, area: 'basic', prereqs: ['MEVE_AA02'] },
                { id: 'MEVE_DA05', name: 'Hito Evaluativo I', credits: 4, area: 'general', prereqs: ['MEVE_CA05', 'FORI_0002'] }
            ]
        },
        {
            sem: 5, courses: [
                { id: 'MEVE_EB01', name: 'Patología Gral', credits: 6, area: 'pathology', prereqs: ['MEVE_DB01'] },
                { id: 'MEVE_EB02', name: 'Farmacología', credits: 7, area: 'clinical', prereqs: ['MEVE_DB01'] },
                { id: 'MEVE_EA03', name: 'Nutrición', credits: 5, area: 'production', prereqs: ['MEVE_CA02'] },
                { id: 'MEVE_EB03', name: 'Metodología Inv', credits: 5, area: 'management', prereqs: ['ELECDGEE01'] },
                { id: 'MEVE_EB04', name: 'Emprendimiento', credits: 4, area: 'management', prereqs: [] },
                { id: 'FORI_0003', name: 'Persona y Sociedad', credits: 3, area: 'general', prereqs: ['FORI_0002'] }
            ]
        },
        {
            sem: 6, courses: [
                { id: 'MEVE_FA01', name: 'Patología Especial', credits: 6, area: 'pathology', prereqs: ['MEVE_EB01'] },
                { id: 'MEVE_FB01', name: 'Exploración Clínica', credits: 7, area: 'clinical', prereqs: ['MEVE_DB01'] },
                { id: 'MEVE_FA03', name: 'Bienestar Animal', credits: 4, area: 'clinical', prereqs: ['MEVE_BB01'] },
                { id: 'MEVE_FA04', name: 'Práctica Inicial', credits: 4, area: 'management', prereqs: ['MEVE_DA05'] },
                { id: 'MEVE_FB02', name: 'Patología Clínica', credits: 6, area: 'pathology', prereqs: ['MEVE_EB01'] },
                { id: 'ELECFORI01', name: 'Electivo I', credits: 3, area: 'general', prereqs: [] }
            ]
        },
        {
            sem: 7, courses: [
                { id: 'MEVE_GA01', name: 'Ganadería Rumiantes', credits: 5, area: 'production', prereqs: ['MEVE_EA03'] },
                { id: 'MEVE_GA02', name: 'Prod Monogástricos', credits: 5, area: 'production', prereqs: ['MEVE_EA03'] },
                { id: 'MEVE_GB01', name: 'Acuicultura', credits: 5, area: 'production', prereqs: ['MEVE_EA03'] },
                { id: 'MEVE_GA04', name: 'Cirugía Gral', credits: 5, area: 'clinical', prereqs: ['MEVE_FB01'] },
                { id: 'MEVE_GB02', name: 'Medicina Interna', credits: 7, area: 'clinical', prereqs: ['MEVE_FB01', 'MEVE_EB02'] },
                { id: 'ELECFORI02', name: 'Electivo II', credits: 3, area: 'general', prereqs: [] }
            ]
        },
        {
            sem: 8, courses: [
                { id: 'MEVE_HB01', name: 'Diagnóstico Imágenes', credits: 8, area: 'clinical', prereqs: ['MEVE_FB01'] },
                { id: 'MEVE_HA02', name: 'Ciencia de Datos', credits: 4, area: 'management', prereqs: ['MEVE_EB03'] },
                { id: 'MEVE_HB02', name: 'Cirugía Especial', credits: 5, area: 'clinical', prereqs: ['MEVE_GA04'] },
                { id: 'MEVE_HB03', name: 'Salud Pública', credits: 5, area: 'public-health', prereqs: ['MEVE_FA03'] },
                { id: 'MEVE_HA05', name: 'Práctica Interm.', credits: 4, area: 'management', prereqs: ['MEVE_FA04'] },
                { id: 'MEVE_HA06', name: 'Hito Evaluativo II', credits: 4, area: 'general', prereqs: ['MEVE_GA04', 'MEVE_GB02'] }
            ]
        },
        {
            sem: 9, courses: [
                { id: 'MEVE_IA01', name: 'Anim Mayores', credits: 4, area: 'clinical', prereqs: ['MEVE_GB02'] },
                { id: 'MEVE_IA02', name: 'Anim Menores', credits: 5, area: 'clinical', prereqs: ['MEVE_GB02'] },
                { id: 'MEVE_IA03', name: 'Inocuidad Alimentos', credits: 3, area: 'public-health', prereqs: ['MEVE_HB03'] },
                { id: 'MEVE_IA04', name: 'Clínica Silvestres', credits: 5, area: 'clinical', prereqs: ['MEVE_DB02', 'MEVE_GB02'] },
                { id: 'ELECFORI03', name: 'Electivo III', credits: 3, area: 'general', prereqs: [] },
                { id: 'MEVE_IB01', name: 'Internado Integr.', credits: 10, area: 'clinical', prereqs: ['MEVE_GB02', 'MEVE_HB02'] }
            ]
        },
        {
            sem: 10, courses: [
                { id: 'MEVE_JB03', name: 'Tesina', credits: 16, area: 'management', prereqs: ['MEVE_IB01'], path: 'tesina' },
                { id: 'MEVE_JB01', name: 'Práctica Avanzada', credits: 16, area: 'management', prereqs: ['MEVE_IB01'], path: 'practica' },
                { id: 'MEVE_JB02', name: 'Internado Clínico', credits: 16, area: 'clinical', prereqs: ['MEVE_IB01'], path: 'clinico' },
                { id: 'ELECDGEE03', name: 'Gestión de Carrera', credits: 4, area: 'management', prereqs: [] },
                { id: 'ELECMEVE01', name: 'Electivo IV', credits: 5, area: 'general', prereqs: [] },
                { id: 'ELECMEVE02', name: 'Electivo V', credits: 5, area: 'general', prereqs: [] }
            ]
        }
    ];

    let currentPath = 'tesina';
    const container = document.getElementById('curriculum-container');
    const svg = document.getElementById('connections-svg');
    const progressBar = document.getElementById('progress-bar');
    const progressText = document.getElementById('progress-text');
    const creditsTotalText = document.getElementById('credits-total');
    const totalRequiredCredits = 300;

    const courseStates = {}; 

    function renderCurriculum() {
        const scrollPos = container.parentElement.scrollLeft;
        container.innerHTML = '';
        curriculumData.forEach(semester => {
            const semDiv = document.createElement('div');
            semDiv.className = 'flex-shrink-0 w-column-width-min space-y-8'; 
            
            const header = document.createElement('div');
            header.className = 'bg-white/40 backdrop-blur-sm px-4 py-2.5 rounded-xl border border-outline-variant/30 text-center shadow-sm';
            header.innerHTML = `<span class="text-[10px] font-black text-primary uppercase tracking-[0.2em]">Semestre ${semester.sem}</span>`;
            semDiv.appendChild(header);

            const listDiv = document.createElement('div');
            listDiv.className = 'flex flex-col semester-column';
            
            semester.courses.forEach(course => {
                if (course.path && course.path !== currentPath) return;

                const card = document.createElement('div');
                const savedState = courseStates[course.id] || 'locked';
                card.className = `course-card p-card-padding rounded-xl ${savedState}`;
                card.dataset.id = course.id;
                card.dataset.credits = course.credits;
                card.dataset.prereqs = JSON.stringify(course.prereqs);
                card.dataset.status = savedState;

                const iconMap = {
                    'locked': 'lock',
                    'available': 'radio_button_unchecked',
                    'enrolled': 'pending_actions',
                    'approved': 'check_circle'
                };

                card.innerHTML = `
                    <div class="flex justify-between items-start mb-1">
                        <span class="text-[8px] font-black opacity-60 uppercase">${course.id}</span>
                        <span class="material-symbols-outlined text-[14px] icon-status">${iconMap[savedState]}</span>
                    </div>
                    <h3 class="text-xs font-bold leading-tight mb-2 h-8 flex items-center">${course.name}</h3>
                    <div class="flex justify-between items-center mt-auto">
                        <span class="text-[9px] font-black opacity-80 uppercase tracking-tighter">${course.credits} SCT</span>
                        <div class="status-marker w-4 h-4 rounded-full border border-black/10 flex items-center justify-center bg-white/10">
                             <span class="material-symbols-outlined text-[10px] ${savedState === 'approved' ? '' : 'hidden'} check-icon">check</span>
                        </div>
                    </div>
                `;
                listDiv.appendChild(card);
            });
            
            semDiv.appendChild(listDiv);
            container.appendChild(semDiv);
        });
        
        checkDependencies(false);
        container.parentElement.scrollLeft = scrollPos;
        requestAnimationFrame(() => {
            setTimeout(drawConnections, 100);
        });
    }

    function drawConnections() {
        svg.innerHTML = `
            <defs>
                <marker id="arrowhead" markerheight="6" markerwidth="6" orient="auto" refx="5" refy="3">
                    <path d="M0,0 L6,3 L0,6 Z" fill="#000000"></path>
                </marker>
            </defs>
        `;

        const containerRect = container.getBoundingClientRect();
        
        document.querySelectorAll('.course-card').forEach(card => {
            const prereqs = JSON.parse(card.dataset.prereqs || '[]');
            const cardRect = card.getBoundingClientRect();
            
            const targetX = cardRect.left - containerRect.left;
            const targetY = cardRect.top - containerRect.top + (cardRect.height / 2);

            prereqs.forEach((prereqId, index) => {
                const sourceCard = document.querySelector(`.course-card[data-id="${prereqId}"]`);
                if (!sourceCard) return;

                const sourceRect = sourceCard.getBoundingClientRect();
                const sourceX = sourceRect.right - containerRect.left;
                const sourceY = sourceRect.top - containerRect.top + (sourceRect.height / 2);

                const gap = targetX - sourceX;
                const midX = sourceX + (gap / 2) + ((index - (prereqs.length-1)/2) * 8);
                
                let d = `M ${sourceX} ${sourceY}`;
                d += ` L ${midX} ${sourceY}`;
                d += ` L ${midX} ${targetY}`;
                d += ` L ${targetX} ${targetY}`;

                const path = document.createElementNS("http://www.w3.org/2000/svg", "path");
                path.setAttribute("d", d);
                path.setAttribute("class", "connection-line");
                path.dataset.from = prereqId;
                path.dataset.to = card.dataset.id;
                path.setAttribute("stroke", "#000000"); 
                
                if (sourceCard.dataset.status === 'approved') {
                    path.classList.add('active');
                }
                
                path.setAttribute("marker-end", "url(#arrowhead)");
                svg.appendChild(path);
            });
        });
    }

    function updateProgress() {
        const approvedCards = document.querySelectorAll('.course-card[data-status="approved"]');
        let earnedCredits = 0;
        approvedCards.forEach(card => {
            earnedCredits += parseInt(card.dataset.credits);
        });

        const percentage = Math.round((earnedCredits / totalRequiredCredits) * 100);
        progressBar.style.width = percentage + '%';
        progressText.innerText = percentage + '%';
        creditsTotalText.innerText = `${earnedCredits} / ${totalRequiredCredits}`;
    }

    function checkDependencies(shouldDraw = true) {
        const approvedIds = Array.from(document.querySelectorAll('.course-card[data-status="approved"]'))
            .map(c => c.dataset.id);

        document.querySelectorAll('.course-card').forEach(card => {
            const currentStatus = card.dataset.status;
            const prereqs = JSON.parse(card.dataset.prereqs || '[]');
            const allMet = prereqs.every(id => approvedIds.includes(id));

            if (!allMet) {
                card.className = `course-card p-card-padding rounded-xl locked`;
                card.dataset.status = 'locked';
                card.querySelector('.icon-status').innerText = 'lock';
                card.querySelector('.check-icon').classList.add('hidden');
                courseStates[card.dataset.id] = 'locked';
            } else if (currentStatus === 'locked') {
                card.className = `course-card p-card-padding rounded-xl available`;
                card.dataset.status = 'available';
                card.querySelector('.icon-status').innerText = 'radio_button_unchecked';
                courseStates[card.dataset.id] = 'available';
            }
        });
        
        if (shouldDraw) drawConnections();
        updateProgress();
    }

    container.addEventListener('click', (e) => {
        const card = e.target.closest('.course-card');
        if (!card || card.dataset.status === 'locked') return;

        const statusCycle = ['available', 'enrolled', 'approved'];
        const currentIdx = statusCycle.indexOf(card.dataset.status);
        const nextStatus = statusCycle[(currentIdx + 1) % statusCycle.length];

        card.className = `course-card p-card-padding rounded-xl ${nextStatus}`;
        card.dataset.status = nextStatus;
        
        const iconStatus = card.querySelector('.icon-status');
        const checkIcon = card.querySelector('.check-icon');

        if (nextStatus === 'available') {
            iconStatus.innerText = 'radio_button_unchecked';
            checkIcon.classList.add('hidden');
        } else if (nextStatus === 'enrolled') {
            iconStatus.innerText = 'pending_actions';
            checkIcon.classList.add('hidden');
        } else if (nextStatus === 'approved') {
            iconStatus.innerText = 'check_circle';
            checkIcon.classList.remove('hidden');
        }

        courseStates[card.dataset.id] = nextStatus;
        checkDependencies();
    });

    document.getElementById('path-tabs').addEventListener('click', (e) => {
        const btn = e.target.closest('button');
        if (!btn) return;
        
        document.querySelectorAll('#path-tabs button').forEach(b => {
            b.classList.remove('tab-active');
            b.classList.add('text-on-surface-variant');
        });
        btn.classList.add('tab-active');
        btn.classList.remove('text-on-surface-variant');
        
        currentPath = btn.dataset.path;
        renderCurriculum();
    });

    container.addEventListener('mouseover', (e) => {
        const card = e.target.closest('.course-card');
        if (!card) return;
        const id = card.dataset.id;
        svg.querySelectorAll(`.connection-line[data-from="${id}"], .connection-line[data-to="${id}"]`).forEach(l => {
            l.classList.add('active');
            l.style.opacity = "1";
        });
    });

    container.addEventListener('mouseout', (e) => {
        const card = e.target.closest('.course-card');
        if (!card) return;
        svg.querySelectorAll('.connection-line').forEach(l => {
            const fromCard = document.querySelector(`.course-card[data-id="${l.dataset.from}"]`);
            if (fromCard && fromCard.dataset.status !== 'approved') {
                l.classList.remove('active');
                l.style.opacity = "0.25";
            }
        });
    });

    window.addEventListener('resize', drawConnections);
    
    renderCurriculum();
</script>
</body></html>
