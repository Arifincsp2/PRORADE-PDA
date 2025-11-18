<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PROTRADE PDA - Professional Trading Platform</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap');
        
        * {
            font-family: 'Inter', sans-serif;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .card-hover {
            transition: all 0.3s ease;
        }
        
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        .chart-bar {
            animation: growBar 1s ease-out;
        }
        
        @keyframes growBar {
            from { height: 0; }
            to { height: var(--bar-height); }
        }
        
        .pulse {
            animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: .5; }
        }
        
        .slide-in {
            animation: slideIn 0.5s ease-out;
        }
        
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .ticker {
            animation: scroll 30s linear infinite;
        }
        
        @keyframes scroll {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        .modal {
            display: none;
        }

        .modal.active {
            display: flex;
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Navigation -->
    <nav class="gradient-bg text-white shadow-lg sticky top-0 z-50">
        <div class="container mx-auto px-6 py-4">
            <div class="flex items-center justify-between">
                <div class="flex items-center space-x-4">
                    <div class="w-10 h-10 bg-white rounded-lg flex items-center justify-center">
                        <span class="text-purple-600 font-bold text-xl">P</span>
                    </div>
                    <div>
                        <h1 class="text-2xl font-bold">PROTRADE PDA</h1>
                        <p class="text-xs opacity-80">Professional Trading Platform</p>
                    </div>
                </div>
                <div class="hidden md:flex space-x-6">
                    <a href="#home" class="hover:text-purple-200 transition-colors">Home</a>
                    <a href="#features" class="hover:text-purple-200 transition-colors">Features</a>
                    <a href="#trading" class="hover:text-purple-200 transition-colors">Trading</a>
                    <a href="#analytics" class="hover:text-purple-200 transition-colors">Analytics</a>
                    <a href="#pricing" class="hover:text-purple-200 transition-colors">Pricing</a>
                </div>
                <div class="flex items-center space-x-4">
                    <button onclick="showLoginModal()" class="hidden md:block px-4 py-2 bg-white/20 rounded-lg hover:bg-white/30 transition-colors">Login</button>
                    <button onclick="showSignupModal()" class="px-6 py-2 bg-white text-purple-600 rounded-lg font-semibold hover:bg-purple-50 transition-colors">Get Started</button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="gradient-bg text-white py-20">
        <div class="container mx-auto px-6">
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div class="slide-in">
                    <h2 class="text-5xl font-bold mb-6 leading-tight">Trade Smarter with AI-Powered Analytics</h2>
                    <p class="text-xl mb-8 opacity-90">Join thousands of traders using PROTRADE PDA to maximize their trading potential with real-time data and advanced tools.</p>
                    <div class="flex space-x-4">
                        <button onclick="showSignupModal()" class="px-8 py-4 bg-white text-purple-600 rounded-xl font-bold text-lg hover:bg-purple-50 transition-all transform hover:scale-105">Start Trading Free</button>
                        <button onclick="scrollToSection('features')" class="px-8 py-4 bg-white/20 rounded-xl font-bold text-lg hover:bg-white/30 transition-colors">Learn More</button>
                    </div>
                    <div class="mt-8 flex items-center space-x-8">
                        <div>
                            <div class="text-3xl font-bold">50K+</div>
                            <div class="text-sm opacity-80">Active Traders</div>
                        </div>
                        <div>
                            <div class="text-3xl font-bold">$2.5B+</div>
                            <div class="text-sm opacity-80">Trading Volume</div>
                        </div>
                        <div>
                            <div class="text-3xl font-bold">99.9%</div>
                            <div class="text-sm opacity-80">Uptime</div>
                        </div>
                    </div>
                </div>
                <div class="relative">
                    <div class="bg-white/10 backdrop-blur-lg rounded-3xl p-8 shadow-2xl">
                        <div class="bg-gradient-to-br from-green-400 to-blue-500 rounded-2xl p-6 mb-4">
                            <div class="text-sm opacity-80 mb-2">Total Portfolio Value</div>
                            <div class="text-4xl font-bold mb-2">$124,850.00</div>
                            <div class="flex items-center text-sm">
                                <span class="text-green-200">▲ +12.5%</span>
                                <span class="ml-2 opacity-70">This month</span>
                            </div>
                        </div>
                        <div class="grid grid-cols-2 gap-4">
                            <div class="bg-white/10 rounded-xl p-4">
                                <div class="text-xs opacity-70 mb-1">Active Trades</div>
                                <div class="text-2xl font-bold">24</div>
                            </div>
                            <div class="bg-white/10 rounded-xl p-4">
                                <div class="text-xs opacity-70 mb-1">Win Rate</div>
                                <div class="text-2xl font-bold">78.3%</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Market Ticker -->
    <div class="bg-gray-900 text-white py-3 overflow-hidden">
        <div class="ticker flex space-x-12">
            <div class="flex space-x-12 min-w-full">
                <div class="flex items-center space-x-2"><span class="font-semibold">BTC/USD</span><span class="text-green-400">$45,250</span><span class="text-xs text-green-400">+2.5%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">ETH/USD</span><span class="text-red-400">$2,548</span><span class="text-xs text-red-400">-1.2%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">EUR/USD</span><span class="text-green-400">1.0845</span><span class="text-xs text-green-400">+0.8%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">GBP/USD</span><span class="text-green-400">1.2654</span><span class="text-xs text-green-400">+1.5%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">XRP/USD</span><span class="text-green-400">$0.65</span><span class="text-xs text-green-400">+3.2%</span></div>
            </div>
            <div class="flex space-x-12 min-w-full">
                <div class="flex items-center space-x-2"><span class="font-semibold">BTC/USD</span><span class="text-green-400">$45,250</span><span class="text-xs text-green-400">+2.5%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">ETH/USD</span><span class="text-red-400">$2,548</span><span class="text-xs text-red-400">-1.2%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">EUR/USD</span><span class="text-green-400">1.0845</span><span class="text-xs text-green-400">+0.8%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">GBP/USD</span><span class="text-green-400">1.2654</span><span class="text-xs text-green-400">+1.5%</span></div>
                <div class="flex items-center space-x-2"><span class="font-semibold">XRP/USD</span><span class="text-green-400">$0.65</span><span class="text-xs text-green-400">+3.2%</span></div>
            </div>
        </div>
    </div>

    <!-- Features Section -->
    <section id="features" class="py-20 bg-white">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold text-gray-800 mb-4">Powerful Trading Features</h2>
                <p class="text-xl text-gray-600">Everything you need to trade like a professional</p>
            </div>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="card-hover bg-gradient-to-br from-blue-50 to-purple-50 rounded-2xl p-8">
                    <div class="w-16 h-16 bg-gradient-to-br from-blue-500 to-purple-600 rounded-2xl flex items-center justify-center text-white text-3xl mb-4">📊</div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-3">Real-Time Analytics</h3>
                    <p class="text-gray-600">Advanced charting tools with live market data and technical indicators for informed decision making.</p>
                </div>
                <div class="card-hover bg-gradient-to-br from-green-50 to-teal-50 rounded-2xl p-8">
                    <div class="w-16 h-16 bg-gradient-to-br from-green-500 to-teal-600 rounded-2xl flex items-center justify-center text-white text-3xl mb-4">🤖</div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-3">AI Trading Signals</h3>
                    <p class="text-gray-600">Machine learning algorithms analyze market patterns to provide actionable trading signals.</p>
                </div>
                <div class="card-hover bg-gradient-to-br from-orange-50 to-red-50 rounded-2xl p-8">
                    <div class="w-16 h-16 bg-gradient-to-br from-orange-500 to-red-600 rounded-2xl flex items-center justify-center text-white text-3xl mb-4">🔒</div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-3">Bank-Level Security</h3>
                    <p class="text-gray-600">Military-grade encryption and 2FA authentication to keep your funds and data secure.</p>
                </div>
                <div class="card-hover bg-gradient-to-br from-pink-50 to-rose-50 rounded-2xl p-8">
                    <div class="w-16 h-16 bg-gradient-to-br from-pink-500 to-rose-600 rounded-2xl flex items-center justify-center text-white text-3xl mb-4">⚡</div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-3">Lightning Fast Execution</h3>
                    <p class="text-gray-600">Execute trades in milliseconds with our high-performance trading engine.</p>
                </div>
                <div class="card-hover bg-gradient-to-br from-indigo-50 to-blue-50 rounded-2xl p-8">
                    <div class="w-16 h-16 bg-gradient-to-br from-indigo-500 to-blue-600 rounded-2xl flex items-center justify-center text-white text-3xl mb-4">📱</div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-3">Multi-Platform Access</h3>
                    <p class="text-gray-600">Trade anywhere with our web, mobile, and desktop applications.</p>
                </div>
                <div class="card-hover bg-gradient-to-br from-yellow-50 to-orange-50 rounded-2xl p-8">
                    <div class="w-16 h-16 bg-gradient-to-br from-yellow-500 to-orange-600 rounded-2xl flex items-center justify-center text-white text-3xl mb-4">💎</div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-3">Premium Support</h3>
                    <p class="text-gray-600">24/7 dedicated support team ready to assist you with any trading questions.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Trading Dashboard Preview -->
    <section id="trading" class="py-20 bg-gray-100">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold text-gray-800 mb-4">Professional Trading Dashboard</h2>
                <p class="text-xl text-gray-600">Manage your portfolio with intuitive tools</p>
            </div>
            <div class="bg-white rounded-3xl shadow-2xl overflow-hidden">
                <div class="bg-gradient-to-r from-purple-600 to-blue-600 text-white p-6">
                    <div class="flex items-center justify-between">
                        <h3 class="text-2xl font-bold">Trading Dashboard</h3>
                        <button onclick="showDashboard()" class="px-6 py-2 bg-white text-purple-600 rounded-lg font-semibold hover:bg-purple-50 transition-colors">Open Dashboard</button>
                    </div>
                </div>
                <div class="p-8">
                    <div class="grid md:grid-cols-4 gap-6 mb-8">
                        <div class="bg-gradient-to-br from-green-500 to-green-600 text-white rounded-2xl p-6">
                            <div class="text-sm opacity-80 mb-2">Total Balance</div>
                            <div class="text-3xl font-bold">$124,850</div>
                            <div class="text-sm mt-2">+$12,450 (11.1%)</div>
                        </div>
                        <div class="bg-gradient-to-br from-blue-500 to-blue-600 text-white rounded-2xl p-6">
                            <div class="text-sm opacity-80 mb-2">Today's Profit</div>
                            <div class="text-3xl font-bold">$2,450</div>
                            <div class="text-sm mt-2">+3.2% from yesterday</div>
                        </div>
                        <div class="bg-gradient-to-br from-purple-500 to-purple-600 text-white rounded-2xl p-6">
                            <div class="text-sm opacity-80 mb-2">Active Trades</div>
                            <div class="text-3xl font-bold">24</div>
                            <div class="text-sm mt-2">18 winning positions</div>
                        </div>
                        <div class="bg-gradient-to-br from-orange-500 to-red-600 text-white rounded-2xl p-6">
                            <div class="text-sm opacity-80 mb-2">Win Rate</div>
                            <div class="text-3xl font-bold">78.3%</div>
                            <div class="text-sm mt-2">Above average</div>
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-8">
                        <div>
                            <h4 class="font-bold text-gray-800 mb-4 text-xl">Recent Trades</h4>
                            <div class="space-y-3">
                                <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                                    <div class="flex items-center space-x-3">
                                        <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center text-green-600 font-bold">B</div>
                                        <div>
                                            <div class="font-semibold text-gray-800">BTC/USD</div>
                                            <div class="text-sm text-gray-500">Buy • 0.05 BTC</div>
                                        </div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-bold text-green-600">+$150</div>
                                        <div class="text-sm text-gray-500">+3.2%</div>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                                    <div class="flex items-center space-x-3">
                                        <div class="w-10 h-10 bg-blue-100 rounded-full flex items-center justify-center text-blue-600 font-bold">E</div>
                                        <div>
                                            <div class="font-semibold text-gray-800">ETH/USD</div>
                                            <div class="text-sm text-gray-500">Buy • 2 ETH</div>
                                        </div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-bold text-green-600">+$85</div>
                                        <div class="text-sm text-gray-500">+1.8%</div>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                                    <div class="flex items-center space-x-3">
                                        <div class="w-10 h-10 bg-red-100 rounded-full flex items-center justify-center text-red-600 font-bold">E</div>
                                        <div>
                                            <div class="font-semibold text-gray-800">EUR/USD</div>
                                            <div class="text-sm text-gray-500">Sell • 1000 EUR</div>
                                        </div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-bold text-red-600">-$25</div>
                                        <div class="text-sm text-gray-500">-0.5%</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div>
                            <h4 class="font-bold text-gray-800 mb-4 text-xl">Performance Chart</h4>
                            <div class="bg-gray-50 rounded-xl p-6">
                                <div class="flex items-end justify-between h-48 space-x-2">
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 60%; height: 60%;"></div>
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 75%; height: 75%;"></div>
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 55%; height: 55%;"></div>
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 85%; height: 85%;"></div>
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 70%; height: 70%;"></div>
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 90%; height: 90%;"></div>
                                    <div class="flex-1 bg-gradient-to-t from-green-500 to-green-400 rounded-t-lg chart-bar" style="--bar-height: 95%; height: 95%;"></div>
                                </div>
                                <div class="flex justify-between mt-4 text-xs text-gray-500">
                                    <span>Mon</span>
                                    <span>Tue</span>
                                    <span>Wed</span>
                                    <span>Thu</span>
                                    <span>Fri</span>
                                    <span>Sat</span>
                                    <span>Sun</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Analytics Section -->
    <section id="analytics" class="py-20 bg-white">
        <div class="container mx-auto px-6">
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div>
                    <h2 class="text-4xl font-bold text-gray-800 mb-6">Advanced Analytics & Insights</h2>
                    <p class="text-xl text-gray-600 mb-8">Make data-driven decisions with our comprehensive analytics suite powered by AI and machine learning.</p>
                    <div class="space-y-4">
                        <div class="flex items-start space-x-4">
                            <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center flex-shrink-0">
                                <span class="text-2xl">📈</span>
                            </div>
                            <div>
                                <h4 class="font-bold text-gray-800 mb-1">Market Trends Analysis</h4>
                                <p class="text-gray-600">Real-time analysis of market trends and sentiment to help you stay ahead.</p>
                            </div>
                        </div>
                        <div class="flex items-start space-x-4">
                            <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center flex-shrink-0">
                                <span class="text-2xl">🎯</span>
                            </div>
                            <div>
                                <h4 class="font-bold text-gray-800 mb-1">Risk Management Tools</h4>
                                <p class="text-gray-600">Advanced risk assessment and portfolio optimization algorithms.</p>
                            </div>
                        </div>
                        <div class="flex items-start space-x-4">
                            <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center flex-shrink-0">
                                <span class="text-2xl">💡</span>
                            </div>
                            <div>
                                <h4 class="font-bold text-gray-800 mb-1">Smart Recommendations</h4>
                                <p class="text-gray-600">AI-powered trading suggestions based on your portfolio and market conditions.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="bg-gradient-to-br from-purple-100 to-blue-100 rounded-3xl p-8">
                    <div class="bg-white rounded-2xl p-6 shadow-lg mb-4">
                        <div class="flex items-center justify-between mb-4">
                            <h4 class="font-bold text-gray-800">Portfolio Distribution</h4>
                            <span class="text-sm text-gray-500">Updated 1 min ago</span>
                        </div>
                        <div class="space-y-3">
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span class="text-gray-600">Bitcoin (BTC)</span>
                                    <span class="font-semibold text-gray-800">45%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-3">
                                    <div class="bg-gradient-to-r from-orange-400 to-orange-600 h-3 rounded-full" style="width: 45%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span class="text-gray-600">Ethereum (ETH)</span>
                                    <span class="font-semibold text-gray-800">30%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-3">
                                    <div class="bg-gradient-to-r from-blue-400 to-blue-600 h-3 rounded-full" style="width: 30%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span class="text-gray-600">Forex</span>
                                    <span class="font-semibold text-gray-800">15%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-3">
                                    <div class="bg-gradient-to-r from-green-400 to-green-600 h-3 rounded-full" style="width: 15%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span class="text-gray-600">Others</span>
                                    <span class="font-semibold text-gray-800">10%</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-3">
                                    <div class="bg-gradient-to-r from-purple-400 to-purple-600 h-3 rounded-full" style="width: 10%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-white rounded-xl p-4 shadow-lg">
                            <div class="text-sm text-gray-500 mb-1">Total Return</div>
                            <div class="text-2xl font-bold text-green-600">+24.5%</div>
                        </div>
                        <div class="bg-white rounded-xl p-4 shadow-lg">
                            <div class="text-sm text-gray-500 mb-1">Sharpe Ratio</div>
                            <div class="text-2xl font-bold text-blue-600">2.8</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section id="pricing" class="py-20 bg-gray-100">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold text-gray-800 mb-4">Choose Your Plan</h2>
                <p class="text-xl text-gray-600">Start trading today with a plan that fits your needs</p>
            </div>
            <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
                <div class="bg-white rounded-3xl p-8 shadow-lg card-hover">
                    <div class="text-center mb-6">
                        <h3 class="text-2xl font-bold text-gray-800 mb-2">Starter</h3>
                        <div class="text-5xl font-bold text-gray-800 mb-2">$0</div>
                        <div class="text-gray-500">Free Forever</div>
                    </div>
                    <ul class="space-y-4 mb-8">
                        <li class="flex items-center"><span class="text-green-500 mr-2">✓</span> Basic Trading Tools</li>
                        <li class="flex items-center"><span class="text-green-500 mr
