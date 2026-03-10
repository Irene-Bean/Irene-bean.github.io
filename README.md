<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NSQ Positioning Engine</title>
    <script src="https://cdn.tailwindcss.com"></script>
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
        .fade-in {
            animation: fadeIn 0.6s ease-out forwards;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        input[type="date"]::-webkit-calendar-picker-indicator {
            filter: invert(1);
            cursor: pointer;
        }
        .pulse-shadow {
            box-shadow: 0 0 12px #E9A68A;
        }
    </style>
</head>
<body class="pt-8 pb-20">
    <main class="max-w-6xl mx-auto p-6 space-y-8">
        <!-- HERO SECTION: ADAPTIVE DECISION TREE -->
        <section class="bg-white rounded-[2rem] shadow-sm border border-[#E9A68A]/10 overflow-hidden">
            <div class="cocoa-bg p-10 text-center relative">
                <div class="absolute top-6 left-6 opacity-10">
                    <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9.5 2A2.5 2.5 0 0 1 12 4.5v15a2.5 2.5 0 0 1-4.96.44 2.5 2.5 0 0 1-2.54-2.44 2.5 2.5 0 0 1-2.5-2.5V4.5A2.5 2.5 0 0 1 4.5 2z"/><path d="M14.5 2A2.5 2.5 0 0 0 12 4.5v15a2.5 2.5 0 0 0 4.96.44 2.5 2.5 0 0 0 2.54-2.44 2.5 2.5 0 0 0 2.5-2.5V4.5A2.5 2.5 0 0 0 19.5 2z"/></svg>
                </div>
                <h2 class="text-white text-3xl font-bold mb-3 tracking-tight">Adaptive Content Selector</h2>
                <p class="terracotta-text text-sm max-w-lg mx-auto font-medium opacity-90">
                    Diagnose audience physiological state to determine the most effective strategy.
                </p>
            </div>
            <div class="p-10" id="assessment-container">
                <!-- Assessment View (Default) -->
                <div id="view-selector" class="fade-in">
                    <h3 class="text-center font-bold text-[#2D1B0D] mb-10 text-xl">
                        How would you describe your audience's current physiological arousal level?
                    </h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <button onclick="showResult('sympathetic')" class="p-8 text-center border-2 border-[#E9A68A]/30 rounded-3xl transition-all hover:scale-[1.02] hover:border-[#E9A68A] flex flex-col items-center group bg-[#FDF8F5]">
                            <div class="bg-white p-3 rounded-full mb-4 shadow-sm group-hover:shadow-md transition-all">
                                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/></svg>
                            </div>
                            <span class="font-bold text-lg mb-2">High Arousal</span>
                            <span class="text-xs opacity-70 leading-relaxed font-medium">Frantic, hyper-focused, anxious, or overwhelmed</span>
                            <div class="mt-6 flex items-center gap-1 text-[10px] font-black uppercase tracking-[0.2em] opacity-0 group-hover:opacity-100 transition-opacity terracotta-text">
                                Select <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
                            </div>
                        </button>
                        <button onclick="showResult('dorsal')" class="p-8 text-center border-2 border-[#E9A68A]/30 rounded-3xl transition-all hover:scale-[1.02] hover:border-[#E9A68A] flex flex-col items-center group bg-[#FDF8F5]">
                            <div class="bg-white p-3 rounded-full mb-4 shadow-sm group-hover:shadow-md transition-all">
                                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z"/></svg>
                            </div>
                            <span class="font-bold text-lg mb-2">Low Arousal</span>
                            <span class="text-xs opacity-70 leading-relaxed font-medium">Frozen, numb, procrastinating, or dissociated</span>
                            <div class="mt-6 flex items-center gap-1 text-[10px] font-black uppercase tracking-[0.2em] opacity-0 group-hover:opacity-100 transition-opacity terracotta-text">
                                Select <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
                            </div>
                        </button>
                        <button onclick="showResult('ventral')" class="p-8 text-center border-2 border-[#E9A68A]/30 rounded-3xl transition-all hover:scale-[1.02] hover:border-[#E9A68A] flex flex-col items-center group bg-[#FDF8F5]">
                            <div class="bg-white p-3 rounded-full mb-4 shadow-sm group-hover:shadow-md transition-all">
                                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 14c1.49-1.46 3-3.21 3-5.5A5.5 5.5 0 0 0 16.5 3c-1.76 0-3 .5-4.5 2-1.5-1.5-2.74-2-4.5-2A5.5 5.5 0 0 0 2 8.5c0 2.3 1.5 4.05 3 5.5l7 7Z"/></svg>
                            </div>
                            <span class="font-bold text-lg mb-2">Social Safety</span>
                            <span class="text-xs opacity-70 leading-relaxed font-medium">Regulated, creative, connected, and curious</span>
                            <div class="mt-6 flex items-center gap-1 text-[10px] font-black uppercase tracking-[0.2em] opacity-0 group-hover:opacity-100 transition-opacity terracotta-text">
                                Select <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
                            </div>
                        </button>
                    </div>
                </div>
                <!-- Results View (Hidden by default) -->
                <div id="view-result" class="hidden fade-in">
                    <div class="flex flex-col md:flex-row items-center justify-between mb-8 pb-6 border-b border-[#E9A68A]/10 gap-4">
                        <button onclick="resetAssessment()" class="group flex items-center gap-2 text-[#2D1B0D] font-bold text-xs uppercase tracking-widest">
                            <div class="bg-[#E9A68A]/10 p-2 rounded-full group-hover:bg-[#E9A68A]/20 transition-colors">
                                <svg id="sync-icon-small" xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12a9 9 0 1 1-9-9c2.52 0 4.93 1 6.74 2.74L21 8"/><path d="M21 3v5h-5"/></svg>
                            </div>
                            Restart Assessment
                        </button>
                        <div class="flex items-center gap-3">
                            <span class="text-[10px] text-[#2D1B0D]/40 font-bold uppercase tracking-widest">Protocol</span>
                            <div id="result-badge" class="px-5 py-2 terracotta-bg text-white text-[10px] font-black rounded-full uppercase tracking-[0.2em] shadow-lg shadow-[#E9A68A]/20">
                                STRATEGY
                            </div>
                        </div>
                    </div>
                    <div class="w-full">
                        <div class="cocoa-bg rounded-[2rem] p-10 text-white shadow-2xl relative overflow-hidden">
                            <div class="relative z-10">
                                <div class="flex items-center gap-2 terracotta-text text-[10px] font-black uppercase tracking-[0.3em] mb-4">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="m12 3-1.912 5.813a2 2 0 0 1-1.275 1.275L3 12l5.813 1.912a2 2 0 0 1 1.275 1.275L12 21l1.912-5.813a2 2 0 0 1 1.275-1.275L21 12l-5.813-1.912a2 2 0 0 1-1.275-1.275L12 3Z"/></svg> 
                                    Recommended Protocol
                                </div>
                                <h4 id="result-title" class="text-4xl font-bold mb-8 tracking-tight">Strategy Title</h4>
                                <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
                                    <div class="space-y-4">
                                        <p class="terracotta-text text-[10px] font-black uppercase tracking-widest mb-4 border-l-2 terracotta-border pl-3">Strategic Tactics</p>
                                        <div id="result-tactics" class="grid grid-cols-1 gap-3">
                                            <!-- Tactics injected here -->
                                        </div>
                                    </div>
                                    <div class="flex flex-col justify-center">
                                        <div class="bg-[#E9A68A]/10 p-8 rounded-3xl border border-[#E9A68A]/20 text-center">
                                            <p class="text-[10px] terracotta-text font-bold uppercase mb-3 tracking-widest">Projected Outcome</p>
                                            <p id="result-impact" class="text-xl font-medium leading-relaxed italic text-white/90">"Impact statement"</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="absolute top-0 right-0 w-80 h-80 bg-[#E9A68A]/5 rounded-full blur-[100px] -mr-32 -mt-32"></div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <!-- MIDDLE SECTION: PULSE & ANCHORS -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
            <div class="lg:col-span-7">
                <div class="bg-white p-10 rounded-[2rem] border border-[#E9A68A]/10 shadow-sm h-full">
                    <h3 class="text-lg font-bold mb-6 flex items-center gap-2 text-[#2D1B0D]">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10Z"/><path d="m9 12 2 2 4-4"/></svg>
                        Strategic Anchors
                    </h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="p-6 bg-[#FDF8F5] rounded-3xl border border-[#E9A68A]/5">
                            <p class="text-[10px] font-black terracotta-text uppercase mb-3 tracking-widest">Rest Ethic</p>
                            <p class="text-sm text-[#2D1B0D]/70 font-medium leading-relaxed">Reframing rest as a performance prerequisite for creatives rather than a reward.</p>
                        </div>
                        <div class="p-6 bg-[#FDF8F5] rounded-3xl border border-[#E9A68A]/5">
                            <p class="text-[10px] font-black terracotta-text uppercase mb-3 tracking-widest">Temporal Opt.</p>
                            <p class="text-sm text-[#2D1B0D]/70 font-medium leading-relaxed">Aligning output with ultradian cycles (90-min blocks) and biological rhythms.</p>
                        </div>
                    </div>
                </div>
            </div>
            <aside class="lg:col-span-5">
                <div class="cocoa-bg rounded-[2rem] p-10 text-white relative overflow-hidden shadow-xl h-full flex flex-col justify-between">
                    <div class="relative z-10">
                        <div class="flex items-center justify-between mb-10">
                            <h3 class="text-[10px] font-black uppercase tracking-[0.3em] terracotta-text">System Pulse</h3>
                            <button onclick="triggerSync()" class="p-2 rounded-full bg-white/5 hover:bg-white/10 transition-colors">
                                <svg id="sync-icon" xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12a9 9 0 1 1-9-9c2.52 0 4.93 1 6.74 2.74L21 8"/><path d="M21 3v5h-5"/></svg>
                            </button>
                        </div>
                        <div class="space-y-10">
                            <div>
                                <p class="text-6xl font-bold mb-2 tracking-tighter">94.2%</p>
                                <p class="text-[11px] terracotta-text font-bold uppercase tracking-widest opacity-80">Somatic Safety Index</p>
                            </div>
                            <div class="grid grid-cols-2 gap-4">
                                <div class="p-5 bg-white/5 rounded-3xl border border-white/5">
                                    <div class="flex items-center gap-2 mb-3">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="4"/><path d="M12 2v2"/><path d="M12 20v2"/><path d="m4.93 4.93 1.41 1.41"/><path d="m17.66 17.66 1.41 1.41"/><path d="M2 12h2"/><path d="M20 12h2"/><path d="m6.34 17.66-1.41 1.41"/><path d="m19.07 4.93-1.41 1.41"/></svg>
                                        <span class="text-[10px] font-black text-white/40 uppercase">Circadian</span>
                                    </div>
                                    <p class="text-xl font-bold text-white">+22%</p>
                                </div>
                                <div class="p-5 bg-white/5 rounded-3xl border border-white/5">
                                    <div class="flex items-center gap-2 mb-3">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#E9A68A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 8h1a4 4 0 1 1 0 8h-1"/><path d="M3 8h14v9a4 4 0 0 1-4 4H7a4 4 0 0 1-4-4Z"/><line x1="6" y1="2" x2="6" y2="4"/><line x1="10" y1="2" x2="10" y2="4"/><line x1="14" y1="2" x2="14" y2="4"/></svg>
                                        <span class="text-[10px] font-black text-white/40 uppercase">Recovery</span>
                                    </div>
                                    <p class="text-xl font-bold text-white">68%</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="relative z-10 pt-8 mt-8 border-t border-white/10 flex justify-between items-end">
                        <div class="flex flex-col">
                            <p class="text-[10px] terracotta-text font-bold uppercase mb-1 tracking-widest">Status</p>
                            <p class="text-xs font-bold text-white uppercase tracking-tighter italic">Signal Optimal</p>
                        </div>
                        <div class="w-2.5 h-2.5 rounded-full terracotta-bg animate-pulse pulse-shadow"></div>
                    </div>
                </div>
            </aside>
        </div>
        <!-- FOOTER SECTION: ATTRIBUTION & DATE SELECTOR -->
        <footer class="w-full mt-12">
            <div class="p-12 cocoa-bg rounded-[2.5rem] text-white text-center shadow-2xl relative overflow-hidden border border-[#E9A68A]/5">
                <div class="relative z-10 flex flex-col items-center gap-4">
                    <div class="flex items-center gap-3 mb-2">
                        <div class="h-[1px] w-8 bg-[#E9A68A]/40"></div>
                        <p class="text-[10px] font-black terracotta-text uppercase tracking-[0.4em]">Designer Credit</p>
                        <div class="h-[1px] w-8 bg-[#E9A68A]/40"></div>
                    </div>
                    <p class="text-xl md:text-2xl font-medium leading-relaxed max-w-2xl mx-auto tracking-tight">
                        "Designed by <span class="terracotta-text font-bold">Irene Mutwiri, M.Ed.</span> for <span class="terracotta-text font-bold">@WellbyCami</span>."
                    </p>
                </div>
                <div class="relative z-10 flex flex-col items-center gap-4 pt-10 mt-10 border-t border-white/5 w-full max-w-sm mx-auto">
                    <div class="flex items-center gap-2 terracotta-text">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="18" height="18" x="3" y="4" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                        <label for="last-updated" class="text-[10px] font-black uppercase tracking-[0.2em]">Last updated on</label>
                    </div>
                    <input 
                        id="last-updated"
                        type="date" 
                        value="2024-05-20"
                        class="bg-[#3D2614] text-white text-sm border border-[#E9A68A]/10 rounded-2xl px-6 py-3 focus:outline-none focus:ring-2 focus:ring-[#E9A68A] cursor-pointer w-full text-center transition-all hover:bg-[#4D311A]"
                    />
                </div>
                <div class="absolute top-0 left-0 w-64 h-64 bg-[#E9A68A]/5 rounded-full blur-[80px] -ml-32 -mt-32"></div>
                <div class="absolute bottom-0 right-0 w-64 h-64 bg-[#E9A68A]/5 rounded-full blur-[80px] -mr-32 -mb-32"></div>
            </div>
        </footer>
    </main>
    <script>
        const results = {
            sympathetic: {
                title: "The 'Settle' Strategy",
                focus: "Down-Regulation & Sensory Softness",
                tactics: ["Low-contrast visuals", "Ambient audio loops", "Single-choice carousels", "Short, calming breathwork cues"],
                impact: "Reduces Decision Fatigue & Adrenaline Spikes"
            },
            dorsal: {
                title: "The 'Gentle Spark' Strategy",
                focus: "Safe Mobilization",
                tactics: ["High-contrast 'Waking' cues", "Micro-wins (15-30s videos)", "Physical movement prompts", "Bright, warm lighting visuals"],
                impact: "Combats Dissociation & Functional Freeze"
            },
            ventral: {
                title: "The 'Deep Flow' Strategy",
                focus: "Collaborative Mastery",
                tactics: ["Long-form immersive content", "Interactive community builds", "90-min co-working", "Non-linear problem solving prompts"],
                impact: "Maximizes Creative ROI & Community Bond"
            }
        };
        function showResult(key) {
            const data = results[key];
            const selector = document.getElementById('view-selector');
            const result = document.getElementById('view-result');
            // Set content
            document.getElementById('result-badge').innerText = `${key.toUpperCase()} STRATEGY`;
            document.getElementById('result-title').innerText = data.title;
            document.getElementById('result-impact').innerText = `"${data.impact}"`;
            const tacticsContainer = document.getElementById('result-tactics');
            tacticsContainer.innerHTML = '';
            data.tactics.forEach(tactic => {
                const div = document.createElement('div');
                div.className = 'flex items-center gap-4 bg-white/5 p-4 rounded-2xl border border-white/5 hover:bg-white/10 transition-colors';
                div.innerHTML = `
                    <div class="w-1.5 h-1.5 terracotta-bg rounded-full shrink-0 shadow-[0_0_8px_#E9A68A]"></div>
                    <span class="text-sm font-medium tracking-wide">${tactic}</span>
                `;
                tacticsContainer.appendChild(div);
            });
            // Transition
            selector.classList.add('hidden');
            result.classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
        function resetAssessment() {
            document.getElementById('view-selector').classList.remove('hidden');
            document.getElementById('view-result').classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
        function triggerSync() {
            const icon = document.getElementById('sync-icon');
            icon.classList.add('animate-spin');
            setTimeout(() => {
                icon.classList.remove('animate-spin');
            }, 1200);
        }
    </script>
</body>
</html>
