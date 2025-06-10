<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SeedTech | Advanced Interactive Proposal by Brandi</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;900&family=Tajawal:wght@400;700;900&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/feather-icons/dist/feather.min.js"></script>
    <style>
        :root {
            --bg-color: #f9fafb; /* gray-50 */
            --card-bg-color: #ffffff;
            --text-color-primary: #111827; /* gray-900 */
            --text-color-secondary: #4b5563; /* gray-600 */
            --border-color: #e5e7eb; /* gray-200 */
            
            /* New Nature-inspired Brand Colors */
            --accent-green-dark: #0A7029;
            --accent-green-mid: #9ABA12;
            --accent-green-light: #C8DF52;
            --accent-yellow: #FEDE00;
            
            /* Header/Footer Colors from Logo */
            --header-gradient-start: #4f46e5;
            --header-gradient-end: #7c3aed;
            --brand-orange-footer: #f97316;
            
            --map-inactive: #D1D5DB;
        }

        html.dark {
            --bg-color: #111827; /* Charcoal */
            --card-bg-color: #1F2937; /* Darker Gray */
            --text-color-primary: #F3F4F6; /* Light Gray */
            --text-color-secondary: #9CA3AF; /* Medium Gray */
            --border-color: #374151; /* Gray */
            --map-inactive: #4B5563;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color-primary);
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        
        html[dir="rtl"] body {
            font-family: 'Tajawal', sans-serif;
        }
        
        .gradient-text {
            background: linear-gradient(to right, var(--accent-green-light), var(--accent-green-dark));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .brand-gradient-bg {
             background: linear-gradient(90deg, var(--header-gradient-start), var(--header-gradient-end));
        }
        .card {
            background-color: var(--card-bg-color);
            border: 1px solid var(--border-color);
            transition: background-color 0.3s ease, border-color 0.3s ease;
        }
        .tab-button { transition: all 0.3s ease; padding: 0.5rem 1rem; border-radius: 9999px; font-weight: 600; }
        .tab-button.active { background-color: var(--accent-green-dark); color: white; box-shadow: 0 4px 14px rgba(10, 112, 41, 0.3); }
        .kpi-selector-btn { background-color: transparent; border: 1px solid var(--border-color); padding: 0.5rem 1rem; border-radius: 9999px; font-weight: 600; color: var(--text-color-secondary); }
        .kpi-selector-btn.active { background-color: var(--accent-green-dark); color: white; border-color: var(--accent-green-dark); }
        .section-title { font-weight: 900; font-size: 2.25rem; letter-spacing: -0.05em; text-align: center; margin-bottom: 1rem; }
        .section-subtitle { text-align: center; color: var(--text-color-secondary); margin-bottom: 4rem; max-width: 3xl; margin-left: auto; margin-right: auto; }
        
        .lang-toggle { font-weight: bold; cursor: pointer; padding: 0.25rem 0.5rem; border-radius: 0.25rem; transition: background-color 0.2s; }
        .lang-toggle:not(.active) { opacity: 0.6; }
        
        .calendar-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 0.5rem; }
        .calendar-day { background-color: var(--bg-color); border: 1px solid var(--border-color); border-radius: 0.5rem; padding: 0.5rem; min-height: 100px; display: flex; flex-direction: column; gap: 4px; }
        .calendar-day-header { font-size: 0.75rem; font-weight: 600; color: var(--text-color-secondary); }
        .post-pill { font-size: 0.75rem; padding: 0.25rem 0.5rem; border-radius: 9999px; font-weight: 600; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s; }
        .post-pill:hover { transform: translateY(-2px); box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
        .kpi-infographic-item { text-align: center; }
        .target-arrow { color: var(--accent-green-dark); font-weight: bold; margin: 0 0.25rem;}
        #content-modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.6); z-index: 99; display: none; align-items: center; justify-content: center; backdrop-filter: blur(4px); }
        #content-modal { background-color: var(--card-bg-color); padding: 2rem; border-radius: 1rem; max-width: 500px; width: 90%; box-shadow: 0 25px 50px -12px rgba(0,0,0,0.25); position: relative; }
        #notes-area { width: 100%; min-height: 150px; border: 2px dashed var(--border-color); padding: 1rem; border-radius: 0.5rem; background-color: var(--bg-color); }
        #notes-area:focus { outline: 2px solid var(--accent-green-dark); }
    </style>
</head>
<body>

    <header class="brand-gradient-bg sticky top-0 z-50 shadow-lg">
        <div class="container mx-auto px-4 sm:px-6 py-3 flex justify-between items-center">
            <a href="#" class="flex items-center space-x-2">
                <span class="font-bold text-2xl text-white">SeedTech</span>
            </a>
            <div class="flex items-center space-x-2 sm:space-x-4">
                <nav class="hidden md:flex items-center space-x-4 lg:space-x-6 text-sm lg:text-base">
                    <a href="#assessment" class="text-white/80 hover:text-white transition" data-lang-key="nav_assessment">Assessment</a>
                    <a href="#kpis" class="text-white/80 hover:text-white transition" data-lang-key="nav_snapshots">Snapshots</a>
                    <a href="#channel-performance" class="text-white/80 hover:text-white transition" data-lang-key="nav_channels">Channels</a>
                    <a href="#strategy" class="text-white/80 hover:text-white transition" data-lang-key="nav_strategy">Strategy</a>
                    <a href="#planning" class="text-white/80 hover:text-white transition" data-lang-key="nav_planning">Planning</a>
                    <a href="#budget" class="text-white/80 hover:text-white transition" data-lang-key="nav_budget">Budget</a>
                </nav>
                 <div class="flex items-center bg-white/20 rounded-full p-1 text-sm text-white">
                    <span id="lang-en" class="lang-toggle active" data-lang="en">EN</span>
                    <span id="lang-ar" class="lang-toggle" data-lang="ar">AR</span>
                </div>
                 <button id="dark-mode-toggle" class="p-2 rounded-full text-white/80 hover:text-white hover:bg-white/20 transition">
                    <i data-feather="moon" class="dark-mode-icon dark:hidden"></i>
                    <i data-feather="sun" class="dark-mode-icon hidden dark:inline-block"></i>
                </button>
                <div class="md:hidden"><button id="menu-btn" class="p-2 text-white"><i data-feather="menu"></i></button></div>
            </div>
        </div>
        <div id="mobile-menu" class="hidden md:hidden px-6 pb-4 bg-white/10">
            <a href="#assessment" class="block py-2 text-white/90 hover:text-white" data-lang-key="nav_assessment">Assessment</a>
            <a href="#kpis" class="block py-2 text-white/90 hover:text-white" data-lang-key="nav_snapshots">Snapshots</a>
            <a href="#channel-performance" class="block py-2 text-white/90 hover:text-white" data-lang-key="nav_channels">Channels</a>
            <a href="#strategy" class="block py-2 text-white/90 hover:text-white" data-lang-key="nav_strategy">Strategy</a>
            <a href="#planning" class="block py-2 text-white/90 hover:text-white" data-lang-key="nav_planning">Planning</a>
            <a href="#budget" class="block py-2 text-white/90 hover:text-white" data-lang-key="nav_budget">Budget</a>
        </div>
    </header>

    <main class="container mx-auto px-6 py-16">
        <div class="text-center">
            <h1 class="text-4xl md:text-6xl font-black tracking-tighter" data-lang-key="main_title">Cultivating <span class="gradient-text">Digital Growth</span> for SeedTech</h1>
            <p class="mt-4 max-w-3xl mx-auto text-lg text-slate-600 dark:text-slate-300" data-lang-key="main_subtitle">An advanced interactive proposal by <span class="font-semibold">Brandi</span> to establish SeedTech as the premier agricultural solutions provider.</p>
             <div class="mt-8 max-w-4xl mx-auto rounded-2xl shadow-2xl overflow-hidden">
                <img src="https://placehold.co/1200x600/111827/C8DF52?text=SeedTech%0ASeeds+%26+Agriculture" alt="SeedTech Brand Visual" class="w-full h-auto">
            </div>
        </div>

        <section id="foundation" class="pt-24">
            <h2 class="section-title" data-lang-key="foundation_title">Brand Foundation</h2>
            <p class="section-subtitle" data-lang-key="foundation_subtitle">Our strategy is built upon SeedTech's core identity, amplifying its strengths across all digital channels.</p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="card p-8 rounded-2xl shadow-lg">
                    <h3 class="text-xl font-bold flex items-center"><i data-feather="briefcase" class="mr-3 text-accent-green-dark"></i><span data-lang-key="profile_title">Company Profile</span></h3>
                    <p class="mt-4 text-slate-600 dark:text-slate-300" data-lang-key="profile_content">Since 2012, SeedTech has partnered with Technisem to improve agricultural productivity via high-quality seeds and agronomic expertise. Now expanding from Sudan to Oman and Uganda, SeedTech is a visionary leader in regional food security.</p>
                </div>
                <div class="card p-8 rounded-2xl shadow-lg">
                    <h3 class="text-xl font-bold flex items-center"><i data-feather="compass" class="mr-3 text-accent-green-dark"></i><span data-lang-key="pillars_title">Brand Identity Pillars</span></h3>
                     <ul class="mt-4 space-y-3">
                        <li class="flex items-start"><i data-feather="check" class="text-accent-green-dark mx-2 mt-1 flex-shrink-0"></i><span data-lang-key="pillar_quality"><strong>Quality:</strong> Uncompromising excellence in every seed and consultation.</span></li>
                        <li class="flex items-start"><i data-feather="check" class="text-accent-green-dark mx-2 mt-1 flex-shrink-0"></i><span data-lang-key="pillar_expertise"><strong>Expertise:</strong> Demonstrating deep technical knowledge and dependable support.</span></li>
                        <li class="flex items-start"><i data-feather="check" class="text-accent-green-dark mx-2 mt-1 flex-shrink-0"></i><span data-lang-key="pillar_innovation"><strong>Innovation:</strong> Highlighting premium varieties and modern Agri-Tech.</span></li>
                        <li class="flex items-start"><i data-feather="check" class="text-accent-green-dark mx-2 mt-1 flex-shrink-0"></i><span data-lang-key="pillar_education"><strong>Education:</strong> Making complex agronomy accessible and practical for all.</span></li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="assessment" class="pt-24">
            <h2 class="section-title" data-lang-key="assessment_title">SeedTech Current Initial Assessment</h2>
            <p class="section-subtitle" data-lang-key="assessment_subtitle">To forge a successful path forward, we must first understand the starting point. This initial assessment establishes the baseline digital footprint and sets our 6-month growth targets.</p>
            <div class="card p-8 rounded-2xl shadow-lg">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <!-- Sudan -->
                    <div class="card p-6 rounded-xl border-l-4 rtl:border-l-0 rtl:border-r-4" style="border-color: var(--accent-green-dark);">
                        <h4 class="text-xl font-bold mb-4">SeedTech Sudan</h4>
                        <ul class="space-y-3 mb-4">
                            <li class="flex items-center"><i data-feather="facebook" class="mx-3 text-gray-500"></i><span data-lang-key="facebook">Facebook</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">11,000 <span class="target-arrow">→ 12.5K</span></span></li>
                            <li class="flex items-center"><i data-feather="linkedin" class="mx-3 text-gray-500"></i><span data-lang-key="linkedin">LinkedIn</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">881 <span class="target-arrow">→ 1.2K</span></span></li>
                            <li class="flex items-center"><i data-feather="instagram" class="mx-3 text-gray-500"></i><span data-lang-key="instagram">Instagram</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">182 <span class="target-arrow">→ 500</span></span></li>
                            <li class="flex items-center"><i data-feather="youtube" class="mx-3 text-gray-500"></i><span data-lang-key="youtube">YouTube</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">125 <span class="target-arrow">→ 400</span></span></li>
                            <li class="flex items-center"><i data-feather="video" class="mx-3 text-gray-500"></i><span data-lang-key="tiktok">TikTok</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">28 <span class="target-arrow">→ 250</span></span></li>
                        </ul>
                        <a href="https://seedtech-sd.com" target="_blank" class="font-semibold text-accent-green-dark hover:underline flex items-center" data-lang-key="website">Website <i data-feather="arrow-right" class="w-4 h-4 ltr:ml-1 rtl:mr-1"></i></a>
                    </div>
                    <!-- Uganda -->
                    <div class="card p-6 rounded-xl border-l-4 rtl:border-l-0 rtl:border-r-4" style="border-color: var(--accent-yellow);">
                        <h4 class="text-xl font-bold mb-4">Agriganda (Uganda)</h4>
                        <ul class="space-y-3 mb-4">
                             <li class="flex items-center"><i data-feather="video" class="mx-3 text-gray-500"></i><span data-lang-key="tiktok">TikTok</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">16 <span class="target-arrow">→ 500</span></span></li>
                            <li class="flex items-center"><i data-feather="facebook" class="mx-3 text-gray-500"></i><span data-lang-key="facebook">Facebook</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">8 <span class="target-arrow">→ 1K</span></span></li>
                            <li class="flex items-center"><i data-feather="instagram" class="mx-3 text-gray-500"></i><span data-lang-key="instagram">Instagram</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">2 <span class="target-arrow">→ 500</span></span></li>
                            <li class="flex items-center text-gray-400"><i data-feather="youtube" class="mx-3"></i><span data-lang-key="youtube">YouTube</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">N/A <span class="target-arrow">→ 250</span></span></li>
                            <li class="flex items-center text-gray-400"><i data-feather="linkedin" class="mx-3"></i><span data-lang-key="linkedin">LinkedIn</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">N/A <span class="target-arrow">→ 100</span></span></li>
                        </ul>
                        <a href="https://agri-ganda.com" target="_blank" class="font-semibold text-accent-green-dark hover:underline flex items-center" data-lang-key="website">Website <i data-feather="arrow-right" class="w-4 h-4 ltr:ml-1 rtl:mr-1"></i></a>
                    </div>
                    <!-- Oman -->
                    <div class="card p-6 rounded-xl border-l-4 rtl:border-l-0 rtl:border-r-4" style="border-color: var(--accent-green-light);">
                        <h4 class="text-xl font-bold mb-4">WOGUD (Oman)</h4>
                        <ul class="space-y-3 mb-4">
                            <li class="flex items-center"><i data-feather="facebook" class="mx-3 text-gray-500"></i><span data-lang-key="facebook">Facebook</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">18 <span class="target-arrow">→ 1K</span></span></li>
                            <li class="flex items-center"><i data-feather="video" class="mx-3 text-gray-500"></i><span data-lang-key="tiktok">TikTok</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">16 <span class="target-arrow">→ 500</span></span></li>
                            <li class="flex items-center"><i data-feather="instagram" class="mx-3 text-gray-500"></i><span data-lang-key="instagram">Instagram</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">4 <span class="target-arrow">→ 750</span></span></li>
                            <li class="flex items-center text-gray-400"><i data-feather="youtube" class="mx-3"></i><span data-lang-key="youtube">YouTube</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">N/A <span class="target-arrow">→ 250</span></span></li>
                            <li class="flex items-center text-gray-400"><i data-feather="linkedin" class="mx-3"></i><span data-lang-key="linkedin">LinkedIn</span>: <span class="font-bold ltr:ml-auto rtl:mr-auto">N/A <span class="target-arrow">→ 500</span></span></li>
                        </ul>
                         <a href="https://agri-ganda.com" target="_blank" class="font-semibold text-accent-green-dark hover:underline flex items-center" data-lang-key="website">Website <i data-feather="arrow-right" class="w-4 h-4 ltr:ml-1 rtl:mr-1"></i></a>
                    </div>
                </div>
                 <div class="mt-8 pt-8 border-t border-gray-200 dark:border-gray-700">
                    <h3 class="text-xl font-bold text-center mb-6" data-lang-key="assessment_interactive_title">Interactive Channel Analysis</h3>
                    <div class="flex flex-wrap justify-center gap-2 mb-6">
                        <button class="kpi-selector-btn active" data-region="sd" data-lang-key="sudan">Sudan</button>
                        <button class="kpi-selector-btn" data-region="ug" data-lang-key="uganda">Uganda</button>
                        <button class="kpi-selector-btn" data-region="om" data-lang-key="oman">Oman</button>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                        <div class="h-80"><canvas id="assessment-chart"></canvas></div>
                        <div id="assessment-insights" class="card p-6 rounded-xl"></div>
                    </div>
                </div>
            </div>
        </section>

        <section id="kpis" class="pt-24">
            <h2 class="section-title" data-lang-key="snapshots_title">Performance Insights Snapshots</h2>
            
            <div class="card p-8 rounded-2xl shadow-lg">
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 text-center">
                    <div class="kpi-infographic-item">
                        <i data-feather="eye" class="w-12 h-12 mx-auto text-accent-green-dark"></i>
                        <p class="text-4xl font-black mt-4">4.4K</p>
                        <h4 class="font-semibold mt-2 text-slate-600 dark:text-slate-300" data-lang-key="impressions">Impressions</h4>
                    </div>
                    <div class="kpi-infographic-item">
                         <i data-feather="percent" class="w-12 h-12 mx-auto text-accent-green-dark"></i>
                        <p class="text-4xl font-black mt-4">23.35%</p>
                        <h4 class="font-semibold mt-2 text-slate-600 dark:text-slate-300" data-lang-key="engagement_rate">Engagement Rate</h4>
                    </div>
                    <div class="kpi-infographic-item">
                        <i data-feather="users" class="w-12 h-12 mx-auto text-accent-green-dark"></i>
                        <p class="text-4xl font-black mt-4">7.1K</p>
                        <h4 class="font-semibold mt-2 text-slate-600 dark:text-slate-300" data-lang-key="fans_followers">Fans & Followers</h4>
                    </div>
                    <div class="kpi-infographic-item">
                        <i data-feather="share-2" class="w-12 h-12 mx-auto text-accent-green-dark"></i>
                        <p class="text-4xl font-black mt-4">123</p>
                        <h4 class="font-semibold mt-2 text-slate-600 dark:text-slate-300" data-lang-key="shares">Shares</h4>
                    </div>
                </div>
        
                <div class="mt-12 pt-8 border-t border-gray-200 dark:border-gray-700">
                    <h3 class="text-xl font-bold text-center mb-6" data-lang-key="strategic_insights">Strategic Insights</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 text-left max-w-4xl mx-auto">
                        <div class="card p-6 rounded-xl">
                            <h4 class="font-bold flex items-center"><i data-feather="zap" class="ltr:mr-2 rtl:ml-2 text-accent-yellow"></i><span data-lang-key="insight_resonance_title">High-Resonance Content</span></h4>
                            <p class="mt-2 text-slate-600 dark:text-slate-300" data-lang-key="insight_resonance_content">An engagement rate of <strong>23.35%</strong> is exceptional. It validates that our content strategy, focusing on educational and high-quality visuals, deeply resonates with the target farming community, turning passive viewers into active participants.</p>
                        </div>
                        <div class="card p-6 rounded-xl">
                            <h4 class="font-bold flex items-center"><i data-feather="award" class="ltr:mr-2 rtl:ml-2 text-accent-yellow"></i><span data-lang-key="insight_authority_title">Building Authority & Trust</span></h4>
                            <p class="mt-2 text-slate-600 dark:text-slate-300" data-lang-key="insight_authority_content">Achieving <strong>7,100 followers</strong> and <strong>123 shares</strong> in a short period demonstrates rapid community growth and trust. Farmers are not only following but are also endorsing our content by sharing it with their networks, amplifying our reach organically.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="channel-performance" class="pt-24">
            <h2 class="section-title" data-lang-key="channel_perf_title">Channel Performance Breakdown</h2>
            <p class="section-subtitle" data-lang-key="channel_perf_subtitle">Diving deeper into the data reveals how each platform contributes to our overall success. This allows us to optimize our strategy and double down on what works.</p>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Facebook -->
                <div class="card p-6 rounded-xl shadow-lg border-t-4 border-blue-600">
                    <h4 class="text-xl font-bold mb-4 flex items-center"><i data-feather="facebook" class="ltr:mr-3 rtl:ml-3 text-blue-600"></i><span data-lang-key="fb_perf_title">Facebook Performance</span></h4>
                    <ul class="space-y-3">
                        <li class="flex items-center"><span data-lang-key="fans">Fans</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg">6,922</span></li>
                        <li class="flex items-center"><span data-lang-key="new_followers">New Followers</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg text-green-500">+5</span></li>
                        <li class="flex items-center"><span data-lang-key="impressions">Impressions</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg">65,918</span></li>
                        <li class="flex items-center"><span data-lang-key="engagement">Engagement</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg" data-lang-key="high">High</span></li>
                    </ul>
                </div>
                <!-- Instagram -->
                <div class="card p-6 rounded-xl shadow-lg border-t-4 border-pink-500">
                    <h4 class="text-xl font-bold mb-4 flex items-center"><i data-feather="instagram" class="ltr:mr-3 rtl:ml-3 text-pink-500"></i><span data-lang-key="ig_perf_title">Instagram Performance</span></h4>
                    <ul class="space-y-3">
                        <li class="flex items-center"><span data-lang-key="followers">Followers</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg">153</span></li>
                        <li class="flex items-center"><span data-lang-key="new_followers">New Followers</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg text-green-500">+153</span></li>
                        <li class="flex items-center"><span data-lang-key="impressions">Impressions</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg">2,853</span></li>
                        <li class="flex items-center"><span data-lang-key="engagement">Engagement</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg" data-lang-key="very_high">Very High</span></li>
                    </ul>
                </div>
                <!-- LinkedIn -->
                <div class="card p-6 rounded-xl shadow-lg border-t-4 border-blue-800">
                     <h4 class="text-xl font-bold mb-4 flex items-center"><i data-feather="linkedin" class="ltr:mr-3 rtl:ml-3 text-blue-800"></i><span data-lang-key="li_perf_title">LinkedIn Performance</span></h4>
                    <ul class="space-y-3">
                        <li class="flex items-center"><span data-lang-key="followers">Followers</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg">40</span></li>
                        <li class="flex items-center"><span data-lang-key="new_followers">New Followers</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg text-green-500">+1</span></li>
                        <li class="flex items-center"><span data-lang-key="impressions">Impressions</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg">1</span></li>
                        <li class="flex items-center"><span data-lang-key="engagement">Engagement</span>:<span class="font-bold ltr:ml-auto rtl:mr-auto text-lg" data-lang-key="moderate">Moderate</span></li>
                    </ul>
                </div>
            </div>
             <div class="mt-8 pt-8 border-t border-gray-200 dark:border-gray-700">
                <h3 class="text-xl font-bold text-center mb-4" data-lang-key="channel_insight_title">Channel Insights</h3>
                <p class="text-center text-slate-600 dark:text-slate-300 max-w-3xl mx-auto" data-lang-key="channel_insight_content"><strong>Facebook</strong> is our bedrock, providing massive reach and a stable community. <strong>Instagram</strong> is our growth engine, attracting a highly engaged new audience with visual content. <strong>LinkedIn</strong> is in its foundational stage, poised for strategic B2B outreach. This multi-platform approach ensures we are building both broad awareness and deep, targeted connections.</p>
            </div>
        </section>

        <section id="strategy" class="pt-24">
             <h2 class="section-title" data-lang-key="strategy_title">Channel Strategy & Regional Focus</h2>
            <p class="section-subtitle" data-lang-key="strategy_subtitle">A tailored approach for each market is crucial. We prioritize platforms based on user demographics and their alignment with B2B and B2C objectives.</p>
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div id="world-map-container" class="lg:col-span-2 card p-2 sm:p-6 rounded-2xl shadow-lg flex items-center justify-center">
                    <div id="map-tooltip"></div>
                    <div id="world-map" class="w-full h-full"></div>
                </div>
                <div class="card p-6 rounded-2xl shadow-lg">
                    <div class="flex justify-between items-center bg-gray-100 dark:bg-gray-700 p-1 rounded-full">
                         <button class="tab-button active w-1/3" data-country="sd" data-lang-key="sudan">Sudan</button>
                         <button class="tab-button w-1/3" data-country="om" data-lang-key="oman">Oman</button>
                         <button class="tab-button w-1/3" data-country="ug" data-lang-key="uganda">Uganda</button>
                    </div>
                    <div id="channel-priorities" class="mt-4 space-y-3"></div>
                    <div id="channel-insights" class="mt-4 pt-4 border-t border-gray-200 dark:border-gray-700">
                       <!-- Dynamic insights here -->
                    </div>
                </div>
            </div>
        </section>

        <section id="creatives" class="pt-24">
            <h2 class="section-title" data-lang-key="creatives_title">Creative Content Showcase</h2>
            <p class="section-subtitle" data-lang-key="creatives_subtitle">We'll create compelling content that tells the SeedTech story, from farmer successes to the technology behind the harvest.</p>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div class="card rounded-2xl shadow-lg overflow-hidden group">
                    <img src="https://placehold.co/600x400/C8DF52/0A7029?text=Grow+%26+Win" alt="Competition visual" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <span class="text-sm font-bold" style="color:var(--accent-green-mid)" data-lang-key="creative1_type">COMPETITION</span>
                        <h4 class="font-bold text-lg mt-1" data-lang-key="creative1_title">"Grow & Win" Contest</h4>
                        <p class="text-sm mt-2 text-slate-600 dark:text-slate-300" data-lang-key="creative1_desc">User-generated content campaign to showcase successful harvests and reward our community with valuable agri-kits.</p>
                    </div>
                </div>
                <div class="card rounded-2xl shadow-lg overflow-hidden group">
                     <img src="https://placehold.co/600x400/FEDE00/0A7029?text=Success+Story" alt="Farmer success story" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <span class="text-sm font-bold" style="color: var(--accent-yellow)" data-lang-key="creative2_type">SUCCESS STORY</span>
                        <h4 class="font-bold text-lg mt-1" data-lang-key="creative2_title">Farmer Testimonials</h4>
                        <p class="text-sm mt-2 text-slate-600 dark:text-slate-300" data-lang-key="creative2_desc">"With Kiara seeds, my yield increased by 40%. SeedTech's support was invaluable." - A. Hassan, Gezira</p>
                    </div>
                </div>
                 <div class="card rounded-2xl shadow-lg overflow-hidden group">
                    <img src="https://placehold.co/600x400/9ABA12/ffffff?text=Visual+Post" alt="Lush green field" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <span class="text-sm font-bold" style="color: var(--accent-green-mid)" data-lang-key="creative3_type">VISUAL POST</span>
                        <h4 class="font-bold text-lg mt-1" data-lang-key="creative3_title">Highlighting Quality</h4>
                        <p class="text-sm mt-2 text-slate-600 dark:text-slate-300" data-lang-key="creative3_desc">Stunning visuals of healthy crops, drone footage of fields, and behind-the-scenes at our research facilities.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="planning" class="pt-24">
            <h2 class="section-title" data-lang-key="planning_title">Interactive Content Calendar</h2>
            <p class="section-subtitle" data-lang-key="planning_subtitle">A great strategy requires disciplined execution. Click on any content type below to see a creative sample of what we'll produce.</p>
            <div class="card p-6 rounded-2xl shadow-lg">
                <div class="calendar-grid">
                    <div class="calendar-day-header text-center" data-lang-key="day_mon">Mon</div><div class="calendar-day-header text-center" data-lang-key="day_tue">Tue</div><div class="calendar-day-header text-center" data-lang-key="day_wed">Wed</div><div class="calendar-day-header text-center" data-lang-key="day_thu">Thu</div><div class="calendar-day-header text-center" data-lang-key="day_fri">Fri</div><div class="calendar-day-header text-center" data-lang-key="day_sat">Sat</div><div class="calendar-day-header text-center" data-lang-key="day_sun">Sun</div>
                    <div class="calendar-day"><div class="post-pill bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-200" data-type="blog" data-lang-key="content_blog">Blog Post</div></div>
                    <div class="calendar-day"></div>
                    <div class="calendar-day"><div class="post-pill bg-purple-100 dark:bg-purple-900 text-purple-800 dark:text-purple-200" data-type="qanda" data-lang-key="content_qanda">Farmer Q&A</div></div>
                    <div class="calendar-day"></div>
                    <div class="calendar-day"><div class="post-pill bg-red-100 dark:bg-red-900 text-red-800 dark:text-red-200" data-type="youtube" data-lang-key="content_youtube">YouTube Video</div></div>
                    <div class="calendar-day"><div class="post-pill bg-yellow-100 dark:bg-yellow-900 text-yellow-800 dark:text-yellow-200" data-type="testimonial" data-lang-key="content_testimonial">Testimonial</div></div>
                    <div class="calendar-day"></div>
                    <div class="calendar-day"><div class="post-pill bg-pink-100 dark:bg-pink-900 text-pink-800 dark:text-pink-200" data-type="tiktok" data-lang-key="content_tiktok">TikTok Tip</div></div>
                    <div class="calendar-day"></div>
                    <div class="calendar-day"><div class="post-pill bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-200" data-type="blog" data-lang-key="content_blog">Blog Post</div></div>
                    <div class="calendar-day"></div>
                    <div class="calendar-day"><div class="post-pill bg-indigo-100 dark:bg-indigo-900 text-indigo-800 dark:text-indigo-200" data-type="reel" data-lang-key="content_reel">IG Reel</div></div>
                    <div class="calendar-day"></div>
                    <div class="calendar-day"></div>
                </div>
            </div>
        </section>

        <section id="budget" class="pt-24">
            <h2 class="section-title" data-lang-key="budget_title">Dynamic & Transparent Investment</h2>
            <p class="section-subtitle" data-lang-key="budget_subtitle">Our adjustable budget model ensures your investment is allocated efficiently for maximum ROI, with the flexibility to scale based on performance.</p>
            <div class="card p-8 rounded-2xl shadow-lg">
                <div class="flex flex-col lg:flex-row items-center justify-between gap-8">
                    <div class="w-full lg:w-1/2">
                        <label for="budget-slider" class="block font-bold text-lg mb-2" data-lang-key="budget_slider_label">Adjust Total Monthly Investment</label>
                        <input id="budget-slider" type="range" min="0" max="5000" value="0" step="100" class="w-full h-3 bg-gray-200 dark:bg-gray-600 rounded-lg appearance-none cursor-pointer">
                        <div class="flex justify-between text-sm text-slate-500 dark:text-slate-400 mt-2"><span>$0</span><span>$5,000</span></div>
                        <div id="budget-breakdown" class="mt-6 space-y-2 text-lg"></div>
                    </div>
                    <div class="w-full lg:w-1/2 h-72"><canvas id="budget-chart-main"></canvas></div>
                </div>
            </div>
        </section>

        <section id="recommendations" class="pt-24">
            <h2 class="section-title" data-lang-key="notes_title">Recommendations & Notes by SeedTech Team</h2>
            <p class="section-subtitle" data-lang-key="notes_subtitle">This is a collaborative space. Please use the area below to add your notes, questions, and feedback for our team to review.</p>
            <div class="card max-w-4xl mx-auto p-8 rounded-2xl shadow-lg">
                <textarea id="notes-area" class="text-slate-600 dark:text-slate-300" data-lang-key="notes_placeholder" placeholder="Type your notes here..."></textarea>
                <div class="mt-6 text-center">
                    <button id="send-notes-btn" class="bg-accent-green-dark text-white font-bold py-3 px-8 rounded-full hover:bg-accent-green-mid transition-colors disabled:opacity-50 disabled:cursor-not-allowed" data-lang-key="submit_notes" disabled>Submit Notes via Email</button>
                </div>
            </div>
        </section>

        <section id="contact" class="pt-24 text-center">
            <h2 class="section-title" data-lang-key="contact_title">Your Digital Growth Partner</h2>
            <p class="section-subtitle" data-lang-key="contact_subtitle">We don't just manage social media; we build digital ecosystems that drive business growth. Let's start cultivating your future today.</p>
            <div class="card max-w-4xl mx-auto p-8 rounded-2xl shadow-lg brand-gradient-bg">
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                    <a href="tel:+905433400087" class="bg-white/20 p-4 rounded-lg flex flex-col items-center justify-center text-white hover:bg-white/30 hover:-translate-y-1 transition-all">
                        <i data-feather="phone" class="w-8 h-8"></i><span class="mt-2 font-semibold" data-lang-key="contact_call">Call Us</span>
                    </a>
                    <a href="https://wa.me/249963777777" target="_blank" class="bg-white/20 p-4 rounded-lg flex flex-col items-center justify-center text-white hover:bg-white/30 hover:-translate-y-1 transition-all">
                        <i data-feather="message-circle" class="w-8 h-8"></i><span class="mt-2 font-semibold" data-lang-key="contact_whatsapp">WhatsApp</span>
                    </a>
                     <a href="mailto:care@branddi.co.site" class="bg-white/20 p-4 rounded-lg flex flex-col items-center justify-center text-white hover:bg-white/30 hover:-translate-y-1 transition-all">
                        <i data-feather="mail" class="w-8 h-8"></i><span class="mt-2 font-semibold" data-lang-key="contact_email">Email Us</span>
                    </a>
                    <a href="#" class="bg-brand-orange-footer text-white p-4 rounded-lg flex flex-col items-center justify-center hover:shadow-xl hover:opacity-90 hover:-translate-y-1 transition-all">
                        <i data-feather="arrow-right-circle" class="w-8 h-8"></i><span class="mt-2 font-semibold" data-lang-key="contact_start">Get Started</span>
                    </a>
                </div>
            </div>
        </section>
    </main>

    <!-- Content Modal -->
    <div id="content-modal-overlay">
        <div id="content-modal">
            <button id="modal-close-btn" class="absolute top-4 right-4 text-slate-500 hover:text-slate-800 dark:hover:text-white">&times;</button>
            <h3 id="modal-title" class="text-2xl font-bold mb-4"></h3>
            <div id="modal-content" class="text-slate-600 dark:text-slate-300"></div>
        </div>
    </div>


    <script>
        document.addEventListener('DOMContentLoaded', function () {
            // --- GLOBAL VARIABLES, DATA & TRANSLATIONS ---
            const html = document.documentElement;
            const budgetChartCanvas = document.getElementById('budget-chart-main');
            const assessmentChartCanvas = document.getElementById('assessment-chart');
            
            // --- DATA OBJECTS ---
            const assessmentData = {
                sd: { insight_key: 'assessment_insight_sd' },
                ug: { insight_key: 'assessment_insight_ug' },
                om: { insight_key: 'assessment_insight_om' }
            };

            const contentModalData = {
                blog: { title_key: 'content_modal_blog_title', content_key: 'content_modal_blog_content'},
                qanda: { title_key: 'content_modal_qanda_title', content_key: 'content_modal_qanda_content'},
                youtube: { title_key: 'content_modal_youtube_title', content_key: 'content_modal_youtube_content'},
                testimonial: { title_key: 'content_modal_testimonial_title', content_key: 'content_modal_testimonial_content'},
                tiktok: { title_key: 'content_modal_tiktok_title', content_key: 'content_modal_tiktok_content'},
                reel: { title_key: 'content_modal_reel_title', content_key: 'content_modal_reel_content'}
            };

            const channelInsightsData = {
                sd: "sd_channel_insight",
                om: "om_channel_insight",
                ug: "ug_channel_insight"
            };

            // --- TRANSLATIONS OBJECT ---
            const translations = {
                // English Translations
                en: {
                    // Nav
                    nav_assessment: "Assessment", nav_snapshots: "Snapshots", nav_channels: "Channels", nav_strategy: "Strategy", nav_planning: "Planning", nav_budget: "Budget",
                    // Hero
                    main_title: 'Cultivating <span class="gradient-text">Digital Growth</span> for SeedTech',
                    main_subtitle: 'An advanced interactive proposal by <span class="font-semibold">Brandi</span> to establish SeedTech as the premier agricultural solutions provider.',
                    // Foundation
                    foundation_title: "Brand Foundation", foundation_subtitle: "Our strategy is built upon SeedTech's core identity, amplifying its strengths across all digital channels.",
                    profile_title: "Company Profile", profile_content: "Since 2012, SeedTech has partnered with Technisem to improve agricultural productivity via high-quality seeds and agronomic expertise. Now expanding from Sudan to Oman and Uganda, SeedTech is a visionary leader in regional food security.",
                    pillars_title: "Brand Identity Pillars", pillar_quality: '<strong>Quality:</strong> Uncompromising excellence in every seed and consultation.', pillar_expertise: '<strong>Expertise:</strong> Demonstrating deep technical knowledge and dependable support.', pillar_innovation: '<strong>Innovation:</strong> Highlighting premium varieties and modern Agri-Tech.', pillar_education: '<strong>Education:</strong> Making complex agronomy accessible and practical for all.',
                    // Assessment
                    assessment_title: "SeedTech Current Initial Assessment", assessment_subtitle: "To forge a successful path forward, we must first understand the starting point. This initial assessment establishes the baseline digital footprint and sets our 6-month growth targets.",
                    website: "Website",
                    assessment_interactive_title: "Interactive Channel Analysis",
                    assessment_insight_sd: `<h4 class="text-lg font-bold mb-2">Analysis: Sudan</h4><p class="text-slate-600 dark:text-slate-300">SeedTech Sudan has a formidable presence on <strong>Facebook (11k)</strong>, making it the cornerstone of our strategy. The significant following on <strong>LinkedIn (881)</strong> indicates strong B2B potential. Other platforms are nascent, representing an opportunity to capture a younger demographic by leveraging the established brand trust.</p>`,
                    assessment_insight_ug: `<h4 class="text-lg font-bold mb-2">Analysis: Uganda (Agriganda)</h4><p class="text-slate-600 dark:text-slate-300">The digital presence in Uganda is in its infancy, presenting a ground-floor opportunity. Interestingly, <strong>TikTok (16)</strong> leads slightly, suggesting a potential for rapid, viral growth with short-form video. Our strategy will be to build foundational audiences on Facebook and Instagram while experimenting with engaging content for the emerging TikTok user base.</p>`,
                    assessment_insight_om: `<h4 class="text-lg font-bold mb-2">Analysis: Oman (WOGUD)</h4><p class="text-slate-600 dark:text-slate-300">Oman is a clean slate. With a small but present audience on <strong>Facebook (18)</strong> and <strong>TikTok (16)</strong>, we can test which platform gains traction fastest. The strategy here will be agile, focusing on establishing the brand, identifying the most responsive local audience, and then scaling efforts on the winning channels.</p>`,
                    // Snapshots
                    snapshots_title: "Performance Insights Snapshots",
                    impressions: "Impressions", engagement_rate: "Engagement Rate", fans_followers: "Fans & Followers", shares: "Shares",
                    strategic_insights: "Strategic Insights",
                    insight_resonance_title: "High-Resonance Content", insight_resonance_content: "An engagement rate of <strong>23.35%</strong> is exceptional. It validates that our content strategy, focusing on educational and high-quality visuals, deeply resonates with the target farming community, turning passive viewers into active participants.",
                    insight_authority_title: "Building Authority & Trust", insight_authority_content: "Achieving <strong>7,100 followers</strong> and <strong>123 shares</strong> in a short period demonstrates rapid community growth and trust. Farmers are not only following but are also endorsing our content by sharing it with their networks, amplifying our reach organically.",
                    // Channel Performance
                    channel_perf_title: "Channel Performance Breakdown", channel_perf_subtitle: "Diving deeper into the data reveals how each platform contributes to our overall success. This allows us to optimize our strategy and double down on what works.",
                    fb_perf_title: "Facebook Performance", fans: "Fans", new_followers: "New Followers", followers: "Followers", engagement: "Engagement", high: "High",
                    ig_perf_title: "Instagram Performance", very_high: "Very High",
                    li_perf_title: "LinkedIn Performance", moderate: "Moderate",
                    channel_insight_title: "Channel Insights", channel_insight_content: "<strong>Facebook</strong> is our bedrock, providing massive reach and a stable community. <strong>Instagram</strong> is our growth engine, attracting a highly engaged new audience with visual content. <strong>LinkedIn</strong> is in its foundational stage, poised for strategic B2B outreach. This multi-platform approach ensures we are building both broad awareness and deep, targeted connections.",
                    // Regional Strategy
                    strategy_title: "Channel Strategy & Regional Focus", strategy_subtitle: "A tailored approach for each market is crucial. We prioritize platforms based on user demographics and their alignment with B2B and B2C objectives.",
                    sudan: "Sudan", oman: "Oman", uganda: "Uganda",
                    sd_channel_insight: "Sudan's digital landscape is dominated by <strong>Facebook</strong> and <strong>WhatsApp</strong>. Our strategy focuses on leveraging the existing Facebook community for high engagement and using WhatsApp for direct farmer communication and lead nurturing.",
                    om_channel_insight: "Oman has a high internet penetration rate with strong usage of <strong>Instagram</strong> for visual branding and <strong>LinkedIn</strong> for B2B connections. We will prioritize these platforms for establishing a premium brand image and connecting with commercial partners.",
                    ug_channel_insight: "In Uganda, <strong>Facebook</strong> remains the most popular platform, making it essential for broad-reach campaigns. The rapid growth of <strong>YouTube</strong> for educational content presents a key opportunity to position SeedTech as an agricultural authority.",
                    // Creatives
                    creatives_title: "Creative Content Showcase", creatives_subtitle: "We'll create compelling content that tells the SeedTech story, from farmer successes to the technology behind the harvest.",
                    creative1_type: "COMPETITION", creative1_title: '"Grow & Win" Contest', creative1_desc: "User-generated content campaign to showcase successful harvests and reward our community with valuable agri-kits.",
                    creative2_type: "SUCCESS STORY", creative2_title: 'Farmer Testimonials', creative2_desc: '"With Kiara seeds, my yield increased by 40%. SeedTech\'s support was invaluable." - A. Hassan, Gezira',
                    creative3_type: "VISUAL POST", creative3_title: "Highlighting Quality", creative3_desc: "Stunning visuals of healthy crops, drone footage of fields, and behind-the-scenes at our research facilities.",
                    // Planning
                    planning_title: "Interactive Content Calendar", planning_subtitle: "A great strategy requires disciplined execution. Click on any content type below to see a creative sample of what we'll produce.",
                    day_mon: "Mon", day_tue: "Tue", day_wed: "Wed", day_thu: "Thu", day_fri: "Fri", day_sat: "Sat", day_sun: "Sun",
                    content_blog: "Blog Post", content_qanda: "Farmer Q&A", content_youtube: "YouTube Video", content_testimonial: "Testimonial", content_tiktok: "TikTok Tip", content_reel: "IG Reel",
                    // Calendar Modal Content
                    content_modal_blog_title: 'Blog Post: "5 Ways to Boost Tomato Yield in Dry Climates"', content_modal_blog_content: `<p>A practical, SEO-optimized article addressing a key pain point for farmers. It will include high-quality images, actionable tips, and link to relevant SeedTech products like our drought-resistant tomato varieties.</p><p class="mt-2"><strong>Goal:</strong> Drive organic traffic, establish expertise, and generate leads.</p>`,
                    content_modal_qanda_title: 'Live Q&A: "Ask Our Agronomist Anything"', content_modal_qanda_content: `<p>A live session on Facebook and Instagram with a SeedTech agronomist. We'll promote it in advance to gather questions and engage directly with the community, answering their specific challenges in real-time.</p><p class="mt-2"><strong>Goal:</strong> Build community trust and demonstrate technical expertise.</p>`,
                    content_modal_youtube_title: 'YouTube Video: "Step-by-Step Guide to Proper Drip Irrigation Setup"', content_modal_youtube_content: `<p>A high-quality, 5-7 minute tutorial video showing farmers how to properly install and maintain a drip irrigation system. The video will visually showcase the benefits and feature SeedTech branding subtly.</p><p class="mt-2"><strong>Goal:</strong> Provide high-value educational content and grow our YouTube subscriber base.</p>`,
                    content_modal_testimonial_title: 'Testimonial Post: "Farmer Spotlight"', content_modal_testimonial_content: `<p>A carousel post on Instagram and Facebook featuring a successful farmer. It will include a powerful quote, a high-quality photo of them with their harvest, and key results (e.g., "40% yield increase with Kiara seeds").</p><p class="mt-2"><strong>Goal:</strong> Provide social proof and build relatable brand stories.</p>`,
                    content_modal_tiktok_title: 'TikTok Tip: "One Simple Trick for Healthier Seedlings"', content_modal_tiktok_content: `<p>A quick, 15-second video showing a simple hack for improving seedling health. It will use trending audio and fast-paced edits to capture attention and encourage shares.</p><p class="mt-2"><strong>Goal:</strong> Drive viral reach and engage a younger audience.</p>`,
                    content_modal_reel_title: 'Instagram Reel: "From Seed to Harvest in 30 Seconds"', content_modal_reel_content: `<p>A visually stunning time-lapse video showing the entire lifecycle of a plant grown from a SeedTech seed. It will be set to uplifting, trending music to create an emotional connection and highlight the quality of our products.</p><p class="mt-2"><strong>Goal:</strong> Increase brand awareness and create highly shareable content.</p>`,
                    // Budget
                    budget_title: "Dynamic & Transparent Investment", budget_subtitle: "Our adjustable budget model ensures your investment is allocated efficiently for maximum ROI, with the flexibility to scale based on performance.",
                    budget_slider_label: "Adjust Total Monthly Investment", budget_total: "Total Investment:", budget_ads: "Paid Advertising", budget_content: "Content & Mgmt", budget_tools: "Tools & Software",
                    // Notes
                    notes_title: "Recommendations & Notes by SeedTech Team", notes_subtitle: "This is a collaborative space. Please use the area below to add your notes, questions, and feedback for our team to review.",
                    notes_placeholder: "Type your notes here...",
                    submit_notes: "Submit Notes via Email",
                    // Contact
                    contact_title: "Your Digital Growth Partner", contact_subtitle: "We don't just manage social media; we build digital ecosystems that drive business growth. Let's start cultivating your future today.",
                    contact_call: "Call Us", contact_whatsapp: "WhatsApp", contact_email: "Email Us", contact_start: "Get Started",
                    // Channel Names
                    facebook: "Facebook", linkedin: "LinkedIn", instagram: "Instagram", youtube: "YouTube", tiktok: "TikTok",
                },
                // Arabic Translations
                ar: {
                    // Nav
                    nav_assessment: "التقييم", nav_snapshots: "لقطات الأداء", nav_channels: "القنوات", nav_strategy: "الاستراتيجية", nav_planning: "التخطيط", nav_budget: "الميزانية",
                    // Hero
                    main_title: 'زراعة <span class="gradient-text">النمو الرقمي</span> لـ SeedTech',
                    main_subtitle: 'مقترح تفاعلي متقدم من <span class="font-semibold">Brandi</span> لترسيخ SeedTech كمزود رائد للحلول الزراعية.',
                    // Foundation
                    foundation_title: "أساس العلامة التجارية", foundation_subtitle: "تعتمد استراتيجيتنا على هوية SeedTech الأساسية، معززة نقاط قوتها عبر جميع القنوات الرقمية.",
                    profile_title: "ملف الشركة", profile_content: "منذ عام 2012، دخلت SeedTech في شراكة مع Technisem لتحسين الإنتاجية الزراعية عبر بذور عالية الجودة وخبرة زراعية. الآن تتوسع من السودان إلى عمان وأوغندا، وتعتبر SeedTech رائدة ذات رؤية في الأمن الغذائي الإقليمي.",
                    pillars_title: "أركان هوية العلامة التجارية", pillar_quality: '<strong>الجودة:</strong> تميز لا هوادة فيه في كل بذرة واستشارة.', pillar_expertise: '<strong>الخبرة:</strong> إظهار معرفة تقنية عميقة ودعم يمكن الاعتماد عليه.', pillar_innovation: '<strong>الابتكار:</strong> تسليط الضوء على الأصناف المتميزة والتكنولوجيا الزراعية الحديثة.', pillar_education: '<strong>التعليم:</strong> جعل علوم الزراعة المعقدة متاحة وعملية للجميع.',
                    // Assessment
                    assessment_title: "التقييم المبدئي الحالي لـ SeedTech", assessment_subtitle: "لرسم مسار ناجح للمستقبل، يجب أن نفهم نقطة البداية أولاً. يحدد هذا التقييم المبدئي البصمة الرقمية الأساسية ويضع أهداف النمو لمدة 6 أشهر.",
                    website: "الموقع الإلكتروني",
                    assessment_interactive_title: "تحليل تفاعلي للقنوات",
                    assessment_insight_sd: `<h4 class="text-lg font-bold mb-2">تحليل: السودان</h4><p class="text-slate-600 dark:text-slate-300">تتمتع SeedTech السودان بحضور هائل على <strong>فيسبوك (11 ألف)</strong>، مما يجعله حجر الزاوية في استراتيجيتنا. ويشير العدد الكبير من المتابعين على <strong>لينكد إن (881)</strong> إلى إمكانات قوية للأعمال التجارية (B2B). المنصات الأخرى ناشئة، مما يمثل فرصة لجذب فئة ديموغرافية أصغر سناً من خلال الاستفادة من ثقة العلامة التجارية القائمة.</p>`,
                    assessment_insight_ug: `<h4 class="text-lg font-bold mb-2">تحليل: أوغندا (Agriganda)</h4><p class="text-slate-600 dark:text-slate-300">الحضور الرقمي في أوغندا في مراحله الأولى، مما يتيح فرصة للانطلاق من الصفر. ومن المثير للاهتمام أن <strong>تيك توك (16)</strong> يتصدر بفارق ضئيل، مما يشير إلى إمكانية تحقيق نمو سريع وانتشار واسع من خلال الفيديو القصير. ستكون استراتيجيتنا هي بناء جماهير أساسية على فيسبوك وإنستغرام مع تجربة محتوى جذاب لقاعدة مستخدمي تيك توك الناشئة.</p>`,
                    assessment_insight_om: `<h4 class="text-lg font-bold mb-2">تحليل: عمان (WOGUD)</h4><p class="text-slate-600 dark:text-slate-300">عمان تمثل صفحة بيضاء. مع جمهور صغير ولكنه موجود على <strong>فيسبوك (18)</strong> و<strong>تيك توك (16)</strong>، يمكننا اختبار أي منصة تكتسب زخماً أسرع. ستكون الاستراتيجية هنا مرنة، مع التركيز على ترسيخ العلامة التجارية، وتحديد الجمهور المحلي الأكثر استجابة، ثم توسيع نطاق الجهود على القنوات الفائزة.</p>`,
                    // Snapshots
                    snapshots_title: "لقطات الأداء",
                    impressions: "مرات الظهور", engagement_rate: "معدل التفاعل", fans_followers: "المعجبون والمتابعون", shares: "المشاركات",
                    strategic_insights: "رؤى استراتيجية",
                    insight_resonance_title: "محتوى عالي الصدى", insight_resonance_content: "معدل تفاعل بنسبة <strong>23.35%</strong> هو رقم استثنائي. هذا يؤكد أن استراتيجية المحتوى الخاصة بنا، التي تركز على المرئيات التعليمية وعالية الجودة، تلقى صدى عميقًا لدى المجتمع الزراعي المستهدف، وتحول المشاهدين السلبيين إلى مشاركين نشطين.",
                    insight_authority_title: "بناء المصداقية والثقة", insight_authority_content: "تحقيق <strong>7,100 متابع</strong> و <strong>123 مشاركة</strong> في فترة قصيرة يوضح نموًا سريعًا للمجتمع وثقة. لا يتابع المزارعون فقط، بل يؤيدون المحتوى الخاص بنا من خلال مشاركته مع شبكاتهم، مما يضخم وصولنا بشكل عضوي.",
                    // Channel Performance
                    channel_perf_title: "أداء القنوات بالتفصيل", channel_perf_subtitle: "الغوص أعمق في البيانات يكشف كيف تساهم كل منصة في نجاحنا العام. هذا يسمح لنا بتحسين استراتيجيتنا والتركيز على ما ينجح.",
                    fb_perf_title: "أداء فيسبوك", fans: "المعجبون", new_followers: "متابعون جدد", followers: "المتابعون", engagement: "التفاعل", high: "مرتفع",
                    ig_perf_title: "أداء انستغرام", very_high: "مرتفع جداً",
                    li_perf_title: "أداء لينكدإن", moderate: "متوسط",
                    channel_insight_title: "رؤى القنوات", channel_insight_content: "<strong>فيسبوك</strong> هو أساسنا، حيث يوفر وصولاً هائلاً ومجتمعاً مستقراً. <strong>انستغرام</strong> هو محرك نمونا، حيث يجذب جمهورًا جديدًا شديد التفاعل بالمحتوى المرئي. <strong>لينكدإن</strong> في مرحلته التأسيسية، مهيأ للتواصل الاستراتيجي بين الشركات (B2B). يضمن هذا النهج متعدد المنصات أننا نبني وعيًا واسعًا واتصالات عميقة ومستهدفة.",
                    // Regional Strategy
                    strategy_title: "استراتيجية القنوات والتركيز الإقليمي", strategy_subtitle: "النهج المخصص لكل سوق أمر بالغ الأهمية. نحن نعطي الأولوية للمنصات بناءً على التركيبة السكانية للمستخدمين وتوافقها مع أهداف B2B و B2C.",
                    sudan: "السودان", oman: "عمان", uganda: "أوغندا",
                    sd_channel_insight: "يهيمن <strong>فيسبوك</strong> و<strong>واتساب</strong> على المشهد الرقمي في السودان. تركز استراتيجيتنا على الاستفادة من مجتمع فيسبوك الحالي لتحقيق تفاعل عالٍ واستخدام واتساب للتواصل المباشر مع المزارعين ورعاية العملاء المحتملين.",
                    om_channel_insight: "تتمتع عمان بمعدل انتشار عالٍ للإنترنت مع استخدام قوي لـ <strong>انستغرام</strong> للعلامة التجارية المرئية و<strong>لينكدإن</strong> للتواصل بين الشركات (B2B). سنعطي الأولوية لهذه المنصات لترسيخ صورة علامة تجارية متميزة والتواصل مع الشركاء التجاريين.",
                    ug_channel_insight: "في أوغندا، يظل <strong>فيسبوك</strong> المنصة الأكثر شعبية، مما يجعله ضروريًا للحملات واسعة النطاق. يمثل النمو السريع لـ <strong>يوتيوب</strong> للمحتوى التعليمي فرصة رئيسية لوضع SeedTech كسلطة زراعية.",
                    // Creatives
                    creatives_title: "استعراض المحتوى الإبداعي", creatives_subtitle: "سننشئ محتوى مقنعًا يروي قصة SeedTech، من نجاحات المزارعين إلى التكنولوجيا وراء الحصاد.",
                    creative1_type: "مسابقة", creative1_title: 'مسابقة "ازرع واربح"', creative1_desc: "حملة محتوى من إنشاء المستخدمين لعرض الحصاد الناجح ومكافأة مجتمعنا بمجموعات زراعية قيمة.",
                    creative2_type: "قصة نجاح", creative2_title: 'شهادات المزارعين', creative2_desc: '"مع بذور كيارا، زاد محصولي بنسبة 40٪. كان دعم SeedTech لا يقدر بثمن." - أ. حسن، الجزيرة',
                    creative3_type: "منشور مرئي", creative3_title: "تسليط الضوء على الجودة", creative3_desc: "صور مذهلة للمحاصيل الصحية، لقطات بطائرات بدون طيار للحقول، وما وراء الكواليس في مرافقنا البحثية.",
                    // Planning
                    planning_title: "تقويم المحتوى التفاعلي", planning_subtitle: "تتطلب الاستراتيجية الرائعة تنفيذًا منضبطًا. انقر على أي نوع محتوى أدناه لمشاهدة عينة إبداعية مما سننتجه.",
                    day_mon: "إثن", day_tue: "ثلا", day_wed: "أرب", day_thu: "خمي", day_fri: "جمع", day_sat: "سبت", day_sun: "أحد",
                    content_blog: "منشور مدونة", content_qanda: "سؤال وجواب للمزارعين", content_youtube: "فيديو يوتيوب", content_testimonial: "شهادة", content_tiktok: "نصيحة تيك توك", content_reel: "ريل انستغرام",
                    // Calendar Modal Content
                    content_modal_blog_title: 'منشور مدونة: "5 طرق لزيادة محصول الطماطم في المناخات الجافة"', content_modal_blog_content: `<p>مقال عملي ومحسن لمحركات البحث يعالج نقطة ألم رئيسية للمزارعين. سيتضمن صورًا عالية الجودة ونصائح قابلة للتنفيذ وروابط لمنتجات SeedTech ذات الصلة مثل أصناف الطماطم المقاومة للجفاف.</p><p class="mt-2"><strong>الهدف:</strong> زيادة الزيارات العضوية، ترسيخ الخبرة، وتوليد عملاء محتملين.</p>`,
                    content_modal_qanda_title: 'جلسة سؤال وجواب مباشرة: "اسأل مهندسنا الزراعي أي شيء"', content_modal_qanda_content: `<p>جلسة مباشرة على فيسبوك وانستغرام مع مهندس زراعي من SeedTech. سنقوم بالترويج لها مسبقًا لجمع الأسئلة والتفاعل مباشرة مع المجتمع، والإجابة على تحدياتهم المحددة في الوقت الفعلي.</p><p class="mt-2"><strong>الهدف:</strong> بناء ثقة المجتمع وإظهار الخبرة التقنية.</p>`,
                    content_modal_youtube_title: 'فيديو يوتيوب: "دليل خطوة بخطوة لإعداد الري بالتنقيط بشكل صحيح"', content_modal_youtube_content: `<p>فيديو تعليمي عالي الجودة مدته 5-7 دقائق يوضح للمزارعين كيفية تركيب وصيانة نظام الري بالتنقيط بشكل صحيح. سيعرض الفيديو الفوائد بشكل مرئي ويتميز بعلامة SeedTech التجارية بمهارة.</p><p class="mt-2"><strong>الهدف:</strong> توفير محتوى تعليمي عالي القيمة وزيادة قاعدة مشتركينا على يوتيوب.</p>`,
                    content_modal_testimonial_title: 'منشور شهادة: "مزارع تحت الضوء"', content_modal_testimonial_content: `<p>منشور دوار (carousel) على انستغرام وفيسبوك يعرض مزارعًا ناجحًا. سيتضمن اقتباسًا قويًا، وصورة عالية الجودة له مع محصوله، ونتائج رئيسية (على سبيل المثال، "زيادة بنسبة 40٪ في المحصول مع بذور كيارا").</p><p class="mt-2"><strong>الهدف:</strong> تقديم دليل اجتماعي وبناء قصص علامة تجارية ذات صلة.</p>`,
                    content_modal_tiktok_title: 'نصيحة تيك توك: "خدعة بسيطة لشتلات أكثر صحة"', content_modal_tiktok_content: `<p>فيديو سريع مدته 15 ثانية يعرض حيلة بسيطة لتحسين صحة الشتلات. سيستخدم صوتًا رائجًا ومونتاج سريع لجذب الانتباه وتشجيع المشاركات.</p><p class="mt-2"><strong>الهدف:</strong> زيادة الوصول الفيروسي والتفاعل مع جمهور أصغر سناً.</p>`,
                    content_modal_reel_title: 'ريل انستغرام: "من البذرة إلى الحصاد في 30 ثانية"', content_modal_reel_content: `<p>فيديو مذهل بصريًا بتقنية الفاصل الزمني (time-lapse) يوضح دورة حياة نبات كاملة نمت من بذرة SeedTech. سيتم تعيينه على موسيقى راقية ورائجة لخلق اتصال عاطفي وتسليط الضوء على جودة منتجاتنا.</p><p class="mt-2"><strong>الهدف:</strong> زيادة الوعي بالعلامة التجارية وإنشاء محتوى قابل للمشاركة بشكل كبير.</p>`,
                    // Budget
                    budget_title: "استثمار ديناميكي وشفاف", budget_subtitle: "يضمن نموذج الميزانية القابل للتعديل لدينا تخصيص استثمارك بكفاءة لتحقيق أقصى عائد على الاستثمار، مع المرونة في التوسع بناءً على الأداء.",
                    budget_slider_label: "تعديل إجمالي الاستثمار الشهري", budget_total: "إجمالي الاستثمار:", budget_ads: "الإعلانات المدفوعة", budget_content: "المحتوى والإدارة", budget_tools: "الأدوات والبرامج",
                    // Notes
                    notes_title: "توصيات وملاحظات فريق SeedTech", notes_subtitle: "هذه مساحة تعاونية. يرجى استخدام المنطقة أدناه لإضافة ملاحظاتك وأسئلتك وتعليقاتك ليراجعها فريقنا.",
                    notes_placeholder: "اكتب ملاحظاتك هنا...",
                    submit_notes: "إرسال الملاحظات عبر البريد الإلكتروني",
                    // Contact
                    contact_title: "شريكك في النمو الرقمي", contact_subtitle: "نحن لا ندير وسائل التواصل الاجتماعي فقط؛ بل نبني أنظمة بيئية رقمية تدفع نمو الأعمال. لنبدأ في زراعة مستقبلك اليوم.",
                    contact_call: "اتصل بنا", contact_whatsapp: "واتساب", contact_email: "راسلنا", contact_start: "ابدأ الآن",
                    // Channel Names
                    facebook: "فيسبوك", linkedin: "لينكدإن", instagram: "انستغرام", youtube: "يوتيوب", tiktok: "تيك توك",
                }
            };
            
            const priorityLevels = ['High', 'Medium', 'Low', 'Potential'];
            const priorityColors = { High: 'bg-red-500', Medium: 'bg-yellow-500', Low: 'bg-blue-500', Potential: 'bg-gray-500' };

            // --- FUNCTION DEFINITIONS ---
            function setLanguage(lang) {
                const currentLang = translations[lang];
                document.querySelectorAll('[data-lang-key]').forEach(el => {
                    const key = el.dataset.langKey;
                    if (currentLang[key]) {
                        if (el.tagName === 'TEXTAREA' && el.hasAttribute('placeholder')) {
                            el.placeholder = currentLang[key];
                        } else {
                            el.innerHTML = currentLang[key];
                        }
                    }
                });

                html.lang = lang;
                html.dir = lang === 'ar' ? 'rtl' : 'ltr';

                document.getElementById('lang-en').classList.toggle('active', lang === 'en');
                document.getElementById('lang-ar').classList.toggle('active', lang === 'ar');
                
                localStorage.setItem('preferred_language', lang);
                
                // Re-render dynamic components
                applyTheme(localStorage.getItem('theme') || 'light');
                const activeCountry = document.querySelector('#strategy .tab-button.active').dataset.country;
                updateChannelPriorities(activeCountry);
            }
            
            function applyTheme(theme) {
                html.classList.toggle('dark', theme === 'dark');
                if(window.budgetChart) window.budgetChart.destroy();
                updateBudget(document.getElementById('budget-slider').value);
                
                if(window.assessmentChart) window.assessmentChart.destroy();
                const activeRegionBtn = document.querySelector('#assessment .kpi-selector-btn.active');
                if (activeRegionBtn) {
                    renderAssessmentChart(activeRegionBtn.dataset.region);
                }
            }
            
            function renderAssessmentChart(region) {
                const lang = localStorage.getItem('preferred_language') || 'en';
                const isDark = html.classList.contains('dark');
                const textColor = isDark ? '#9CA3AF' : '#4B5563';
                const gridColor = isDark ? 'rgba(75, 85, 99, 0.5)' : 'rgba(229, 231, 235, 0.5)';
                
                const regionData = {
                    sd: { labels: ['Facebook', 'LinkedIn', 'Instagram', 'YouTube', 'TikTok'], data: [11000, 881, 182, 125, 28] },
                    ug: { labels: ['TikTok', 'Facebook', 'Instagram'], data: [16, 8, 2] },
                    om: { labels: ['Facebook', 'TikTok', 'Instagram'], data: [18, 16, 4] }
                };
                
                const insightKey = assessmentData[region].insight_key;
                document.getElementById('assessment-insights').innerHTML = translations[lang][insightKey] || '';
                
                if (window.assessmentChart) window.assessmentChart.destroy();
                
                window.assessmentChart = new Chart(assessmentChartCanvas.getContext('2d'), {
                    type: 'bar',
                    data: {
                        labels: regionData[region].labels.map(l => translations[lang][l.toLowerCase()] || l),
                        datasets: [{
                            label: translations[lang].followers || 'Followers',
                            data: regionData[region].data,
                            backgroundColor: ['#1877F2', '#0A66C2', '#E4405F', '#FF0000', '#000000'].map(c => c + '99'),
                            borderColor: ['#1877F2', '#0A66C2', '#E4405F', '#FF0000', '#000000'],
                            borderWidth: 1,
                            borderRadius: 4,
                        }]
                    },
                    options: {
                        indexAxis: 'y', responsive: true, maintainAspectRatio: false,
                        plugins: { legend: { display: false } },
                        scales: { 
                            y: { grid: { display: false }, ticks: { color: textColor } },
                            x: { grid: { color: gridColor }, ticks: { color: textColor }, type: 'logarithmic' }
                        }
                    }
                });
            }

            function updateChannelPriorities(country) {
                const lang = localStorage.getItem('preferred_language') || 'en';
                const container = document.getElementById('channel-priorities');
                const insightsContainer = document.getElementById('channel-insights');
                const priorityData = {
                    sd: [{ name: 'Facebook', priority: 'High', icon: 'facebook' }, { name: 'WhatsApp', priority: 'High', icon: 'message-circle' }, { name: 'YouTube', priority: 'Medium', icon: 'youtube' }, { name: 'Instagram', priority: 'Medium', icon: 'instagram' }, { name: 'X (Twitter)', priority: 'Low', icon: 'twitter' }, { name: 'LinkedIn', priority: 'Low', icon: 'linkedin' }, { name: 'TikTok', priority: 'Potential', icon: 'video' }],
                    om: [{ name: 'Instagram', priority: 'High', icon: 'instagram' }, { name: 'WhatsApp', priority: 'High', icon: 'message-circle' }, { name: 'LinkedIn', priority: 'High', icon: 'linkedin' }, { name: 'Facebook', priority: 'Medium', icon: 'facebook' }, { name: 'YouTube', priority: 'Medium', icon: 'youtube' }, { name: 'X (Twitter)', priority: 'Low', icon: 'twitter' }, { name: 'TikTok', priority: 'Potential', icon: 'video' }],
                    ug: [{ name: 'Facebook', priority: 'High', icon: 'facebook' }, { name: 'WhatsApp', priority: 'High', icon: 'message-circle' }, { name: 'YouTube', priority: 'Medium', icon: 'youtube' }, { name: 'TikTok', priority: 'Low', icon: 'video' }, { name: 'Instagram', priority: 'Low', icon: 'instagram' }, { name: 'X (Twitter)', priority: 'Potential', icon: 'twitter' }]
                };

                container.innerHTML = priorityData[country].map((p, index) => {
                    const translatedPriority = translations[lang][p.priority.toLowerCase()] || p.priority;
                    return `
                    <div class="flex items-center justify-between p-3 card rounded-lg">
                        <div class="flex items-center"><i data-feather="${p.icon}" class="w-5 h-5 ltr:mr-3 rtl:ml-3 text-accent-green-dark"></i><span class="font-semibold">${translations[lang][p.name.toLowerCase()] || p.name}</span></div>
                        <div class="priority-dropdown">
                            <button class="flex items-center">
                                <span class="text-sm ltr:mr-2 rtl:ml-2 font-semibold text-slate-500 dark:text-slate-400">${translatedPriority}</span>
                                <div class="w-3 h-3 rounded-full ${priorityColors[p.priority]}"></div>
                            </button>
                        </div>
                    </div>`
                }).join('');
                insightsContainer.innerHTML = `<p class="text-sm text-slate-600 dark:text-slate-300">${translations[lang][channelInsightsData[country]]}</p>`;
                feather.replace();
            }
            
            function setActiveCountry(country) {
                document.querySelectorAll('#strategy .tab-button').forEach(btn => btn.classList.toggle('active', btn.dataset.country === country));
                document.querySelectorAll('#world-map svg path.highlight-country').forEach(path => {
                    path.classList.toggle('active', path.dataset.country === country);
                });
                updateChannelPriorities(country);
            }

            function formatCurrency(value) { return new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD', minimumFractionDigits: 0 }).format(value); }

            function updateBudget(total) {
                const lang = localStorage.getItem('preferred_language') || 'en';
                const ads = total * 0.55;
                const content = total * 0.35;
                const tools = total * 0.10;
                const isDark = html.classList.contains('dark');
                const textColor = isDark ? '#9CA3AF' : '#6B7280';

                document.getElementById('budget-breakdown').innerHTML = `
                    <div class="flex justify-between items-center font-bold"><span>${translations[lang].budget_total}</span> <span class="text-2xl gradient-text">${formatCurrency(total)}</span></div>
                    <div class="mt-4 pt-4 border-t border-gray-200 dark:border-gray-700">
                        <div class="flex justify-between items-center"><span class="flex items-center"><i data-feather="dollar-sign" class="w-4 h-4 ltr:mr-2 rtl:ml-2"></i>${translations[lang].budget_ads}</span> <span class="font-semibold">${formatCurrency(ads)}</span></div>
                        <div class="flex justify-between items-center"><span class="flex items-center"><i data-feather="edit-3" class="w-4 h-4 ltr:mr-2 rtl:ml-2"></i>${translations[lang].budget_content}</span> <span class="font-semibold">${formatCurrency(content)}</span></div>
                        <div class="flex justify-between items-center"><span class="flex items-center"><i data-feather="settings" class="w-4 h-4 ltr:mr-2 rtl:ml-2"></i>${translations[lang].budget_tools}</span> <span class="font-semibold">${formatCurrency(tools)}</span></div>
                    </div>`;
                feather.replace();
                
                if (window.budgetChart) window.budgetChart.destroy();
                window.budgetChart = new Chart(budgetChartCanvas.getContext('2d'), {
                    type: 'doughnut',
                    data: {
                        labels: [translations[lang].budget_ads, translations[lang].budget_content, translations[lang].budget_tools],
                        datasets: [{ data: [ads, content, tools], backgroundColor: ['var(--accent-green-dark)', 'var(--accent-green-mid)', 'var(--accent-yellow)'], borderColor: 'var(--card-bg-color)', borderWidth: 4, }]
                    },
                    options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: true, position: 'bottom', labels: { color: textColor, font: { family: lang === 'ar' ? 'Tajawal' : 'Inter' } } } }, cutout: '60%' }
                });
            }

            function injectMapAndSetupListeners() {
                const mapContainer = document.getElementById('world-map');
                const tooltip = document.getElementById('map-tooltip');
                const mapSVG = `<svg viewBox="0 0 1000 590" xmlns="http://www.w3.org/2000/svg"><g class="country" fill="#D1D5DB" stroke-width=".3" stroke="#fff"><path d="M495,125L495,125L495,125L495,125z M448,220L448,220L448,220L448,220z"/></g><path id="om" class="highlight-country" d="M722.5,357.5 l-2.6,0.3 l-2.8-1.5 l-1.3-2.6 l3.1-4.7 l4.9-3.9 l3.4,1.9 l1.4,4.2 l-1.8,4.7 l-3.3,3.3z" data-name="Oman" data-country="om"></path><path id="ug" class="highlight-country" d="M609.9,251.3 C 607.4,250.2 604.9,250.7 602.8,252.5 C 600.7,254.3 599.4,257 599.5,259.6 C 599.6,262.2 601.1,264.6 603.5,265.8 C 605.9,267 608.6,266.8 610.9,265.3 C 613.2,263.8 614.7,261.2 614.8,258.6 C 614.9,256 613.5,253.5 611.4,252.2 C 610.9,251.9 610.4,251.6 609.9,251.3" data-name="Uganda" data-country="ug"></path><path id="sd" class="highlight-country" d="M598.7,203.4 C 594.4,201.8 589.6,201.9 585.3,203.7 C 581,205.5 577.5,208.9 575.6,213.2 C 573.7,217.5 573.5,222.4 575.1,226.9 C 576.7,231.4 580,235.1 584.5,237.2 C 589,239.3 594.1,239.6 598.7,238 C 603.3,236.4 607,233.1 609.2,228.8 C 611.4,224.5 611.9,219.6 610.7,215.1 C 609.5,210.6 606.6,206.8 602.6,204.6 C 601.3,203.9 599.9,203.5 598.7,203.4" data-name="Sudan" data-country="sd"></path></svg>`;
                mapContainer.innerHTML = mapSVG;

                const countryCodes = { sd: 'Sudan', om: 'Oman', ug: 'Uganda' };
                Object.keys(countryCodes).forEach(code => {
                    const path = mapContainer.querySelector(`#${code}`);
                    if (path) {
                        path.addEventListener('click', () => setActiveCountry(path.dataset.country));
                        path.addEventListener('mousemove', (e) => {
                            tooltip.style.display = 'block';
                            const containerRect = mapContainer.getBoundingClientRect();
                            tooltip.style.left = `${e.clientX - containerRect.left}px`;
                            tooltip.style.top = `${e.clientY - containerRect.top}px`;
                            tooltip.textContent = path.dataset.name;
                        });
                        path.addEventListener('mouseleave', () => { tooltip.style.display = 'none'; });
                    }
                });
            }

            function showContentModal(type) {
                const lang = localStorage.getItem('preferred_language') || 'en';
                const overlay = document.getElementById('content-modal-overlay');
                const titleEl = document.getElementById('modal-title');
                const contentEl = document.getElementById('modal-content');
                const data = contentModalData[type];

                if (data) {
                    titleEl.innerHTML = translations[lang][data.title_key];
                    contentEl.innerHTML = translations[lang][data.content_key];
                    overlay.style.display = 'flex';
                }
            }

            function hideContentModal() { document.getElementById('content-modal-overlay').style.display = 'none'; }

            // --- INITIALIZATION & EVENT LISTENERS ---
            
            injectMapAndSetupListeners();
            feather.replace(); // Initial call
            
            const initialTheme = localStorage.getItem('theme') || 'light';
            const initialLang = localStorage.getItem('preferred_language') || 'en';
            setLanguage(initialLang); // This will set lang and call applyTheme
            
            document.getElementById('dark-mode-toggle').addEventListener('click', () => {
                const newTheme = html.classList.contains('dark') ? 'light' : 'dark';
                localStorage.setItem('theme', newTheme);
                applyTheme(newTheme);
            });
            
            document.querySelectorAll('.lang-toggle').forEach(btn => {
                btn.addEventListener('click', (e) => setLanguage(e.target.dataset.lang));
            });

            document.getElementById('menu-btn').addEventListener('click', () => {
                document.getElementById('mobile-menu').classList.toggle('hidden');
                feather.replace();
            });
            
            document.querySelectorAll('#assessment .kpi-selector-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    document.querySelectorAll('#assessment .kpi-selector-btn').forEach(b => b.classList.remove('active'));
                    e.target.classList.add('active');
                    renderAssessmentChart(e.target.dataset.region);
                });
            });
            
            document.querySelectorAll('#planning .post-pill').forEach(pill => {
                pill.addEventListener('click', (e) => showContentModal(e.target.dataset.type));
            });
            
            document.getElementById('content-modal-overlay').addEventListener('click', (e) => { if(e.target.id === 'content-modal-overlay') hideContentModal(); });
            document.getElementById('modal-close-btn').addEventListener('click', hideContentModal);

            document.querySelectorAll('#strategy .tab-button').forEach(btn => btn.addEventListener('click', (e) => setActiveCountry(e.target.dataset.country)));

            document.getElementById('budget-slider').addEventListener('input', (e) => updateBudget(e.target.value));
            
            const notesArea = document.getElementById('notes-area');
            const sendNotesBtn = document.getElementById('send-notes-btn');

            notesArea.addEventListener('input', () => {
                sendNotesBtn.disabled = notesArea.value.trim() === '';
            });

            sendNotesBtn.addEventListener('click', () => {
                const notes = notesArea.value;
                if (notes.trim() !== '') {
                    const subject = "Notes from SeedTech Interactive Proposal";
                    const body = encodeURIComponent(notes);
                    window.location.href = `mailto:care@branddi.co.site?subject=${encodeURIComponent(subject)}&body=${body}`;
                }
            });
            
            // Set initial state after everything is set up
            renderAssessmentChart('sd');
            setActiveCountry('sd');
            updateBudget(document.getElementById('budget-slider').value);
        });
    </script>
</body>
</html>
# brandisocialmm
