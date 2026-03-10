  const decisionTree = {
    id: 'root',
    question: "How would you describe your audience's current physiological arousal level?",
    options: [
      { 
        label: "High Arousal", 
        subtext: "Frantic, hyper-focused, anxious, or overwhelmed",
        next: 'sympathetic', 
        color: 'bg-[#FDF8F5] border-[#E9A68A]/30 text-[#2D1B0D] hover:border-[#E9A68A]',
        icon: <Zap className="w-5 h-5 mb-2 text-[#E9A68A]" />
      },
      { 
        label: "Low Arousal", 
        subtext: "Frozen, numb, procrastinating, or dissociated",
        next: 'dorsal', 
        color: 'bg-[#FDF8F5] border-[#E9A68A]/30 text-[#2D1B0D] hover:border-[#E9A68A]',
        icon: <Moon className="w-5 h-5 mb-2 text-[#E9A68A]" />
      },
      { 
        label: "Social Safety", 
        subtext: "Regulated, creative, connected, and curious",
        next: 'ventral', 
        color: 'bg-[#FDF8F5] border-[#E9A68A]/30 text-[#2D1B0D] hover:border-[#E9A68A]',
        icon: <HeartPulse className="w-5 h-5 mb-2 text-[#E9A68A]" />
      }
    ]
  };

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

  return (
    <div className="min-h-screen bg-[#FDF8F5] text-[#2D1B0D] font-sans pt-8 pb-20">
      <main className="max-w-6xl mx-auto p-6 space-y-8">
        {/* HERO SECTION: ADAPTIVE DECISION TREE */}
        <section className="bg-white rounded-[2rem] shadow-sm border border-[#E9A68A]/10 overflow-hidden">
          <div className="bg-[#2D1B0D] p-10 text-center relative">
             <div className="absolute top-6 left-6 opacity-10"><Brain className="text-[#E9A68A] w-12 h-12" /></div>
             <h2 className="text-white text-3xl font-bold mb-3 tracking-tight">Adaptive Content Selector</h2>
             <p className="text-[#E9A68A] text-sm max-w-lg mx-auto font-medium opacity-90">
               Diagnose audience physiological state to determine the most effective strategy.
             </p>
          </div>
          <div className="p-10">
            {!selectedNode ? (
              <div className="animate-in fade-in slide-in-from-bottom-4 duration-700">
                <h3 className="text-center font-bold text-[#2D1B0D] mb-10 text-xl">
                  {decisionTree.question}
                </h3>
                <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                  {decisionTree.options.map((opt) => (
                    <button
                      key={opt.next}
                      onClick={() => setSelectedNode(opt.next)}
                      className={`p-8 text-center border-2 rounded-3xl transition-all hover:scale-[1.02] flex flex-col items-center ${opt.color} group`}
                    >
                      <div className="bg-white p-3 rounded-full mb-4 shadow-sm group-hover:shadow-md transition-all">
                        {opt.icon}
                      </div>
                      <span className="font-bold text-lg mb-2">{opt.label}</span>
                      <span className="text-xs opacity-70 leading-relaxed font-medium">{opt.subtext}</span>
                      <div className="mt-6 flex items-center gap-1 text-[10px] font-black uppercase tracking-[0.2em] opacity-0 group-hover:opacity-100 transition-opacity text-[#E9A68A]">
                        Select <ArrowRight className="w-3 h-3" />
                      </div>
                    </button>
                  ))}
                </div>
              </div>
            ) : (
              <div className="animate-in zoom-in-95 duration-500">
                <div className="flex flex-col md:flex-row items-center justify-between mb-8 pb-6 border-b border-[#E9A68A]/10 gap-4">
                  <button 
                    onClick={() => setSelectedNode(null)} 
                    className="group flex items-center gap-2 text-[#2D1B0D] font-bold text-xs uppercase tracking-widest"
                  >
                    <div className="bg-[#E9A68A]/10 p-2 rounded-full group-hover:bg-[#E9A68A]/20 transition-colors">
                      <RefreshCw className="w-3 h-3 text-[#E9A68A]" />
                    </div>
                    Restart Assessment
                  </button>
                  <div className="flex items-center gap-3">
                     <span className="text-[10px] text-[#2D1B0D]/40 font-bold uppercase tracking-widest">Protocol</span>
                     <div className="px-5 py-2 bg-[#E9A68A] text-white text-[10px] font-black rounded-full uppercase tracking-[0.2em] shadow-lg shadow-[#E9A68A]/20">
                       {selectedNode} Strategy
                     </div>
                  </div>
                </div>
                <div className="w-full">
                  <div className="bg-[#2D1B0D] rounded-[2rem] p-10 text-white shadow-2xl relative overflow-hidden">
                     <div className="relative z-10">
                      <div className="flex items-center gap-2 text-[#E9A68A] text-[10px] font-black uppercase tracking-[0.3em] mb-4">
                        <Sparkles className="w-4 h-4" /> Recommended Protocol
                      </div>
                      <h4 className="text-4xl font-bold mb-8 tracking-tight">{results[selectedNode].title}</h4>
                      <div className="grid grid-cols-1 lg:grid-cols-2 gap-10">
                        <div className="space-y-4">
                          <p className="text-[#E9A68A] text-[10px] font-black uppercase tracking-widest mb-4 border-l-2 border-[#E9A68A] pl-3">Strategic Tactics</p>
                          <div className="grid grid-cols-1 gap-3">
                            {results[selectedNode].tactics.map((t, i) => (
                              <div key={i} className="flex items-center gap-4 bg-white/5 p-4 rounded-2xl border border-white/5 hover:bg-white/10 transition-colors">
                                <div className="w-1.5 h-1.5 bg-[#E9A68A] rounded-full shrink-0 shadow-[0_0_8px_#E9A68A]" />
                                <span className="text-sm font-medium tracking-wide">{t}</span>
                              </div>
                            ))}
                          </div>
                        </div>
                        <div className="flex flex-col justify-center">
                          <div className="bg-[#E9A68A]/10 p-8 rounded-3xl border border-[#E9A68A]/20 text-center">
                             <p className="text-[10px] text-[#E9A68A] font-bold uppercase mb-3 tracking-widest">Projected Outcome</p>
                             <p className="text-xl font-medium leading-relaxed italic text-white/90">"{results[selectedNode].impact}"</p>
                          </div>
                        </div>
                      </div>
                     </div>
                     <div className="absolute top-0 right-0 w-80 h-80 bg-[#E9A68A]/5 rounded-full blur-[100px] -mr-32 -mt-32"></div>
                  </div>
                </div>
              </div>
            )}
          </div>
        </section>
        {/* MIDDLE SECTION: PULSE & ANCHORS */}
        <div className="grid grid-cols-1 lg:grid-cols-12 gap-8">
          <div className="lg:col-span-7">
            <div className="bg-white p-10 rounded-[2rem] border border-[#E9A68A]/10 shadow-sm h-full">
              <h3 className="text-lg font-bold mb-6 flex items-center gap-2 text-[#2D1B0D]">
                <ShieldCheck className="text-[#E9A68A] w-6 h-6" />
                Strategic Anchors
              </h3>
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div className="p-6 bg-[#FDF8F5] rounded-3xl border border-[#E9A68A]/5">
                  <p className="text-[10px] font-black text-[#E9A68A] uppercase mb-3 tracking-widest">Rest Ethic</p>
                  <p className="text-sm text-[#2D1B0D]/70 font-medium leading-relaxed">Reframing rest as a performance prerequisite for creatives rather than a reward.</p>
                </div>
                <div className="p-6 bg-[#FDF8F5] rounded-3xl border border-[#E9A68A]/5">
                  <p className="text-[10px] font-black text-[#E9A68A] uppercase mb-3 tracking-widest">Temporal Opt.</p>
                  <p className="text-sm text-[#2D1B0D]/70 font-medium leading-relaxed">Aligning output with ultradian cycles (90-min blocks) and biological rhythms.</p>
                </div>
              </div>
            </div>
          </div>
          <aside className="lg:col-span-5">
            <div className="bg-[#2D1B0D] rounded-[2rem] p-10 text-white relative overflow-hidden shadow-xl h-full flex flex-col justify-between">
              <div className="relative z-10">
                <div className="flex items-center justify-between mb-10">
                  <h3 className="text-[10px] font-black uppercase tracking-[0.3em] text-[#E9A68A]">System Pulse</h3>
                  <button 
                    onClick={syncData}
                    className={`p-2 rounded-full bg-white/5 hover:bg-white/10 transition-colors ${isSyncing ? 'animate-spin' : ''}`}
                  >
                    <RefreshCw className="w-4 h-4 text-[#E9A68A]" />
                  </button>
                </div>
                <div className="space-y-10">
                  <div>
                    <p className="text-6xl font-bold mb-2 tracking-tighter">94.2%</p>
                    <p className="text-[11px] text-[#E9A68A] font-bold uppercase tracking-widest opacity-80">Somatic Safety Index</p>
                  </div>
                  <div className="grid grid-cols-2 gap-4">
                    <div className="p-5 bg-white/5 rounded-3xl border border-white/5">
                      <div className="flex items-center gap-2 mb-3">
                        <Sun className="w-5 h-5 text-[#E9A68A]" />
                        <span className="text-[10px] font-black text-white/40 uppercase">Circadian</span>
                      </div>
                      <p className="text-xl font-bold text-white">+22%</p>
                    </div>
                    <div className="p-5 bg-white/5 rounded-3xl border border-white/5">
                      <div className="flex items-center gap-2 mb-3">
                        <Coffee className="w-5 h-5 text-[#E9A68A]" />
                        <span className="text-[10px] font-black text-white/40 uppercase">Recovery</span>
                      </div>
                      <p className="text-xl font-bold text-white">68%</p>
                    </div>
                  </div>
                </div>
              </div>
              <div className="relative z-10 pt-8 mt-8 border-t border-white/10 flex justify-between items-end">
                <div className="flex flex-col">
                  <p className="text-[10px] text-[#E9A68A] font-bold uppercase mb-1 tracking-widest">Status</p>
                  <p className="text-xs font-bold text-white uppercase tracking-tighter italic">Signal Optimal</p>
                </div>
                <div className="w-2.5 h-2.5 rounded-full bg-[#E9A68A] animate-pulse shadow-[0_0_12px_#E9A68A]"></div>
              </div>
            </div>
          </aside>
        </div>
        {/* FOOTER SECTION: ATTRIBUTION & DATE SELECTOR */}
        <footer className="w-full mt-12">
          <div className="p-12 bg-[#2D1B0D] rounded-[2.5rem] text-white text-center shadow-2xl relative overflow-hidden border border-[#E9A68A]/5">
             <div className="relative z-10 flex flex-col items-center gap-4">
               <div className="flex items-center gap-3 mb-2">
                 <div className="h-[1px] w-8 bg-[#E9A68A]/40"></div>
                 <p className="text-[10px] font-black text-[#E9A68A] uppercase tracking-[0.4em]">Designer Credit</p>
                 <div className="h-[1px] w-8 bg-[#E9A68A]/40"></div>
               </div>
               <p className="text-xl md:text-2xl font-medium leading-relaxed max-w-2xl mx-auto tracking-tight">
                 "Designed by <span className="text-[#E9A68A] font-bold">Irene Mutwiri, M.Ed.</span> for <span className="text-[#E9A68A] font-bold">@WellbyCami</span>."
               </p>
             </div>
             <div className="relative z-10 flex flex-col items-center gap-4 pt-10 mt-10 border-t border-white/5 w-full max-w-sm mx-auto">
                <div className="flex items-center gap-2 text-[#E9A68A]">
                  <Calendar className="w-4 h-4" />
                  <label htmlFor="last-updated" className="text-[10px] font-black uppercase tracking-[0.2em]">Last updated on</label>
                </div>
                <input 
                  id="last-updated"
                  type="date" 
                  value={lastUpdated}
                  onChange={(e) => setLastUpdated(e.target.value)}
                  className="bg-[#3D2614] text-white text-sm border border-[#E9A68A]/10 rounded-2xl px-6 py-3 focus:outline-none focus:ring-2 focus:ring-[#E9A68A] cursor-pointer w-full text-center transition-all hover:bg-[#4D311A]"
                />
             </div>
             <div className="absolute top-0 left-0 w-64 h-64 bg-[#E9A68A]/5 rounded-full blur-[80px] -ml-32 -mt-32"></div>
             <div className="absolute bottom-0 right-0 w-64 h-64 bg-[#E9A68A]/5 rounded-full blur-[80px] -mr-32 -mb-32"></div>
          </div>
        </footer>

      </main>
    </div>
  );
};

export default App;
