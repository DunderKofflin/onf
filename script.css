let salesChart, brandChart, costChart, rankingChart;

// 실제 데이터
const monthlyData = {
    labels: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월'],
    totals: [3.9, 3.7, 5.1, 5.2, 5.5, 5.2, 5.2, 5.7]
};

const brandData = {
    '오테이블': [1.46, 1.39, 1.80, 2.09, 2.30, 1.92, 1.73, 2.05],
    '오이탈리안': [1.36, 1.28, 1.38, 1.19, 1.33, 1.27, 1.40, 1.46],
    '키타야': [1.08, 1.03, 1.32, 1.21, 1.31, 1.40, 1.38, 1.46],
    '루베르데': [0, 0, 0.57, 0.69, 0.60, 0.64, 0.71, 0.73]
};

const costRateData = {
    '오테이블': [35.83, 38.33, 34.30, 36.92, 36.77, 33.58, 38.39, 34.88],
    '오이탈리안': [32.29, 36.84, 31.28, 31.65, 36.05, 33.31, 36.25, 32.65],
    '키타야': [34.36, 34.49, 32.62, 35.28, 34.04, 32.86, 35.03, 35.30],
    '루베르데': [null, null, 33.90, 36.44, 31.16, 33.63, 35.02, 31.44]
};

// 현재 시간 업데이트
function updateTime() {
    const now = new Date();
    document.getElementById('lastUpdate').textContent = 
        now.toLocaleString('ko-KR', {
            year: 'numeric',
            month: '2-digit',
            day: '2-digit',
            hour: '2-digit',
            minute: '2-digit'
        });
}

// 탭 전환
function switchTab(tabName) {
    // 탭 버튼 업데이트
    document.querySelectorAll('.tab').forEach(tab => tab.classList.remove('active'));
    event.target.classList.add('active');
    
    // 탭 내용 전환
    document.querySelectorAll('[id$="-tab"]').forEach(tab => tab.style.display = 'none');
    document.getElementById(tabName + '-tab').style.display = 'block';
    
    // 차트 생성/업데이트
    setTimeout(() => {
        if (tabName === 'overview' && !salesChart) {
            createSalesChart();
        } else if (tabName === 'monthly') {
            createBrandChart();
            createCostChart();
        } else if (tabName === 'comparison') {
            createRankingChart();
        }
    }, 100);
}

// 전체 매출 차트
function createSalesChart() {
    const ctx = document.getElementById('salesChart').getContext('2d');
    
    if (salesChart) {
        salesChart.destroy();
    }
    
    salesChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: monthlyData.labels,
            datasets: [{
                label: '총 매출 (억원)',
                data: monthlyData.totals,
                borderColor: '#667eea',
                backgroundColor: 'rgba(102, 126, 234, 0.1)',
                borderWidth: 3,
                fill: true,
                tension: 0.4,
                pointBackgroundColor: '#667eea',
                pointBorderColor: '#fff',
                pointBorderWidth: 2,
                pointRadius: 5
            }]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: { display: false }
            },
            scales: {
                y: {
                    beginAtZero: false,
                    min: 3,
                    max: 6,
                    grid: { color: 'rgba(0,0,0,0.1)' }
                },
                x: {
                    grid: { display: false }
                }
            }
        }
    });
}

// 브랜드별 차트
function createBrandChart() {
    const ctx = document.getElementById('brandChart').getContext('2d');
    
    if (brandChart) {
        brandChart.destroy();
    }
    
    const datasets = Object.keys(brandData).map((brand, index) => {
        const colors = ['#667eea', '#f093fb', '#4facfe', '#43e97b'];
        return {
            label: brand,
            data: brandData[brand],
            borderColor: colors[index],
            backgroundColor: colors[index] + '20',
            borderWidth: 2,
            tension: 0.3
        };
    });
    
    brandChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: monthlyData.labels,
            datasets: datasets
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: {
                    display: true,
                    position: 'top',
                    labels: {
                        usePointStyle: true,
                        padding: 15,
                        font: { size: 11 }
                    }
                }
            },
            scales: {
                y: {
                    beginAtZero: true,
                    grid: { color: 'rgba(0,0,0,0.1)' }
                },
                x: {
                    grid: { display: false }
                }
            }
        }
    });
}

// 원가율 차트
function createCostChart() {
    const ctx = document.getElementById('costChart').getContext('2d');
    
    if (costChart) {
        costChart.destroy();
    }
    
    const datasets = Object.keys(costRateData).map((brand, index) => {
        const colors = ['#667eea', '#f093fb', '#4facfe', '#43e97b'];
        return {
            label: brand,
            data: costRateData[brand],
            borderColor: colors[index],
            backgroundColor: colors[index] + '20',
            borderWidth: 2,
            tension: 0.3,
            spanGaps: true
        };
    });
    
    costChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: monthlyData.labels,
            datasets: datasets
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: {
                    display: true,
                    position: 'top',
                    labels: {
                        usePointStyle: true,
                        padding: 15,
                        font: { size: 11 }
                    }
                }
            },
            scales: {
                y: {
                    min: 25,
                    max: 40,
                    grid: { color: 'rgba(0,0,0,0.1)' },
                    ticks: {
                        callback: function(value) {
                            return value + '%';
                        }
                    }
                },
                x: {
                    grid: { display: false }
                }
            }
        }
    });
}

// 순위 차트
function createRankingChart() {
    const ctx = document.getElementById('rankingChart').getContext('2d');
    
    if (rankingChart) {
        rankingChart.destroy();
    }
    
    const rankingData = {
        labels: ['오이탈리안\n광교', '오테이블\n광교', '루베르데\n광교', '키타야\n수원역', '키타야\n광교', '오테이블\n행궁', '오이탈리안\n동탄', '키타야\n행궁', '오테이블\n목동'],
        sales: [11063, 10926, 7277, 6349, 5455, 5373,