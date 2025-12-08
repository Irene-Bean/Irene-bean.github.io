<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Irene Mutwiri, M.Ed. | Candidate Experience Associate</title>
    <!-- External Libraries for PDF Generation -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700;900&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Roboto', sans-serif; background-color: #F0F4F8; color: #1E293B; }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container { height: 350px; }
        }
        .card {
            background-color: white;
            border-radius: 0.75rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            padding: 1.5rem;
            transition: transform 0.2s;
        }
        .card:hover { transform: translateY(-2px); box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1); }
        .step-circle {
            width: 3rem;
            height: 3rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            margin-bottom: 0.5rem;
        }
        /* Style for the sticky header that needs to be toggled */
        .sticky-header {
            position: sticky;
            top: 0;
            z-index: 50;
        }
    </style>
</head>
<body class="bg-slate-50">
    <header id="app-header" class="bg-white shadow-md sticky-header">
        <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8 flex justify-between items-center">
            <div>
                <h1 class="text-3xl font-black tracking-tight text-gray-900">
                    <span class="text-blue-600">Irene Mutwiri, M.Ed. </span> | ezCatering Cover Letter
                </h1>
                <p class="mt-1 text-sm text-gray-500 font-medium tracking-wide uppercase">Candidate Experience Associate</p>
            </div>
            <div class="flex items-center">
                <button id="pdf-download-button" onclick="generatePdf()" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg shadow-md transition duration-150 ease-in-out flex items-center">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 mr-2">
                        <path fill-rule="evenodd" d="M12 2.25a.75.75 0 0 1 .75.75v11.69l3.44-3.44a.75.75 0 1 1 1.06 1.06l-4.75 4.75a.75.75 0 0 1-1.06 0l-4.75-4.75a.75.75 0 1 1 1.06-1.06l3.44 3.44V3a.75.75 0 0 1 .75-.75ZM7.5 18a.75.75 0 0 0 0 1.5h9a.75.75 0 0 0 0-1.5h-9Z" clip-rule="evenodd" />
                    </svg>                      
                    Download as PDF
                </button>
            </div>
        </div>
    </header>
    <main id="infographic-content" class="max-w-7xl mx-auto py-10 px-4 sm:px-6 lg:px-8">
        <!-- Introduction Section -->
        <section class="mb-12">
            <div class="card bg-gradient-to-r from-blue-600 to-cyan-500 text-white">
                <h2 class="text-2xl font-bold mb-4">My Analysis</h2>
                <p class="text-lg leading-relaxed opacity-90">
                    Candidate experience is not just about scheduling; it's shaping each step with purpose. The graphic here is my brief analysis of the current state of ezCatering's candidate experience, along with some ideas for upping the Talent team's already strong record! Within my first 90 days as the candidate experience associate, my priority would be finding and turning quick fixes into real gains.
                </p>
            </div>
        </section>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                        <!-- Section 1: Interview Sentiment (Data-Grounded) -->
            <section class="col-span-1">
                <div class="card h-full">
                    <h3 class="text-xl font-bold text-gray-800 mb-2 border-l-4 border-indigo-600 pl-3">A majority of ezCatering candidates rate their experience positively.</h3>
                    <p class="text-gray-600 mb-6">
                        Actual candidate feedback from Glassdoor demonstrates that ezCatering sets a high bar for candidate experience. Here's the precise breakdown of candidate sentiment. Prioritizing the small process improvements that address "neutral" feedback would be my first step to help raise positive sentiment up closer to 70%.
                    </p>
                    <div class="chart-container">
                        <canvas id="sentimentChart"></canvas>
                    </div>
                    <div class="mt-4 text-center">
                        <p class="text-3xl font-bold text-green-600">53%</p>
                        <p class="text-sm text-gray-500">Positive Experience</p>
                    </div>
                </div>
            </section>
            <!-- Section 2: Application Channels (Data-Grounded) -->
            <section class="col-span-1">
                <div class="card h-full">
                    <h3 class="text-xl font-bold text-gray-800 mb-2 border-l-4 border-yellow-500 pl-3">81% of ezCatering candidates report applying online.</h3>
                    <p class="text-gray-600 mb-6">
                        This number shows that ezCatering's online presence is undeniable. I would be curious to know the candidate journey into the application; whether they are redirected from a job board or applying directly n ezCatering's website. There may also be an opportunity to scale employee referral programs.
                    </p>
                    <div class="chart-container">
                        <canvas id="channelsChart"></canvas>
                    </div>
                    <div class="mt-4 text-center">
                        <p class="text-3xl font-bold text-yellow-600">81%</p>
                        <p class="text-sm text-gray-500">Applied Online</p>
                    </div>
                </div>
            </section>
            <!-- Section 3: Qualitative Themes -->
            <section class="col-span-1 md:col-span-2">
                <div class="card">
                    <h3 class="text-xl font-bold text-gray-800 mb-2 border-l-4 border-indigo-600 pl-3">Key Highlights</h3>
                    <ul class="space-y-3 pt-4">
                        <!-- Strength: Interviewer Quality -->
                        <li class="flex items-start">
                            <span class="text-green-500 mr-2 text-xl">&#10003;</span>
                            <div>
                                <p class="font-medium text-gray-900">Interviewer Quality & Support</p>
                                <p class="text-sm text-gray-600">Candidates highlight interviewers and recruiters as professional, kind, genuine, and supportive, often describing the overall experience as "top-notch" or "fun."</p>
                            </div>
                        </li>
                        <!-- Strength: Transparency & Prep -->
                        <li class="flex items-start">
                            <span class="text-green-500 mr-2 text-xl">&#10003;</span>
                            <div>
                                <p class="font-medium text-gray-900">High Transparency & Preparation</p>
                                <p class="text-sm text-gray-600">The hiring process is praised for transparency, clear communication, and providing helpful preparation materials (questions, videos) in advance.</p>
                            </div>
                        </li>
                        <!-- Challenge: Internal Consistency -->
                        <li class="flex items-start">
                            <span class="text-red-500 mr-2 text-xl">&#10007;</span>
                            <div>
                                <p class="font-medium text-gray-900">Internal Alignment & Consistency</p>
                                <p class="text-sm text-gray-600">A significant opportunity exists to improve internal alignment, structural consistency across teams.</p>
                            </div>
                        </li>
                        <!-- Observation: Time to Hire -->
                        <li class="flex items-start">
                            <span class="text-yellow-500 mr-2 text-xl">&#9888;</span>
                            <div>
                                <p class="font-medium text-gray-900">Variable Time-to-Hire</p>
                                <p class="text-sm text-gray-600">The average hiring time is approximately 17.76 days, with time-to-hire ranging from one day for some roles up to 49 days for others. There may be opportunity here to standardize and streamline workflows.</p>
                            </div>
                        </li>
                    </ul>
                </div>
            </section>
            <!-- Section: Recommendation Callout (cNPS) -->
            <section class="col-span-1 md:col-span-2">
                <div class="card bg-blue-50 border-l-4 border-blue-600 p-6">
                    <h3 class="text-xl font-bold text-blue-800 mb-3 flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-6 h-6 mr-3">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v3.75m9-.75a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9 3.75h.008v.008H12Z" />
                        </svg>
                        My Recommendation
                    </h3>
                    <p class="text-lg text-blue-700 leading-relaxed">
                        I recommend tracking a Candidate Net Promoter Score (cNPS). This number takes what people say in their own words, turns it into something measurable, then links it clearly to hiring outcomes along with how strong your company looks to job seekers. 
                    </p>
                    <p class="mt-2 text-sm text-blue-600 font-semibold">
                        Success Metric: cNPS (Promoters - Detractors)
                    </p>
                </div>
            </section>
            <!-- Section 4: The Optimization Cycle (Diagram) -->
            <section class="col-span-1 md:col-span-2">
                <div class="card">
                    <h3 class="text-xl font-bold text-gray-800 mb-2 border-l-4 border-gray-800 pl-3">My Approach</h3>
                    <p class="text-gray-600 mb-8">
                        Moving beyond simple execution requires a cyclical approach to operations. This model demonstrates how we proactively suggest improvements and refine best practices based on data.
                    </p>
                                        <div class="grid grid-cols-1 md:grid-cols-4 gap-4 text-center relative">
                        <!-- Connecting Line (Desktop) -->
                        <div class="hidden md:block absolute top-1/2 left-0 w-full h-1 bg-gray-200 -z-10 transform -translate-y-1/2"></div>
                        <!-- Step 1 -->
                        <div class="flex flex-col items-center bg-white p-4">
                            <div class="step-circle bg-blue-600 text-xl shadow-lg">1</div>
                            <h4 class="font-bold text-lg mt-2 text-blue-800">Assess</h4>
                            <p class="text-sm text-gray-500 mt-1">Analyze current state of candidate experience journey and workflows</p>
                        </div>
                        <!-- Step 2 -->
                        <div class="flex flex-col items-center bg-white p-4">
                            <div class="step-circle bg-cyan-500 text-xl shadow-lg">2</div>
                            <h4 class="font-bold text-lg mt-2 text-cyan-800">Suggest</h4>
                            <p class="text-sm text-gray-500 mt-1">Propose low-lift, high-impact fixes to target "neutral" experiences </p>
                        </div>
                        <!-- Step 3 -->
                        <div class="flex flex-col items-center bg-white p-4">
                            <div class="step-circle bg-orange-500 text-xl shadow-lg">3</div>
                            <h4 class="font-bold text-lg mt-2 text-orange-800">Enhance</h4>
                            <p class="text-sm text-gray-500 mt-1">Co-create and refine SOPs, best practices, and documentation</p>
                        </div>
                        <!-- Step 4 -->
                        <div class="flex flex-col items-center bg-white p-4">
                            <div class="step-circle bg-gray-800 text-xl shadow-lg">4</div>
                            <h4 class="font-bold text-lg mt-2 text-gray-800">Report</h4>
                            <p class="text-sm text-gray-500 mt-1">Implement, validate effectiveness with data, and reiterate</p>
                        </div>
                    </div>
                </div>
            </section>
        </div>
                <footer class="mt-12 text-center text-gray-400 text-sm">
            <p>Thanks for reading and for considering my application for the Candidate Experience Associate role! </p>
            <p> Designed and edited by <a href="https://www.linkedin.com/in/irenemutwiri/">Irene Mutwiri, M.Ed.</a> for ezCatering. (Last Updated December 08, 2025)</p>
         <style>
