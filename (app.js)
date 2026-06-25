// 1. Initialize Mermaid.js
mermaid.initialize({ startOnLoad: true, theme: 'dark' });

// 2. Dark/Light Theme Toggle
const themeToggleBtn = document.getElementById('theme-toggle');
const htmlTag = document.documentElement;

themeToggleBtn.addEventListener('click', () => {
    const currentTheme = htmlTag.getAttribute('data-theme');
    const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
    htmlTag.setAttribute('data-theme', newTheme);
    
    // Update Mermaid theme dynamically (requires re-render in complex setups, simplified here)
    mermaid.initialize({ theme: newTheme === 'dark' ? 'dark' : 'default' });
    
    // Update button icon
    themeToggleBtn.innerHTML = newTheme === 'dark' ? '<i class="fas fa-sun"></i> Light Mode' : '<i class="fas fa-moon"></i> Dark Mode';
});

// 3. WACC Calculator Logic
function calculateWACC() {
    const Re = parseFloat(document.getElementById('costEq').value) / 100;
    const Rd = parseFloat(document.getElementById('costDebt').value) / 100;
    const T = parseFloat(document.getElementById('taxRate').value) / 100;
    const We = parseFloat(document.getElementById('weightEq').value) / 100;
    const Wd = parseFloat(document.getElementById('weightDebt').value) / 100;

    // Validate weights equal 100%
    if (Math.abs((We + Wd) - 1.0) > 0.01) {
        alert("Weight of Equity and Debt must equal 100%");
        return;
    }

    const wacc = (We * Re) + (Wd * Rd * (1 - T));
    const waccPercentage = (wacc * 100).toFixed(2);

    document.getElementById('waccResult').innerText = `WACC: ${waccPercentage}%`;
}

// 4. Chart.js Dashboard Initialization (Hero Section)
document.addEventListener('DOMContentLoaded', function() {
    const ctx = document.getElementById('heroChart').getContext('2d');
    
    // Gradient fill for the chart
    let gradient = ctx.createLinearGradient(0, 0, 0, 400);
    gradient.addColorStop(0, 'rgba(59, 130, 246, 0.5)');
    gradient.addColorStop(1, 'rgba(59, 130, 246, 0.0)');

    new Chart(ctx, {
        type: 'line',
        data: {
            labels: ['2021', '2022', '2023', '2024', '2025E', '2026E'],
            datasets: [{
                label: 'Projected Enterprise Free Cash Flow ($M)',
                data: [120, 150, 180, 175, 210, 250],
                borderColor: '#3b82f6',
                backgroundColor: gradient,
                borderWidth: 3,
                fill: true,
                tension: 0.4 // Smooth curves
            }]
        },
        options: {
            responsive: true,
            plugins: {
                legend: { labels: { color: '#a0aec0' } }
            },
            scales: {
                x: { ticks: { color: '#a0aec0' } },
                y: { ticks: { color: '#a0aec0' } }
            }
        }
    });
});
