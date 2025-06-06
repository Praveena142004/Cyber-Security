# Cyber-Security
Project Title : Dark Web Forensics Investigating Cyber Criminal Activities

CODE:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DarkWeb Crawler - Vulnerability Assessment</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --cyber-dark: #0a0e17;
            --cyber-darker: #050709;
            --cyber-accent: #00b4d8;
            --cyber-accent-hover: #0096c7;
            --cyber-text: #e0e0e0;
            --cyber-green: #00ff66;
            --cyber-yellow: #ffd000;
            --cyber-red: #ff2a6d;
            --risk-high: rgba(255, 42, 109, 0.1);
            --risk-medium: rgba(255, 208, 0, 0.1);
            --risk-low: rgba(0, 255, 102, 0.1);
        }
        
        body {
            background-color: var(--cyber-dark);
            color: var(--cyber-text);
            font-family: 'Courier New', monospace;
            position: relative;
            overflow-x: hidden;
        }
        
        body::before {
            display: none; /* Remove original background */
        }
        
        .navbar {
            background-color: var(--cyber-darker);
            border-bottom: 1px solid var(--cyber-accent);
        }
        
        .navbar-brand, .nav-link {
            color: var(--cyber-accent) !important;
            text-shadow: 0 0 5px rgba(0, 180, 216, 0.5);
            transition: all 0.3s ease;
        }
        
        .nav-link:hover, .navbar-brand:hover {
            color: var(--cyber-text) !important;
            text-shadow: 0 0 10px var(--cyber-accent);
        }
        
        .content-section {
            background-color: rgba(10, 14, 23, 0.7);
            border: 1px solid var(--cyber-accent);
            border-radius: 5px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 0 15px rgba(0, 180, 216, 0.2);
            position: relative;
            overflow: hidden;
        }
        
        .content-section::after {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--cyber-accent), transparent);
            animation: scanning 3s linear infinite;
        }
        
        @keyframes scanning {
            0% { left: -100%; }
            100% { left: 100%; }
        }
        
        .section-title {
            color: var(--cyber-accent);
            font-weight: bold;
            text-transform: uppercase;
            display: inline-block;
            position: relative;
            margin-bottom: 20px;
        }
        
        .section-title::before, .section-title::after {
            content: "//";
            color: var(--cyber-accent);
            margin: 0 8px;
            opacity: 0.7;
        }
        
        .btn-cyber {
            background-color: var(--cyber-accent);
            color: var(--cyber-darker);
            border: none;
            font-weight: bold;
            text-transform: uppercase;
            position: relative;
            overflow: hidden;
            z-index: 1;
            transition: all 0.3s ease;
        }
        
        .btn-cyber:hover {
            background-color: var(--cyber-accent-hover);
            box-shadow: 0 0 10px var(--cyber-accent);
            color: white;
        }
        
        .btn-cyber::before {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: all 0.3s ease;
            z-index: -1;
        }
        
        .btn-cyber:hover::before {
            left: 100%;
            transition: all 0.3s ease;
        }
        
        .risk-indicator {
            font-size: 24px;
            font-weight: bold;
            text-align: center;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            line-height: 50px;
            margin: 0 auto;
            transition: all 0.3s ease;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .risk-high {
            background-color: var(--cyber-red);
            color: white;
        }
        
        .risk-high::after {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: radial-gradient(circle, rgba(255, 42, 109, 0.7) 0%, rgba(255, 42, 109, 0) 70%);
            animation: pulse 1.5s ease-out infinite;
        }
        
        .risk-medium {
            background-color: var(--cyber-yellow);
            color: var(--cyber-darker);
        }
        
        .risk-medium::after {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: radial-gradient(circle, rgba(255, 208, 0, 0.7) 0%, rgba(255, 208, 0, 0) 70%);
            animation: pulse 2s ease-out infinite;
        }
        
        .risk-low {
            background-color: var(--cyber-green);
            color: var(--cyber-darker);
        }
        
        .risk-low::after {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: radial-gradient(circle, rgba(0, 255, 102, 0.7) 0%, rgba(0, 255, 102, 0) 70%);
            animation: pulse 3s ease-out infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 0.7; transform: scale(1); }
            100% { opacity: 0; transform: scale(2.5); }
        }
        
        .card {
            background-color: rgba(5, 7, 9, 0.7);
            border: 1px solid var(--cyber-accent);
            margin-bottom: 15px;
            transition: all 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 180, 216, 0.2);
        }
        
        .card-header {
            background-color: rgba(0, 180, 216, 0.1);
            border-bottom: 1px solid var(--cyber-accent);
            color: var(--cyber-accent);
            font-weight: bold;
        }
        
        .risk-card-high {
            border-color: var(--cyber-red);
            background: var(--risk-high);
        }
        
        .risk-card-high .card-header {
            background-color: rgba(255, 42, 109, 0.2);
            border-bottom: 1px solid var(--cyber-red);
            color: var(--cyber-red);
        }
        
        .risk-card-medium {
            border-color: var(--cyber-yellow);
            background: var(--risk-medium);
        }
        
        .risk-card-medium .card-header {
            background-color: rgba(255, 208, 0, 0.2);
            border-bottom: 1px solid var(--cyber-yellow);
            color: var(--cyber-yellow);
        }
        
        .risk-card-low {
            border-color: var(--cyber-green);
            background: var(--risk-low);
        }
        
        .risk-card-low .card-header {
            background-color: rgba(0, 255, 102, 0.2);
            border-bottom: 1px solid var(--cyber-green);
            color: var(--cyber-green);
        }
        
        .typing-effect {
            border-right: 2px solid var(--cyber-accent);
            white-space: nowrap;
            overflow: hidden;
            width: 0;
            animation: typing 3.5s steps(40, end) forwards, blink-caret 0.75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: var(--cyber-accent) }
        }
        
        .spinner {
            width: 40px;
            height: 40px;
            margin: 0 auto;
            border: 4px solid rgba(0, 180, 216, 0.2);
            border-top: 4px solid var(--cyber-accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Dynamic background with cursor effects */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
        }

        .cursor-follower {
            position: fixed;
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, rgba(0,180,216,0.3) 0%, rgba(0,180,216,0) 70%);
            border-radius: 50%;
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: -1;
            animation: pulse-cursor 2s infinite;
            mix-blend-mode: screen;
        }

        .data-lines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            overflow: hidden;
        }

        .data-line {
            position: absolute;
            height: 1px;
            width: 100%;
            background-image: linear-gradient(to right, 
                transparent, 
                rgba(0, 180, 216, 0.1), 
                rgba(0, 180, 216, 0.2), 
                rgba(0, 180, 216, 0.1), 
                transparent);
            animation-name: data-line-animation;
            animation-timing-function: linear;
            animation-iteration-count: infinite;
            box-shadow: 0 0 5px rgba(0, 180, 216, 0.5);
        }

        @keyframes data-line-animation {
            0% { transform: translateY(-200%); }
            100% { transform: translateY(200vh); }
        }

        .digital-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -3;
            color: rgba(0, 180, 216, 0.1);
            font-family: monospace;
            font-size: 14px;
            overflow: hidden;
            pointer-events: none;
        }

        .digital-rain .rain-column {
            position: absolute;
            top: -20%;
            animation-name: digital-rain-animation;
            animation-timing-function: linear;
            animation-iteration-count: infinite;
            text-align: center;
        }

        @keyframes digital-rain-animation {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(200vh); }
        }

        @keyframes pulse-cursor {
            0% { opacity: 0.2; transform: translate(-50%, -50%) scale(1); }
            50% { opacity: 0.4; transform: translate(-50%, -50%) scale(1.5); }
            100% { opacity: 0.2; transform: translate(-50%, -50%) scale(1); }
        }
    </style>