a:link { color: blue; background-color: transparent; text-decoration: none; } a:visited { color: pink; background-color: transparent; text-decoration: none; } a:hover { color: red; background-color: transparent; text-decoration: underline; } a:active { color: yellow; background-color: transparent; text-decoration: underline; } </style>
        </footer>
    </main>
    <script>
        // PDF GENERATION FUNCTION
        async function generatePdf() {
            const input = document.getElementById('infographic-content');
            const pdfButton = document.getElementById('pdf-download-button');
            const header = document.getElementById('app-header');
                        // 1. Temporarily hide elements that shouldn't be in the PDF
            pdfButton.style.display = 'none';
            header.classList.remove('sticky-header'); // Remove sticky position for clean capture
            header.style.position = 'static'; 
            try {
                // 2. Generate Canvas from HTML content
                const canvas = await html2canvas(input, {
                    scale: 2, // Higher scale for better resolution
                    logging: false,
                    useCORS: true
                });
                const imgData = canvas.toDataURL('image/jpeg', 0.9);
                const { jsPDF } = window.jspdf;
                                // A4 dimensions in mm
                const pdfWidth = 210; 
                const pdfHeight = 297; 
                                // Content size calculations
                const imgWidth = canvas.width;
                const imgHeight = canvas.height;
                const ratio = imgHeight / imgWidth;
                                // Calculate the dimensions of the content image inside the PDF (10mm margins)
                const contentWidth = pdfWidth - 20; 
                const contentHeight = contentWidth * ratio;
                const doc = new jsPDF('p', 'mm', 'a4');
                let currentPagePosition = 0;
                                // 3. Multi-page slicing logic for long infographics
                const pageHeight = pdfHeight - 20; // Effective page height with margins
                if (contentHeight > pageHeight) {
                    let pageNumber = 1;
                                        while (currentPagePosition < contentHeight) {
                        if (pageNumber > 1) {
                            doc.addPage();
                        }
                                                // Add the image slice to the PDF
                        // The third argument (y-position on PDF) is fixed at 10 (top margin)
                        // The fourth argument (-currentPagePosition) controls the vertical offset of the image inside the PDF
                        doc.addImage(imgData, 'JPEG', 10, 10 - currentPagePosition, contentWidth, contentHeight);
                        currentPagePosition += pageHeight;
                        pageNumber++;
                    }
                } else {
                    // Single page content fits well
                    doc.addImage(imgData, 'JPEG', 10, 10, contentWidth, contentHeight);
                }
                doc.save('Irene Mutwiri, M.Ed. | Candidate Experience Associate (CoverLetter).pdf');
            } catch (error) {
                console.error("PDF generation failed:", error);
                // Use a custom modal or alert fallback if absolutely necessary, but prefer console logging
                console.log("PDF generation failed. Check console for error details."); 
            } finally {
                // 4. Restore elements to their original state
                pdfButton.style.display = 'block';
                header.classList.add('sticky-header');
                header.style.position = 'sticky'; 
            }
        }
        // CHART CONFIGURATION (Remains the same)
        function splitLabel(label, maxLength) {
            if (label.length <= maxLength) return label;
            const words = label.split(' ');
            const lines = [];
            let currentLine = words[0];
            for (let i = 1; i < words.length; i++) {
                if (currentLine.length + 1 + words[i].length <= maxLength) {
                    currentLine += ' ' + words[i];
                } else {
                    lines.push(currentLine);
                    currentLine = words[i];
                }
            }
            lines.push(currentLine);
            return lines;
        }
        const sharedTooltipConfig = {
            callbacks: {
                title: function(tooltipItems) {
                    const item = tooltipItems[0];
                    let label = item.chart.data.labels[item.dataIndex];
                    if (Array.isArray(label)) {
                        return label.join(' ');
                    } else {
                        return label;
                    }
                }
            }
        };
        // --- Chart 1: Interview Sentiment (Data-Grounded) ---
        const ctxSentiment = document.getElementById('sentimentChart').getContext('2d');
                const sentimentLabels = ['Positive (53%)', 'Neutral (15%)', 'Negative (32%)'];
        const processedSentimentLabels = sentimentLabels.map(l => splitLabel(l, 16));
        new Chart(ctxSentiment, {
            type: 'doughnut',
            data: {
                labels: processedSentimentLabels,
                datasets: [{
                    data: [53, 15, 32],
                    backgroundColor: [
                        '#10B981', // Green for Positive
                        '#FCD34D', // Yellow for Neutral
                        '#F87171'  // Red for Negative
                    ],
                    borderWidth: 0,
                    hoverOffset: 8
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: sharedTooltipConfig
                },
                cutout: '70%'
            }
        });
        // --- Chart 2: Application Channels (Data-Grounded) ---
        const ctxChannels = document.getElementById('channelsChart').getContext('2d');
                // REFORMATTED LABELS: Shortened long channel names to prevent awkward line breaks/overlap
        const channelLabels = ['Online (81%)', 'Recruiter (10%)', 'Referral (6%)', 'Other (3%)'];
        const processedChannelLabels = channelLabels.map(l => splitLabel(l, 16));
        new Chart(ctxChannels, {
            type: 'doughnut',
            data: {
                labels: processedChannelLabels,
                datasets: [{
                    data: [81, 10, 6, 3],
                    backgroundColor: [
                        '#F97316', // Orange 500 (Applied Online)
                        '#2563EB', // Blue 600 (Recruiter)
                        '#06B6D4', // Cyan 500 (Referral)
                        '#94a3b8'  // Slate 400 (Other)
                    ],
                    borderWidth: 0,
                    hoverOffset: 8
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: sharedTooltipConfig
                },
                cutout: '70%'
            }
        });
    </script>
</body>
</html>
