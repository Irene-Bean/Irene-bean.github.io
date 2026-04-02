<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NSQ Positioning Engine</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #FDF8F5;
            color: #2D1B0D;
        }
        .cocoa-bg { background-color: #2D1B0D; }
        .terracotta-bg { background-color: #E9A68A; }
        .terracotta-text { color: #E9A68A; }
        .terracotta-border { border-color: #E9A68A; }
        /* Strategy Card Interactions */
        .strategy-card {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
            position: relative;
            background-color: white;
            border-width: 2px;
            border-color: rgba(233, 166, 138, 0.2);
        }
        .strategy-card:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: 0 25px 30px -10px rgba(45, 27, 13, 0.15), 0 15px 15px -10px rgba(45, 27, 13, 0.05);
        }
        /* Active State: Thicker peach border and soft glow */
        .strategy-card.active {
            border-width: 4px;
            border-color: #E9A68A;
            box-shadow: 0 0 25px rgba(233, 166, 138, 0.5);
            z-index: 10;
        }
        /* Select Label Animation */
        .select-label {
            opacity: 0;
            transform: translateY(10px);
            transition: all 0.3s ease;
        }
        .strategy-card:hover .select-label {
            opacity: 1;
            transform: translateY(0);
        }
        canvas {
            max-width: 100%;
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #FDF8F5;
        }
        ::-webkit-scrollbar-thumb {
            background: #E9A68A;
            border-radius: 10px;
        }
    </style>
</head>
<body class="pt-12 pb-20 px-4">
    <main class="max-w-6xl mx-auto space-y-10">
        <!-- HEADER SECTION -->
        <header class="bg-[#2D1B0D] rounded-[2.5rem] p-10 md:p-14 text-center relative overflow-hidden shadow-2xl">
            <div class="absolute top-6 left-6 opacity-20">
                <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="#E9A68A"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>
            </div>
            <h1 class="text-[#E9A68A] text-4xl md:text-5xl font-extrabold mb-4 tracking-tight">Hi Madelena and Catarina!</h1>
            <p class="text-white/80 text-lg max-w-2xl mx-auto font-medium leading-relaxed">
                Here is how my social media strategy can help you grow your coworking community at Estoril Office Center.
            </p>
            <div class="absolute bottom-0 right-0 w-64 h-64 bg-[#E9A68A]/10 rounded-full blur-[80px] -mr-32 -mb-32"></div>
        </header>
        <!-- STRATEGY SELECTOR SECTION -->
        <section class="space-y-8">
            <h2 class="text-center font-bold text-[#2D1B0D] text-2xl tracking-tight">Which platform strategy would you like to focus on?</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- LinkedIn Tile -->
                <div id="btn-linkedin" onclick="setActiveStrategy('linkedin')" class="strategy-card active p-8 rounded-[2rem] flex flex-col items-center text-center">
                    <div class="bg-[#FDF8F5] p-4 rounded-full mb-6 terracotta-text shadow-inner">
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect width="4" height="12" x="2" y="9"/><circle cx="4" cy="4" r="2"/></svg>
                    </div>
                    <h3 class="font-bold text-xl mb-3">LinkedIn Focus</h3>
                    <p class="text-sm opacity-60 font-medium leading-relaxed mb-6">High value corporate networking for private office suites.</p>
                    <span class="select-label text-[10px] font-black uppercase tracking-[0.2em] terracotta-text mt-auto">Select Strategy</span>
                </div>
                <!-- Instagram Tile -->
                <div id="btn-instagram" onclick="setActiveStrategy('instagram')" class="strategy-card p-8 rounded-[2rem] flex flex-col items-center text-center">
                    <div class="bg-[#FDF8F5] p-4 rounded-full mb-6 terracotta-text shadow-inner">
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
                    </div>
                    <h3 class="font-bold text-xl mb-3">Instagram Focus</h3>
                    <p class="text-sm opacity-60 font-medium leading-relaxed mb-6">Visual storytelling focused on lifestyle and community desks.</p>
                    <span class="select-label text-[10px] font-black uppercase tracking-[0.2em] terracotta-text mt-auto">Select Strategy</span>
                </div>
                <!-- Blended Tile -->
                <div id="btn-blended" onclick="setActiveStrategy('blended')" class="strategy-card p-8 rounded-[2rem] flex flex-col items-center text-center">
                    <div class="bg-[#FDF8F5] p-4 rounded-full mb-6 terracotta-text shadow-inner">
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10Z"/><path d="m9 12 2 2 4-4"/></svg>
                    </div>
                    <h3 class="font-bold text-xl mb-3">Blended Scale</h3>
                    <p class="text-sm opacity-60 font-medium leading-relaxed mb-6">Omnichannel market dominance for sustainable full occupancy.</p>
                    <span class="select-label text-[10px] font-black uppercase tracking-[0.2em] terracotta-text mt-auto">Select Strategy</span>
                </div>
            </div>
        </section>
        <!-- ANALYTICS SECTION -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
            <!-- Radar Chart (Intent Mapping) -->
            <div class="lg:col-span-5">
                <div class="bg-white p-10 rounded-[2.5rem] border border-[#E9A68A]/10 shadow-sm h-full flex flex-col">
                    <div class="mb-8">
                        <h3 class="text-xl font-bold text-[#2D1B0D]">Intent Mapping</h3>
                        <p id="radar-description" class="text-sm text-[#2D1B0D]/50 font-medium mt-1">LinkedIn dominates logic-driven authority and B2B intent.</p>
                    </div>
                    <div class="flex-grow flex items-center justify-center min-h-[350px]">
                        <canvas id="intentRadar"></canvas>
                    </div>
                    <div class="mt-8 flex justify-center gap-6">
                        <div class="flex items-center gap-2">
                            <div class="w-3 h-3 rounded-full bg-[#2D1B0D]"></div>
                            <span class="text-[10px] font-bold uppercase tracking-widest opacity-60">LinkedIn</span>
                        </div>
                        <div class="flex items-center gap-2">
                            <div class="w-3 h-3 rounded-full bg-[#E9A68A]"></div>
                            <span class="text-[10px] font-bold uppercase tracking-widest opacity-60">Instagram</span>
                        </div>
                    </div>
                </div>
            </div>
            <!-- Line Chart (Projection) -->
            <div class="lg:col-span-7">
                <div class="bg-white p-10 rounded-[2.5rem] border border-[#E9A68A]/10 shadow-sm h-full flex flex-col">
                    <div class="mb-8">
                        <h3 class="text-xl font-bold text-[#2D1B0D]">12-Month Occupancy Projection</h3>
                        <p class="text-sm text-[#2D1B0D]/50 font-medium mt-1">Proactive targeting ensures high capacity by month 6.</p>
                    </div>
                    <div class="flex-grow min-h-[350px]">
                        <canvas id="occupancyLine"></canvas>
                    </div>
                    <div class="mt-8 grid grid-cols-2 gap-4">
                        <div class="p-4 rounded-2xl bg-[#FDF8F5] border border-[#E9A68A]/10">
                            <p class="text-[10px] font-black terracotta-text uppercase tracking-widest mb-1">Social Lead Strategy</p>
                            <p class="text-xs opacity-60 leading-tight">Optimized growth based on active strategy selection.</p>
                        </div>
                        <div class="p-4 rounded-2xl bg-[#FDF8F5] border border-[#2D1B0D]/5">
                            <p class="text-[10px] font-black text-[#2D1B0D] uppercase tracking-widest mb-1">Baseline Growth</p>
                            <p class="text-xs opacity-60 leading-tight">Generic referral based growth peaks at ~60%.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- BENCHMARK GRID -->
        <section class="bg-white p-12 rounded-[2.5rem] border border-[#E9A68A]/10 shadow-sm">
            <h3 class="text-xl font-bold mb-10 flex items-center gap-3 text-[#2D1B0D]">
                <div class="p-2 bg-[#FDF8F5] rounded-lg">
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="20" x2="12" y2="10"/><line x1="18" y1="20" x2="18" y2="4"/><line x1="6" y1="20" x2="6" y2="16"/></svg>
                </div>
                Channel Efficiency Benchmarks
            </h3>
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-8">
                <!-- Avg Conversion Rate -->
                <div class="group">
                    <p class="text-[10px] font-black terracotta-text uppercase mb-2 tracking-widest">Avg Conversion Rate</p>
                    <p class="text-4xl font-extrabold tracking-tighter">3.0%</p>
                    <div class="h-1 w-12 bg-[#E9A68A]/20 mt-4 group-hover:w-full transition-all duration-500"></div>
                    <p class="text-[10px] opacity-40 font-bold uppercase mt-4">Visitor to Lead Stage</p>
                </div>
                <!-- Revenue per SQ Meter -->
                <div class="group">
                    <p class="text-[10px] font-black terracotta-text uppercase mb-2 tracking-widest">Avg Revenue / m² (Lisbon)</p>
                    <p class="text-4xl font-extrabold tracking-tighter">€35.00</p>
                    <div class="h-1 w-12 bg-[#E9A68A]/20 mt-4 group-hover:w-full transition-all duration-500"></div>
                    <p class="text-[10px] opacity-40 font-bold uppercase mt-4">Regional Industry Avg</p>
                </div>
                <!-- Potential ROI Factor -->
                <div class="group">
                    <p class="text-[10px] font-black terracotta-text uppercase mb-2 tracking-widest">Potential ROI Factor</p>
                    <p class="text-4xl font-extrabold tracking-tighter">4.2x</p>
                    <div class="h-1 w-12 bg-[#E9A68A]/20 mt-4 group-hover:w-full transition-all duration-500"></div>
                    <p class="text-[10px] opacity-40 font-bold uppercase mt-4">Target LTV:CAC Multiplier</p>
                </div>
            </div>
        </section>
        <!-- FOOTER SECTION -->
        <footer class="w-full mt-12">
            <div class="p-14 cocoa-bg rounded-[3rem] text-white text-center shadow-2xl relative overflow-hidden border border-[#E9A68A]/5">
                <div class="relative z-10 flex flex-col items-center gap-6">
                    <div class="flex items-center gap-4">
                        <div class="h-[1px] w-12 bg-[#E9A68A]/30"></div>
                        <p class="text-[10px] font-black terracotta-text uppercase tracking-[0.5em]">Social Media Strategy Presentation</p>
                        <div class="h-[1px] w-12 bg-[#E9A68A]/30"></div>
                    </div>
                    <p class="text-2xl md:text-3xl font-medium leading-tight max-w-3xl mx-auto tracking-tight">
                        Designed by <span class="terracotta-text font-bold">Irene Mutwiri, M.Ed.</span> for <span class="terracotta-text font-bold">Estoril Office Center</span>.
                    </p>
                    <p class="text-white/40 text-[10px] uppercase tracking-widest font-bold">Last Updated April 02, 2026</p>
                </div>
                <div class="absolute top-0 left-0 w-80 h-80 bg-[#E9A68A]/5 rounded-full blur-[100px] -ml-40 -mt-40"></div>
                <div class="absolute bottom-0 right-0 w-80 h-80 bg-[#E9A68A]/5 rounded-full blur-[100px] -mr-40 -mb-40"></div>
            </div>
        </footer>
    </main>
    <script>
        let radarChart, lineChart;
        // Data Repository for specific strategies
        const chartData = {
            linkedin: {
                radar: [95, 30, 90, 40, 95, 80],
                desc: 'LinkedIn dominates logic-driven authority and B2B intent.',
                projection: [20, 28, 45, 70, 88, 94, 96, 97, 98, 98, 98, 99]
            },
            instagram: {
                radar: [35, 95, 60, 98, 30, 70],
                desc: 'Instagram builds brand aesthetic and emotional relatability.',
                projection: [20, 35, 55, 75, 85, 90, 92, 93, 93, 94, 94, 95]
            },
            blended: {
                radar: [85, 85, 95, 85, 90, 95],
                desc: 'Blended scale balances professional logic with social "vibe".',
                projection: [20, 40, 65, 85, 92, 95, 97, 98, 98, 99, 99, 100]
            }
        };
        /**
         * Sets the active visual state for the tiles and triggers chart updates
         */
        function setActiveStrategy(id) {
            // Update UI Card States
            document.querySelectorAll('.strategy-card').forEach(card => card.classList.remove('active'));
            document.getElementById(`btn-${id}`).classList.add('active');
            // Trigger Chart Updates with animation
            updateCharts(id);
            // Update Narrative text
            document.getElementById('radar-description').innerText = chartData[id].desc;
        }
        /**
         * Redraws chart data based on selected strategy
         */
        function updateCharts(id) {
            const data = chartData[id];
            // Update Radar Chart logic
            radarChart.data.datasets[0].data = data.radar;
            // Manage Visibility for Radar Comparison
            if(id === 'linkedin') {
                radarChart.data.datasets[0].hidden = false;
                radarChart.data.datasets[1].hidden = true;
            } else if(id === 'instagram') {
                radarChart.data.datasets[0].hidden = true;
                radarChart.data.datasets[1].hidden = false;
            } else {
                radarChart.data.datasets[0].hidden = false;
                radarChart.data.datasets[1].hidden = false;
                // For blended, we set the second dataset to a default Instagram state for contrast
                radarChart.data.datasets[1].data = chartData.instagram.radar;
            }
            radarChart.update();
            // Update Occupancy Projection
            lineChart.data.datasets[0].data = data.projection;
            lineChart.update();
        }
        /**
         * Initial Chart Setup
         */
        function initCharts() {
            // Global Chart Defaults
            Chart.defaults.font.family = "'Plus Jakarta Sans', sans-serif";
            Chart.defaults.color = "#2D1B0D";
            // Initialize Radar Chart
            const radarCtx = document.getElementById('intentRadar').getContext('2d');
            radarChart = new Chart(radarCtx, {
                type: 'radar',
                data: {
                    labels: ['B2B Authority', 'Emotional Connection', 'Lead Quality', 'Visual Appeal', 'Logic/Data', 'Direct Response'],
                    datasets: [{
                        label: 'LinkedIn Intent',
                        data: chartData.linkedin.radar,
                        fill: true,
                        backgroundColor: 'rgba(45, 27, 13, 0.1)',
                        borderColor: '#2D1B0D',
                        pointBackgroundColor: '#2D1B0D',
                        borderWidth: 2
                    }, {
                        label: 'Instagram Brand',
                        data: chartData.instagram.radar,
                        fill: true,
                        backgroundColor: 'rgba(233, 166, 138, 0.2)',
                        borderColor: '#E9A68A',
                        pointBackgroundColor: '#E9A68A',
                        borderWidth: 2,
                        hidden: true
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { 
                        r: { 
                            min: 0, max: 100, 
                            ticks: { display: false }, 
                            grid: { color: 'rgba(0,0,0,0.05)' },
                            pointLabels: { font: { size: 10, weight: 'bold' } }
                        } 
                    }
                }
            });
            // Initialize Occupancy Line Chart
            const lineCtx = document.getElementById('occupancyLine').getContext('2d');
            lineChart = new Chart(lineCtx, {
                type: 'line',
                data: {
                    labels: ['M1', 'M2', 'M3', 'M4', 'M5', 'M6', 'M7', 'M8', 'M9', 'M10', 'M11', 'M12'],
                    datasets: [{
                        label: 'Active Strategy',
                        data: chartData.linkedin.projection,
                        borderColor: '#E9A68A',
                        backgroundColor: '#E9A68A',
                        tension: 0.4,
                        borderWidth: 4,
                        pointRadius: 4,
                        pointBackgroundColor: '#FFF',
                        pointBorderWidth: 2
                    }, {
                        label: 'Baseline Growth',
                        data: [20, 22, 28, 35, 42, 48, 52, 55, 58, 60, 61, 62],
                        borderColor: '#2D1B0D',
                        borderDash: [8, 4],
                        tension: 0.4,
                        pointRadius: 0,
                        borderWidth: 2,
                        opacity: 0.2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { 
                        y: { 
                            beginAtZero: true, 
                            max: 100, 
                            grid: { color: 'rgba(0,0,0,0.03)' }, 
                            ticks: { callback: v => v + '%' } 
                        },
                        x: { grid: { display: false } }
                    }
                }
            });
        }
        // Wait for page load
        window.onload = initCharts;
    </script>
</body>
</html>