</head>
<body>
    <!-- Dynamic background elements -->
    <div id="particles-js"></div>
    <div class="cursor-follower"></div>
    <div class="data-lines"></div>
    <div class="digital-rain"></div>
    
    <nav class="navbar navbar-expand-lg navbar-dark mb-4">
        <div class="container">
            <a class="navbar-brand" href="/"><i class="fas fa-spider me-2"></i>DarkWeb Crawler</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="/"><i class="fas fa-home me-1"></i> Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/dashboard"><i class="fas fa-chart-line me-1"></i> Dashboard</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/history"><i class="fas fa-history me-1"></i> History</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/batch"><i class="fas fa-tasks me-1"></i> Batch</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link active" href="/vulnerability"><i class="fas fa-shield-alt me-1"></i> Vulnerability</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <div class="container">
        <div class="content-section mb-4">
            <h2 class="section-title typing-effect">Vulnerability Assessment</h2>
            <p>Analyze .onion sites for security risks and vulnerabilities using AI-powered assessment.</p>
            
            <form id="vulnerability-form" class="mb-4">
                <div class="input-group">
                    <span class="input-group-text bg-dark text-light border-secondary"><i class="fas fa-link"></i></span>
                    <input type="text" id="url-input" class="form-control bg-dark text-light border-secondary" placeholder="Enter .onion URL to analyze">
                    <button type="submit" class="btn btn-cyber">
                        <i class="fas fa-search-plus me-1"></i> Analyze
                    </button>
                </div>
            </form>
        </div>

        <div class="row">
            <div class="col-md-4">
                <div class="content-section">
                    <h4 class="section-title">Risk Summary</h4>
                    <div id="risk-overview" class="text-center">
                        <p>Enter a URL to analyze vulnerability risks</p>
                        <div class="risk-indicator">?</div>
                    </div>
                </div>
            </div>
            <div class="col-md-8">
                <div class="content-section">
                    <h4 class="section-title">Vulnerability Details</h4>
                    <div id="vulnerability-details">
                        <p class="text-center">No vulnerability analysis available yet.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="content-section">
            <h4 class="section-title">Recent Vulnerability Assessments</h4>
            <div id="recent-assessments" class="row">
                {% if recent_assessments %}
                    {% for assessment in recent_assessments %}
                    <div class="col-md-6 mb-3">
                        <div class="card {% if assessment.risk_level >= 7 %}risk-card-high{% elif assessment.risk_level >= 4 %}risk-card-medium{% else %}risk-card-low{% endif %}">
                            <div class="card-header">
                                <i class="fas {% if assessment.risk_level >= 7 %}fa-exclamation-triangle{% elif assessment.risk_level >= 4 %}fa-exclamation-circle{% else %}fa-check-circle{% endif %} me-2"></i>
                                {{ assessment.url }}
                            </div>
                            <div class="card-body">
                                <h5 class="card-title">{{ assessment.category }}</h5>
                                <div class="d-flex justify-content-between align-items-center">
                                    <div class="risk-indicator {% if assessment.risk_level >= 7 %}risk-high{% elif assessment.risk_level >= 4 %}risk-medium{% else %}risk-low{% endif %}">
                                        {{ assessment.risk_level }}
                                    </div>
                                    <a href="/analysis/{{ assessment.id }}" class="btn btn-sm btn-cyber">
                                        <i class="fas fa-eye me-1"></i> View
                                    </a>
                                </div>
                            </div>
                            <div class="card-footer text-muted">
                                <small>{{ assessment.timestamp }}</small>
                            </div>
                        </div>
                    </div>
                    {% endfor %}
                {% else %}
                    <p class="text-center">No recent assessments found.</p>
                {% endif %}
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const vulnerabilityForm = document.getElementById('vulnerability-form');
            const riskOverview = document.getElementById('risk-overview');
            const vulnerabilityDetails = document.getElementById('vulnerability-details');
            
            // Initialize dynamic background elements
            initDynamicBackground();
            
            vulnerabilityForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const url = document.getElementById('url-input').value;
                if (!url) return;
                
                // Show loading spinner
                riskOverview.innerHTML = '<div class="spinner my-4"></div><p>Analyzing site security...</p>';
                vulnerabilityDetails.innerHTML = '<div class="spinner my-4"></div><p>Gathering vulnerability data...</p>';
                
                // Call the API to analyze the URL
                fetch('/api/process', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({ url: url }),
                })
                .then(response => response.json())
                .then(data => {
                    if (data.success) {
                        updateRiskDisplay(data);
                        setTimeout(() => {
                            location.reload(); // Refresh to show updated recent assessments
                        }, 3000);
                    } else {
                        showError(data.error);
                    }
                })
                .catch(error => {
                    showError("Failed to analyze URL: " + error);
                });
            });
            
            function updateRiskDisplay(data) {
                // Extract risk level from AI analysis
                let riskLevel = 0;
                let riskClass = "risk-low";
                let riskCategory = "Unknown";
                
                const riskMatch = data.ai_analysis.match(/RISK_LEVEL:\s*(\d+)/);
                if (riskMatch) {
                    riskLevel = parseInt(riskMatch[1]);
                    if (riskLevel >= 7) {
                        riskClass = "risk-high";
                    } else if (riskLevel >= 4) {
                        riskClass = "risk-medium";
                    }
                }
                
                const categoryMatch = data.ai_analysis.match(/CONTENT_TYPE:\s*([^\n]+)/);
                if (categoryMatch) {
                    riskCategory = categoryMatch[1].trim();
                }
                
                // Update risk overview
                riskOverview.innerHTML = `
                    <h5>${riskCategory}</h5>
                    <div class="risk-indicator ${riskClass}">${riskLevel}</div>
                    <p class="mt-3">
                        <span class="badge ${riskLevel >= 7 ? 'bg-danger' : riskLevel >= 4 ? 'bg-warning text-dark' : 'bg-success'}">
                            ${riskLevel >= 7 ? 'High Risk' : riskLevel >= 4 ? 'Medium Risk' : 'Low Risk'}
                        </span>
                    </p>
                `;
                
                // Update vulnerability details
                let sections = data.ai_analysis.split(/\d+\.\s+/);
                if (sections.length > 1) {
                    sections = sections.slice(1); // Remove the first empty element
                    
                    let detailsHtml = '';
                    
                    // Process CONCERNS section
                    const concernsSection = sections.find(s => s.startsWith('CONCERNS'));
                    if (concernsSection) {
                        const concernsList = concernsSection.replace('CONCERNS:', '').trim().split('\n')
                            .filter(item => item.trim().length > 0)
                            .map(item => `<li>${item.trim()}</li>`)
                            .join('');
                            
                        if (concernsList) {
                            detailsHtml += `
                                <div class="mb-4">
                                    <h5><i class="fas fa-exclamation-triangle me-2"></i>Security Concerns</h5>
                                    <ul>${concernsList}</ul>
                                </div>
                            `;
                        }
                    }
                    
                    // Process VULNERABILITIES section
                    const vulnSection = sections.find(s => s.startsWith('VULNERABILITIES'));
                    if (vulnSection) {
                        const vulnList = vulnSection.replace('VULNERABILITIES:', '').trim().split('\n')
                            .filter(item => item.trim().length > 0)
                            .map(item => `<li>${item.trim()}</li>`)
                            .join('');
                            
                        if (vulnList) {
                            detailsHtml += `
                                <div class="mb-4">
                                    <h5><i class="fas fa-bug me-2"></i>Technical Vulnerabilities</h5>
                                    <ul class="text-danger">${vulnList}</ul>
                                </div>
                            `;
                        }
                    }
                    
                    // Process POTENTIAL_FUTURE_RISKS section
                    const futureSection = sections.find(s => s.startsWith('POTENTIAL_FUTURE_RISKS'));
                    if (futureSection) {
                        const futureList = futureSection.replace('POTENTIAL_FUTURE_RISKS:', '').trim().split('\n')
                            .filter(item => item.trim().length > 0)
                            .map(item => `<li>${item.trim()}</li>`)
                            .join('');
                            
                        if (futureList) {
                            detailsHtml += `
                                <div class="mb-4">
                                    <h5><i class="fas fa-binoculars me-2"></i>Potential Future Risks</h5>
                                    <ul class="text-warning">${futureList}</ul>
                                </div>
                            `;
                        }
                    }
                    
                    // Process SUMMARY section
                    const summarySection = sections.find(s => s.startsWith('SUMMARY'));
                    if (summarySection) {
                        const summary = summarySection.replace('SUMMARY:', '').trim();
                        detailsHtml += `
                            <div class="mb-4">
                                <h5><i class="fas fa-info-circle me-2"></i>Summary</h5>
                                <p>${summary}</p>
                            </div>
                        `;
                    }
                    
                    // Add text snippet
                    detailsHtml += `
                        <div>
                            <h5><i class="fas fa-file-alt me-2"></i>Content Sample</h5>
                            <div class="bg-dark p-3 rounded" style="max-height: 200px; overflow-y: auto;">
                                <pre class="text-light mb-0" style="white-space: pre-wrap;">${data.raw_text_snippet}</pre>
                            </div>
                        </div>
                    `;
                    
                    vulnerabilityDetails.innerHTML = detailsHtml;
                } else {
                    vulnerabilityDetails.innerHTML = `<p>${data.ai_analysis}</p>`;
                }
            }
            
            function showError(errorMessage) {
                riskOverview.innerHTML = `
                    <div class="alert alert-danger">
                        <i class="fas fa-exclamation-triangle me-2"></i>${errorMessage}
                    </div>
                `;
                vulnerabilityDetails.innerHTML = `
                    <div class="alert alert-danger">
                        <i class="fas fa-exclamation-triangle me-2"></i>Failed to analyze vulnerabilities.
                    </div>
                `;
            }

            // Initialize dynamic background effects
            function initDynamicBackground() {
                // Initialize particles.js
                particlesJS('particles-js', {
                    "particles": {
                        "number": {
                            "value": 40,
                            "density": {
                                "enable": true,
                                "value_area": 800
                            }
                        },
                        "color": {
                            "value": "#00b4d8"
                        },
                        "shape": {
                            "type": "circle",
                            "stroke": {
                                "width": 0,
                                "color": "#000000"
                            }
                        },
                        "opacity": {
                            "value": 0.2,
                            "random": true,
                            "anim": {
                                "enable": true,
                                "speed": 1,
                                "opacity_min": 0.1,
                                "sync": false
                            }
                        },
                        "size": {
                            "value": 3,
                            "random": true,
                            "anim": {
                                "enable": true,
                                "speed": 2,
                                "size_min": 0.1,
                                "sync": false
                            }
                        },
                        "line_linked": {
                            "enable": true,
                            "distance": 150,
                            "color": "#00b4d8",
                            "opacity": 0.2,
                            "width": 1
                        },
                        "move": {
                            "enable": true,
                            "speed": 1,
                            "direction": "none",
                            "random": true,
                            "straight": false,
                            "out_mode": "out",
                            "bounce": false,
                            "attract": {
                                "enable": true,
                                "rotateX": 600,
                                "rotateY": 1200
                            }
                        }
                    },
                    "interactivity": {
                        "detect_on": "canvas",
                        "events": {
                            "onhover": {
                                "enable": true,
                                "mode": "grab"
                            },
                            "onclick": {
                                "enable": true,
                                "mode": "push"
                            },
                            "resize": true
                        },
                        "modes": {
                            "grab": {
                                "distance": 140,
                                "line_linked": {
                                    "opacity": 0.5
                                }
                            },
                            "push": {
                                "particles_nb": 3
                            }
                        }
                    },
                    "retina_detect": true
                });

                // Create cursor follower effect
                const cursorFollower = document.querySelector('.cursor-follower');
                document.addEventListener('mousemove', (e) => {
                    cursorFollower.style.left = e.clientX + 'px';
                    cursorFollower.style.top = e.clientY + 'px';
                });

                // Create data lines effect
                const dataLines = document.querySelector('.data-lines');
                for (let i = 0; i < 15; i++) {
                    const line = document.createElement('div');
                    line.classList.add('data-line');
                    line.style.top = Math.random() * 100 + 'vh';
                    line.style.animationDuration = (Math.random() * 8 + 5) + 's';
                    line.style.opacity = Math.random() * 0.5 + 0.1;
                    dataLines.appendChild(line);
                }

                // Create digital rain effect
                const digitalRain = document.querySelector('.digital-rain');
                const characters = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
                
                for (let i = 0; i < 30; i++) {
                    const column = document.createElement('div');
                    column.classList.add('rain-column');
                    column.style.left = (Math.random() * 100) + 'vw';
                    column.style.animationDuration = (Math.random() * 10 + 10) + 's';
                    column.style.opacity = Math.random() * 0.3 + 0.1;
                    
                    const columnLength = Math.floor(Math.random() * 20 + 10);
                    let columnHtml = '';
                    
                    for (let j = 0; j < columnLength; j++) {
                        const charIndex = Math.floor(Math.random() * characters.length);
                        columnHtml += characters.charAt(charIndex) + '<br>';
                    }
                    
                    column.innerHTML = columnHtml;
                    digitalRain.appendChild(column);
                }
            }
        });
    </script>
</body>
</html> 
