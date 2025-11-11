---
layout: default
title: Beginner Guide
permalink: /trade-tracker/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ASTRONuri Trade Tracker</title>
    <style>
        /* --- General Layout --- */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e9eef2;
            color: #333;
            padding: 20px;
        }

        .tracker-container {
            display: grid;
            grid-template-columns: 3fr 1.2fr; 
            gap: 20px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .main-panel {
            background: #fff;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.08);
        }

        /* --- Right Panel (Status Panel) Overhaul --- */
        .status-panel {
            background: #2c3e50; 
            color: #ecf0f1; 
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        h1 {
            font-size: 1.8em;
            border-bottom: 2px solid #ddd;
            padding-bottom: 15px;
            margin-bottom: 20px;
            color: #007bff;
        }

        .section-box {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
        }

        legend {
            font-weight: bold;
            color: #0056b3;
            padding: 0 10px;
        }

        /* --- Input Grouping & Fields --- */
        .input-group-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
            align-items: flex-end;
        }

        .input-group-row.compact {
            gap: 10px;
            margin-bottom: 12px;
        }

        .input-group-row.compact > div {
            flex: 1;
        }

        .input-group-row.buttons {
            gap: 10px;
            margin-bottom: 0;
        }

        .input-group-row.buttons > * {
            flex: 1;
        }

        .input-field {
            display: flex;
            flex-direction: column;
        }

        .input-field.compact label {
            font-size: 0.8em;
            margin-bottom: 3px;
        }

        .input-field.compact input,
        .input-field.compact select {
            padding: 6px 8px;
            font-size: 0.85em;
            height: 32px;
        }
        
        .checkbox-group {
            display: flex;
            flex-direction: row;
            align-items: center;
            gap: 10px;
            padding-top: 8px; 
        }

        label {
            font-size: 0.9em;
            color: #555;
            margin-bottom: 5px;
            font-weight: 500;
        }

        input[type="number"], select, input[type="text"] {
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            width: 100%;
            box-sizing: border-box;
            font-size: 1em;
        }

        /* --- Buttons --- */
        .btn {
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            text-transform: uppercase;
            transition: background-color 0.2s, transform 0.1s;
            width: 100%;
            font-size: 0.85em;
        }

        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        .btn:active:not(:disabled) {
            transform: scale(0.98);
        }

        .btn-primary { background-color: #007bff; color: white; }
        .btn-primary:hover:not(:disabled) { background-color: #0056b3; }

        .btn-secondary { background-color: #6c757d; color: white; }
        .btn-secondary:hover:not(:disabled) { background-color: #5a6268; }

        .btn-danger { background-color: #dc3545; color: white; }
        .btn-danger:hover:not(:disabled) { background-color: #bd2130; }

        .btn-success { background-color: #28a745; color: white; }
        .btn-success:hover:not(:disabled) { background-color: #1e7e34; }

        .btn-error { background-color: #dc3545; color: white; }

        .btn-dark { background-color: #34495e; color: white; }
        .btn-dark:hover:not(:disabled) { background-color: #2c3e50; }
        
        /* --- Suggested Cost Box --- */
        .suggested-cost-box {
            text-align: center;
            background-color: #f39c12; 
            color: white;
            padding: 8px 15px;
            border-radius: 5px;
            margin-bottom: 12px;
            position: relative;
        }

        .suggested-cost-box.minimum-warning {
            background-color: #e74c3c;
            animation: pulse-warning 2s infinite;
        }

        @keyframes pulse-warning {
            0% { background-color: #e74c3c; }
            50% { background-color: #f39c12; }
            100% { background-color: #e74c3c; }
        }

        .minimum-cost-warning {
            font-size: 0.8em;
            color: #ffeb3b;
            margin-top: 5px;
            font-weight: bold;
        }

        .suggested-cost-box p {
            margin: 0 0 5px 0;
            font-size: 0.9em;
        }

        .cost-value {
            font-size: 2em;
            font-weight: 900;
            line-height: 1;
        }
        
        /* --- Trade History Table --- */
        .trade-history-table table {
            width: 100%;
            border-collapse: collapse;
        }

        .trade-history-table th, .trade-history-table td {
            border: 1px solid #eee;
            padding: 10px;
            text-align: center;
            font-size: 0.9em;
        }

        .trade-history-table th {
            background-color: #f8f9fa;
        }

        .win { color: #28a745; font-weight: bold; }
        .loss { color: #dc3545; font-weight: bold; }
        .start { color: #007bff; font-weight: bold; }

        /* --- Status Panel Styling --- */
        .status-box {
            padding: 15px;
            border-radius: 6px;
        }

        .status-session {
            background-color: #34495e; 
            text-align: center;
        }
        
        .status-session p {
            font-weight: 300;
            color: #bdc3c7;
            margin-bottom: 10px;
        }

        .status-header-line {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .status-label {
            font-size: 1.1em;
            font-weight: 700;
            padding: 5px 10px;
            border-radius: 4px;
        }

        .halted, .idle {
            background-color: #e74c3c; 
            color: white;
        }

        .started {
            background-color: #2ecc71; 
            color: white;
        }

        .capital-after-display {
            font-size: 1.8em;
            font-weight: 900;
            color: #3498db; 
        }

        .session-counters {
            font-size: 1.2em;
            font-weight: 600;
        }
        
        .session-counters span:first-child {
            background: #f39c12; 
            color: white;
            padding: 2px 6px;
            border-radius: 3px;
        }

        /* --- Profit & Streak Boxes --- */
        .status-profit, .status-streak {
            text-align: center;
            background-color: #34495e;
            border-bottom: 3px solid #f39c12; 
            color: white;
        }
        
        .status-profit p, .status-streak p {
            margin: 0;
            font-weight: 300;
            font-size: 0.9em;
            color: #bdc3c7;
        }
        
        .status-profit span, .status-streak span {
            display: block;
            font-size: 1.6em;
            font-weight: 700;
            color: #2ecc71; 
        }

        /* --- Risk Monitoring --- */
        .risk-monitoring {
            background-color: #34495e;
            color: white;
            padding: 15px;
            border-radius: 6px;
        }
        
        .risk-monitoring p {
            text-align: center;
            font-weight: 600;
            color: #e74c3c; 
            margin-bottom: 10px;
        }

        .risk-values {
            display: flex;
            justify-content: space-around;
        }

        .risk-item {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .risk-item label {
            color: #bdc3c7;
            font-size: 0.85em;
            margin-bottom: 2px;
        }

        .risk-item span {
            font-weight: bold;
            font-size: 1.2em;
            color: #e67e22; 
        }

        .session-halt-log {
            background-color: #34495e;
            border: 1px solid #e74c3c;
            padding: 10px;
            font-size: 0.9em;
            color: #f8d7da;
            max-height: 150px;
            overflow-y: auto;
            border-radius: 5px;
        }
        .session-halt-log p {
            margin: 2px 0;
            border-bottom: 1px dashed #4a637a;
        }
        
        /* --- License Modal Styles --- */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85); 
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000; 
        }

        .modal-content {
            background: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.5);
            width: 90%;
            max-width: 450px;
            text-align: center;
        }

        .modal-content h2 {
            margin-top: 0;
            color: #007bff;
        }
        
        .modal-content input[type="text"] {
            text-transform: uppercase;
        }
        
        /* Flashing error for cooldown/limit */
        .flash-error {
            animation: flash 1s infinite alternate;
        }
        @keyframes flash {
            from { background-color: #e74c3c; opacity: 1; }
            to { background-color: #f39c12; opacity: 0.7; }
        }
    </style>
</head>
<body>
    
    <div id="license-modal" class="modal-overlay">
        <div class="modal-content">
            <h2 id="modal-tier-title">Activate Pro Tier</h2>
            <p>Please enter your unique **License Key** below to activate this tier.</p>
            <input type="text" id="license-key-input" placeholder="LICENSE-KEY">
            <div class="modal-buttons">
                <button id="activate-license-btn" class="btn btn-primary">Activate</button>
                <button id="cancel-license-btn" class="btn btn-secondary">Cancel</button>
            </div>
        </div>
    </div>

    <div class="tracker-container">
        <div class="main-panel">
            <h1>ASTRONuri Trade Tracker</h1>

            <fieldset class="section-box">
                <legend>1. SESSION & RISK PARAMETERS</legend>
                <div class="input-group-row">
                    <label for="country">COUNTRY :</label>
                    <select id="country">
                        <option value="PHP">PHP</option>
                        <option value="USD">USD</option>
                    </select>
                </div>

                <div class="input-group-row compact">
                    <div class="input-field compact">
                        <label for="subscription-tier">Subscription Tier</label>
                        <select id="subscription-tier">
                            <option value="Free">Free</option>
                            <option value="Pro">Pro</option>
                            <option value="Unlimited">Unlimited</option>
                        </select>
                    </div>
                    <div class="input-field compact">
                        <label for="initial-capital">Initial Capital</label>
                        <input type="number" id="initial-capital" value="300" min="100" class="session-parameter">
                    </div>
                    <div class="input-field compact">
                        <label for="target-profit">Target Profit</label>
                        <input type="number" id="target-profit" value="100" min="1" class="session-parameter">
                    </div>
                    <div class="input-field compact">
                        <label for="max-daily-loss">Max Daily Loss (%)</label>
                        <input type="number" id="max-daily-loss" value="50" min="1" max="100" class="session-parameter">
                    </div>
                    <div class="input-field compact">
                        <label for="max-drawdown">Max Drawdown</label>
                        <input type="number" id="max-drawdown" value="160" min="1" class="session-parameter">
                    </div>
                </div>

                <div class="input-group-row buttons">
                    <button id="soft-reset" class="btn btn-secondary">SOFT RESET</button>
                    <button id="start-session" class="btn btn-primary">START SESSION</button>
                    <button id="data-reset" class="btn btn-danger">DATA RESET</button>
                </div>
            </fieldset>

            <fieldset class="section-box">
                <legend>2. TRADE DETAILS</legend>
                <div class="input-group-row trade-details-inputs">
                    <div class="input-field">
                        <label for="payout">Payout (%)</label>
                        <input type="number" id="payout" value="92" min="1" max="100">
                    </div>
                    <div class="input-field">
                        <label for="win-rate">Win Rate (%)</label>
                        <input type="number" id="win-rate" value="60" min="1" max="100">
                    </div>
                    <div class="input-field">
                        <label>Trade Cost Control</label>
                        <div class="checkbox-group">
                            <label>
                                <input type="radio" name="cost-type" id="default-radio" checked> Default (Calculated)
                            </label>
                            <label>
                                <input type="radio" name="cost-type" id="manual-radio"> Manual
                            </label>
                            <label>
                                <input type="radio" name="cost-type" id="capital-percentage-radio"> %Capital
                            </label>
                            <input type="number" id="manual-cost-value" value="2" min="1">
                            <span id="cost-unit">%</span> 
                        </div>
                    </div>
                </div>
                
                <div class="suggested-cost-box" id="suggested-cost-box">
                    <p>SUGGESTED NEXT TRADE COST:</p>
                    <div id="next-trade-cost" class="cost-value">0.00</div>
                    <div id="minimum-cost-warning" class="minimum-cost-warning" style="display: none;"></div>
                </div>

                <div class="input-group-row two-cols">
                    <button id="log-win" class="btn btn-success" disabled>LOG WIN</button>
                    <button id="log-loss" class="btn btn-error" disabled>LOG LOSS</button>
                </div>
            </fieldset>

            <fieldset class="section-box">
                <legend>3. TRADE HISTORY</legend>
                <div class="trade-history-table">
                    <table>
                        <thead>
                            <tr>
                                <th>#</th>
                                <th>Cost</th>
                                <th>Result (P&L)</th>
                                <th>Capital After</th>
                                <th>Next Trade</th>
                            </tr>
                        </thead>
                        <tbody id="trade-history-body">
                            </tbody>
                    </table>
                </div>
            </fieldset>
        </div>

        <div class="status-panel">
            <div class="status-box status-session">
                <p>🚀 SESSION STATUS (<span id="session-tier-label">Free</span>)</p>
                <div class="status-header-line">
                    <div id="session-halt-status" class="status-label idle">IDLE</div>
                    <div class="capital-after-display" id="capital-after-top">300.00</div>
                    <div class="session-counters">
                        <span id="session-count">0</span> /
                        <span id="session-max-count">3</span> SESSIONS
                    </div>
                </div>
            </div>
            
            <div class="status-box status-profit">
                <p>CUMULATIVE PROFIT / LOSS</p>
                <span id="current-profit-display">Ph 0.00</span>
            </div>

            <div class="status-box status-streak">
                <p>WINNING STREAK / ACCURACY</p>
                <span id="winning-streak-display">0 WINS (0.00% / 0/0)</span>
            </div>

            <div class="status-box risk-monitoring">
                <p>⚠️ RISK MONITORING</p>
                <div class="risk-values">
                    <div class="risk-item">
                        <label>Max Loss Left</label>
                        <span id="loss-left-display">150.00</span>
                    </div>
                    <div class="risk-item">
                        <label>Max Drawdown</label>
                        <span id="drawdown-display">0.00</span>
                    </div>
                </div>
            </div>
            
            <button id="logout-license-btn" class="btn btn-full btn-danger" style="display: none;">🔑 LOG OUT LICENSE</button>

            <button id="download-history" class="btn btn-full btn-success">⬇️ DOWNLOAD SESSION HISTORY</button>
            <button id="session-halt-history-btn" class="btn btn-full btn-dark">SESSION HALT LOG</button>

            <div class="session-halt-log" id="session-halt-log-box">
                <p>No halts recorded.</p>
            </div>
        </div>
    </div>
    
    <script>
        // Cloudflare Worker URL - UPDATE THIS WITH YOUR ACTUAL WORKER URL
        const CLOUDFLARE_WORKER_URL = 'https://ancient-cell-9c08.paanobaga.workers.dev';

        let licenseResolver = null;
        let previousTier = 'Free';

        /**
         * Checks the license key for a selected tier via Cloudflare Worker.
         * @param {string} tier - The tier to activate ('Pro' or 'Unlimited').
         * @returns {Promise<boolean>} Resolves true if licensed, false otherwise.
         */
        async function checkLicense(tier) {
            if (tier === 'Free') {
                return true;
            }
            
            // Check if history clear is required before proceeding with login attempt
            if (tier !== previousTier && tierDataStore[previousTier].tradeHistory.length > 0) {
                 const currentDataTier = previousTier === 'Free' ? 'Free Tier' : `${previousTier} Tier`;
                 const warning = `WARNING: Logging into the **${tier} Tier** will clear all current ${currentDataTier} trade history and session logs. Please download your data first if you wish to keep it. Do you wish to continue?`;
                 if (!confirm(warning)) {
                     // User canceled the login/clear process
                     subscriptionTierSelect.value = previousTier;
                     updateUI();
                     return false;
                 }
                 // User confirmed, clear data before showing login
                 clearTierData(previousTier, false);
            }

            const modal = document.getElementById('license-modal');
            const title = document.getElementById('modal-tier-title');
            const input = document.getElementById('license-key-input');
            
            title.textContent = `Activate ${tier} Tier`;
            input.value = '';
            
            modal.style.display = 'flex';

            return new Promise((resolve) => {
                licenseResolver = resolve;
            });
        }
        
        async function handleLicenseActivation() {
            const currentTier = subscriptionTierSelect.value;
            const input = document.getElementById('license-key-input');
            const modal = document.getElementById('license-modal');
            
            const enteredKey = input.value.trim().toUpperCase();

            if (!enteredKey) {
                alert('Please enter a license key');
                return;
            }

            try {
                // Call Cloudflare Worker for license verification
                const response = await fetch(CLOUDFLARE_WORKER_URL, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        tier: currentTier,
                        licenseKey: enteredKey
                    })
                });

                const result = await response.json();

                if (result.success) {
                    alert(`License verified for ${currentTier} Tier!`);
                    modal.style.display = 'none';
                    tier = currentTier;
                    previousTier = currentTier;
                    
                    loadTierPersistentData(tier);
                    setMaxSessionsPerDay();
                    if (licenseResolver) licenseResolver(true);
                } else {
                    alert(`Invalid license key for ${currentTier} Tier. Please try again.`);
                    input.value = '';
                }
            } catch (error) {
                console.error('License verification failed:', error);
                alert('License verification failed. Please check your connection and try again.');
            }
            
            updateUI();
        }

        function handleLicenseCancel() {
            const modal = document.getElementById('license-modal');
            alert(`License check canceled. Reverting to ${previousTier} Tier.`);
            modal.style.display = 'none';
            
            subscriptionTierSelect.value = previousTier;
            tier = previousTier;
            loadTierPersistentData(tier);
            setMaxSessionsPerDay();
            if (licenseResolver) licenseResolver(false);
            updateUI();
        }

        // --- GLOBAL STATE VARIABLES (Shared UI/Session Params) ---
        
        let sessionInitialCapital = 300; 
        let sessionTargetProfit = 100;
        let sessionMaxDailyLossPercent = 50;
        let sessionMaxDrawdown = 160;
        
        // Dynamic variables now hold the *current* data, which is loaded/saved from tierDataStore[tier]
        let currentCapital = 300;
        let currentProfit = 0;
        let maxCapital = 300; 
        let tradeCount = 0;
        let accumulatedLoss = 0; 
        let winningStreak = 0;
        let totalTrades = 0;
        let totalWins = 0;
        
        let sessionStatus = 'IDLE'; 
        let tier = 'Free';
        
        let baseTradeCost = 0; 
        let maxSessionsPerDay = 3; 

        // FIX V15.0: Encapsulated persistent tier data
        let tierDataStore = {
             'Free': { sessionCount: 0, nextActivationTime: 0, tradeHistory: [], haltHistory: [] },
             'Pro': { sessionCount: 0, nextActivationTime: 0, tradeHistory: [], haltHistory: [] },
             'Unlimited': { sessionCount: 0, nextActivationTime: 0, tradeHistory: [], haltHistory: [] }
        };
        
        let tradeHistory = [];
        let haltHistory = [];

        // --- UI Caching ---
        const nextTradeCostDisplay = document.getElementById('next-trade-cost');
        const tradeHistoryBody = document.getElementById('trade-history-body');
        const countrySelect = document.getElementById('country');
        const defaultRadio = document.getElementById('default-radio');
        const manualRadio = document.getElementById('manual-radio');
        const capitalPercentageRadio = document.getElementById('capital-percentage-radio');
        const manualCostValueInput = document.getElementById('manual-cost-value');
        const startSessionBtn = document.getElementById('start-session');
        const logWinBtn = document.getElementById('log-win');
        const logLossBtn = document.getElementById('log-loss');
        const subscriptionTierSelect = document.getElementById('subscription-tier');
        const initialCapitalInput = document.getElementById('initial-capital');
        const targetProfitInput = document.getElementById('target-profit');
        const payoutInput = document.getElementById('payout');
        const winRateInput = document.getElementById('win-rate');
        const costUnitSpan = document.getElementById('cost-unit');
        const downloadHistoryBtn = document.getElementById('download-history');
        const sessionParameterInputs = document.querySelectorAll('.session-parameter');
        const logoutLicenseBtn = document.getElementById('logout-license-btn');
        const softResetBtn = document.getElementById('soft-reset');
        const dataResetBtn = document.getElementById('data-reset');
        const suggestedCostBox = document.getElementById('suggested-cost-box');
        const minimumCostWarning = document.getElementById('minimum-cost-warning');
        
        const LOCAL_STORAGE_KEY = 'ASTRONuriTradeTrackerState';
        const TIER_DATA_STORE_KEY = 'ASTRONuriTierDataStore';

        // --- Local Storage Integration ---

        function setMaxSessionsPerDay(selectedTier = tier) {
            if (selectedTier === 'Pro') maxSessionsPerDay = 10;
            else if (selectedTier === 'Unlimited') maxSessionsPerDay = Infinity;
            else maxSessionsPerDay = 3; 
        }

        function saveTierPersistentData(currentTier = tier) {
            if (!tierDataStore[currentTier]) {
                tierDataStore[currentTier] = { sessionCount: 0, nextActivationTime: 0, tradeHistory: [], haltHistory: [] };
            }
            
            tierDataStore[currentTier].tradeHistory = tradeHistory;
            tierDataStore[currentTier].haltHistory = haltHistory;
        }

        function loadTierPersistentData(currentTier = tier) {
            const data = tierDataStore[currentTier];
            
            tradeHistory = data.tradeHistory || [];
            haltHistory = data.haltHistory || [];
            
            let lastTrade = tradeHistory.length > 0 ? tradeHistory[tradeHistory.length - 1] : null;
            
            if (lastTrade && lastTrade.result !== 'START') {
                 currentCapital = lastTrade.capitalAfter;
            } else {
                 currentCapital = parseFloat(initialCapitalInput.value);
            }

            maxCapital = currentCapital;

            tradeCount = tradeHistory.length > 0 ? tradeHistory[tradeHistory.length - 1].id : 0;
            totalTrades = tradeHistory.filter(t => t.result !== 'START').length;
            totalWins = tradeHistory.filter(t => t.result === 'Win').length;
            currentProfit = tradeHistory.filter(t => t.result !== 'START').reduce((sum, trade) => sum + trade.pnl, 0);

            accumulatedLoss = 0;
            winningStreak = 0;
            sessionStatus = 'IDLE';

            setMaxSessionsPerDay(currentTier);
        }

        function saveState() {
            saveTierPersistentData(tier);

            const globalState = {
                sessionInitialCapital, 
                sessionTargetProfit,
                sessionMaxDailyLossPercent,
                sessionMaxDrawdown,
                tier,
                previousTier,
                initialCapitalInput: parseFloat(initialCapitalInput.value),
                targetProfitInput: parseFloat(targetProfitInput.value),
                maxDailyLossPercentInput: parseFloat(document.getElementById('max-daily-loss').value),
                maxDrawdownInput: parseFloat(document.getElementById('max-drawdown').value),
                payout: parseFloat(payoutInput.value),
                winRate: parseFloat(winRateInput.value),
                costControlType: document.querySelector('input[name="cost-type"]:checked').id,
                manualCostValue: parseFloat(manualCostValueInput.value),
                country: countrySelect.value,
                subscriptionTier: subscriptionTierSelect.value
            };

            try {
                localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(globalState));
                localStorage.setItem(TIER_DATA_STORE_KEY, JSON.stringify(tierDataStore));
            } catch (e) {
                console.error("Error saving to Local Storage", e);
            }
        }

        function loadState() {
            try {
                const storedTierData = localStorage.getItem(TIER_DATA_STORE_KEY);
                if (storedTierData) {
                    tierDataStore = JSON.parse(storedTierData);
                }
                
                ['Free', 'Pro', 'Unlimited'].forEach(t => {
                    if (!tierDataStore[t]) {
                        tierDataStore[t] = { sessionCount: 0, nextActivationTime: 0, tradeHistory: [], haltHistory: [] };
                    }
                });

                const storedGlobalState = localStorage.getItem(LOCAL_STORAGE_KEY);
                if (!storedGlobalState) {
                    loadTierPersistentData('Free');
                    return;
                }

                const state = JSON.parse(storedGlobalState);
                
                sessionInitialCapital = state.sessionInitialCapital || 300;
                sessionTargetProfit = state.sessionTargetProfit || 100;
                sessionMaxDailyLossPercent = state.sessionMaxDailyLossPercent || 50;
                sessionMaxDrawdown = state.sessionMaxDrawdown || 160;

                tier = state.tier || 'Free';
                previousTier = state.previousTier || 'Free';
                
                initialCapitalInput.value = state.initialCapitalInput || 300;
                targetProfitInput.value = state.targetProfitInput || 100;
                document.getElementById('max-daily-loss').value = state.maxDailyLossPercentInput || 50;
                document.getElementById('max-drawdown').value = state.maxDrawdownInput || 160;
                payoutInput.value = state.payout || 92;
                winRateInput.value = state.winRate || 60;
                manualCostValueInput.value = state.manualCostValue || 2;
                countrySelect.value = state.country || 'PHP';
                subscriptionTierSelect.value = state.subscriptionTier || 'Free';
                
                const costRadio = document.getElementById(state.costControlType || 'default-radio');
                if (costRadio) costRadio.checked = true;

                loadTierPersistentData(tier);

            } catch (e) {
                console.error("Error loading from Local Storage. Starting clean.", e);
                localStorage.removeItem(LOCAL_STORAGE_KEY);
                localStorage.removeItem(TIER_DATA_STORE_KEY);
                loadTierPersistentData('Free');
                init();
            }
        }

        // --- Core Calculation Functions ---
        
        function calculateBaseTradeCost() {
            const T = parseFloat(targetProfitInput.value) || 1;
            const P = parseFloat(payoutInput.value) / 100 || 0.01;
            const W = parseFloat(winRateInput.value) / 100 || 0.01;
            
            const denominator = P * W * 10;
            
            if (denominator < 0.01) {
                return sessionInitialCapital * 0.01;
            }

            const calculatedCost = T / denominator;
            
            return calculatedCost;
        }

        function calculateRecoveryCost() {
            const PayoutDecimal = parseFloat(payoutInput.value) / 100 || 0.01;
            const currentBaseTradeCost = calculateBaseTradeCost();
            const baseTradeProfit = currentBaseTradeCost * PayoutDecimal; 
            const requiredGrossProfit = accumulatedLoss + baseTradeProfit;
            
            if (PayoutDecimal < 0.01) return accumulatedLoss + currentBaseTradeCost;

            const nextCost = requiredGrossProfit / PayoutDecimal;
            return Math.max(currentBaseTradeCost, nextCost);
        }

        function calculateNextTradeCost() {
            const manualValue = parseFloat(manualCostValueInput.value) || 0;
            let calculatedCost = 0;
            
            if (manualRadio.checked) {
                calculatedCost = manualValue; 
            } else if (capitalPercentageRadio.checked) {
                const percent = manualValue / 100;
                calculatedCost = currentCapital * percent; 
            } else if (accumulatedLoss > 0) {
                calculatedCost = calculateRecoveryCost();
            } else {
                calculatedCost = baseTradeCost;
            }
            
            const minCost = countrySelect.value === 'PHP' ? 50 : 1;
            return Math.max(calculatedCost, minCost);
        }
        
        // --- Log Functions ---

        function logWin() {
            if (sessionStatus !== 'STARTED') return;
            
            const tradeCost = calculateNextTradeCost(); 
            const PayoutDecimal = parseFloat(payoutInput.value) / 100;
            const pnl = tradeCost * PayoutDecimal; 

            currentCapital += pnl;
            currentProfit += pnl;
            maxCapital = Math.max(maxCapital, currentCapital);

            if (defaultRadio.checked) {
                accumulatedLoss = 0; 
            }
            
            totalTrades++;
            totalWins++;
            winningStreak++;

            tradeHistory.push({ 
                id: ++tradeCount,
                cost: tradeCost,
                result: 'Win',
                pnl: pnl,
                capitalAfter: currentCapital,
                timestamp: new Date().toISOString()
            });
            
            checkHaltConditions();
            updateUI();
        }

        function logLoss() {
            if (sessionStatus !== 'STARTED') return;
            
            const tradeCost = calculateNextTradeCost(); 
            const loss = -tradeCost; 

            currentCapital += loss;
            currentProfit += loss;
            
            if (defaultRadio.checked) {
                accumulatedLoss += tradeCost; 
            }
            
            totalTrades++;
            winningStreak = 0;
            
            tradeHistory.push({ 
                id: ++tradeCount,
                cost: tradeCost,
                result: 'Loss',
                pnl: loss,
                capitalAfter: currentCapital,
                timestamp: new Date().toISOString()
            });
            
            checkHaltConditions();
            updateUI();
        }
        
        // --- UI/Data Functions ---

        function renderTradeHistory() {
            tradeHistoryBody.innerHTML = '';
            
            const historyToRender = tierDataStore[tier].tradeHistory;

            for (const trade of historyToRender) {
                const row = tradeHistoryBody.insertRow(0);
                
                let rowNextTradeCost = '---';
                
                const nextTrade = historyToRender.find(t => t.id === trade.id + 1);
                
                if (nextTrade) {
                    rowNextTradeCost = nextTrade.cost.toFixed(2);
                } else if (trade.id === tradeCount && trade.result !== 'START') { 
                    rowNextTradeCost = calculateNextTradeCost().toFixed(2);
                }
                
                const resultClass = trade.result.toLowerCase();
                const pnlDisplay = trade.result === 'START' ? '0.00' : `${trade.pnl > 0 ? '+' : ''}${trade.pnl.toFixed(2)}`;

                row.innerHTML = `
                    <td>${trade.id === 0 ? 'START' : trade.id}</td>
                    <td>${trade.cost.toFixed(2)}</td>
                    <td class="${resultClass}">${trade.result} (${pnlDisplay})</td>
                    <td>${trade.capitalAfter.toFixed(2)}</td>
                    <td>${rowNextTradeCost}</td>
                `;
            }
        }
        
        function isTierInCooldown(currentTier = tier) {
            const now = Date.now();
            const nextActivationTime = tierDataStore[currentTier].nextActivationTime;
            return now < nextActivationTime;
        }

        function getTierCooldownRemaining(currentTier = tier) {
            const now = Date.now();
            const nextActivationTime = tierDataStore[currentTier].nextActivationTime;
            return Math.max(0, nextActivationTime - now);
        }

        function updateUI() {
            baseTradeCost = calculateBaseTradeCost();
            
            const sessionStatusDisplay = document.getElementById('session-halt-status');
            const capitalAfterTopDisplay = document.getElementById('capital-after-top');
            const haltLogBox = document.getElementById('session-halt-log-box');
            
            const currencySymbol = countrySelect.value === 'PHP' ? 'Ph' : '$';
            
            const now = Date.now();
            let isCurrentTierHalted = isTierInCooldown(tier);
            
            if (isCurrentTierHalted && now >= tierDataStore[tier].nextActivationTime) {
                tierDataStore[tier].nextActivationTime = 0;
                isCurrentTierHalted = false;
                sessionStatus = 'IDLE';
                tierDataStore[tier].haltHistory.push(`Severe Halt Cooldown Expired for ${tier} Tier. Session ready.`);
            }

            sessionStatusDisplay.textContent = sessionStatus;
            sessionStatusDisplay.className = `status-label ${sessionStatus.toLowerCase()}`;
            
            const canStartSession = sessionStatus !== 'STARTED' && !isCurrentTierHalted;
            const isSessionStarted = sessionStatus === 'STARTED';
            
            startSessionBtn.disabled = !canStartSession;
            logWinBtn.disabled = !isSessionStarted;
            logLossBtn.disabled = !isSessionStarted;
            
            sessionParameterInputs.forEach(input => {
                input.disabled = isSessionStarted;
            });
            
            softResetBtn.disabled = isSessionStarted;
            dataResetBtn.disabled = isSessionStarted;

            downloadHistoryBtn.disabled = (tier === 'Free');

            if (tier !== 'Free') {
                logoutLicenseBtn.style.display = 'block';
            } else {
                 logoutLicenseBtn.style.display = 'none';
            }

            if (isCurrentTierHalted) {
                 startSessionBtn.classList.add('flash-error');
                 haltLogBox.classList.add('flash-error');
                 
                 const remainingTime = getTierCooldownRemaining(tier);
                 const hours = Math.floor(remainingTime / (1000 * 60 * 60));
                 const minutes = Math.floor((remainingTime % (1000 * 60 * 60)) / (1000 * 60));
                 startSessionBtn.textContent = `COOLDOWN: ${hours}h ${minutes}m`;
            } else {
                 startSessionBtn.classList.remove('flash-error');
                 haltLogBox.classList.remove('flash-error');
                 startSessionBtn.textContent = `START SESSION`;
            }

            if (capitalPercentageRadio.checked) {
                costUnitSpan.textContent = '%';
                manualCostValueInput.disabled = false;
            } else if (manualRadio.checked) {
                costUnitSpan.textContent = currencySymbol;
                manualCostValueInput.disabled = false;
            } else {
                costUnitSpan.textContent = ''; 
                manualCostValueInput.disabled = true;
            }
            
            const nextCost = calculateNextTradeCost();
            const minCost = countrySelect.value === 'PHP' ? 50 : 1;
            
            let rawCost = 0;
            if (manualRadio.checked) {
                rawCost = parseFloat(manualCostValueInput.value) || 0;
            } else if (capitalPercentageRadio.checked) {
                const percent = parseFloat(manualCostValueInput.value) / 100 || 0;
                rawCost = currentCapital * percent;
            } else if (accumulatedLoss > 0) {
                rawCost = calculateRecoveryCost();
            } else {
                rawCost = baseTradeCost;
            }
            
            if (rawCost < minCost && nextCost === minCost) {
                suggestedCostBox.classList.add('minimum-warning');
                minimumCostWarning.style.display = 'block';
                minimumCostWarning.textContent = `MINIMUM: ${currencySymbol} ${minCost.toFixed(2)}`;
            } else {
                suggestedCostBox.classList.remove('minimum-warning');
                minimumCostWarning.style.display = 'none';
            }
            
            capitalAfterTopDisplay.textContent = currentCapital.toFixed(2);
            document.getElementById('session-count').textContent = tierDataStore[tier].sessionCount;
            document.getElementById('session-max-count').textContent = maxSessionsPerDay === Infinity ? '∞' : maxSessionsPerDay;
            document.getElementById('session-tier-label').textContent = tier;
            
            nextTradeCostDisplay.textContent = nextCost.toFixed(2);
            
            document.getElementById('current-profit-display').innerHTML = `${currencySymbol} ${currentProfit.toFixed(2)}`;
            
            document.getElementById('loss-left-display').textContent = calculateLossLeft().toFixed(2);
            document.getElementById('drawdown-display').textContent = calculateDrawdown().toFixed(2);

            const winRate = totalTrades > 0 ? (totalWins / totalTrades) * 100 : 0.00;
            document.getElementById('winning-streak-display').innerHTML = `**${winningStreak} WINS** (${winRate.toFixed(2)}% / ${totalWins}/${totalTrades})`;
            
            renderTradeHistory();
            renderHaltHistory();
            saveState();
        }

        function calculateLossLeft() {
            const maxLossAmount = sessionInitialCapital * (sessionMaxDailyLossPercent / 100);
            const totalLoss = sessionInitialCapital - currentCapital;
            return Math.max(0, maxLossAmount - totalLoss);
        }

        function calculateDrawdown() {
            return Math.max(0, maxCapital - currentCapital);
        }
        
        function checkHaltConditions() {
            let currency = countrySelect.value;
            let shouldHalt = false;
            let criticalHalt = false;
            let reason = '';
            
            if (currentProfit >= sessionTargetProfit) {
                reason = `Target Profit Reached: ${currency} ${currentProfit.toFixed(2)}`;
                shouldHalt = true;
            }

            if (calculateLossLeft() <= 0.01 && !shouldHalt) {
                const totalLoss = sessionInitialCapital - currentCapital;
                reason = `Max Daily Loss Reached (${sessionMaxDailyLossPercent}%) - Total loss: ${currency} ${totalLoss.toFixed(2)}`;
                shouldHalt = true;
            }

            if (calculateDrawdown() >= sessionMaxDrawdown && !shouldHalt) {
                reason = `Max Drawdown Reached (${calculateDrawdown().toFixed(2)})`;
                shouldHalt = true;
            }
            
            const capitalLossThreshold = sessionInitialCapital * 0.20;
            if (currentCapital <= capitalLossThreshold) {
                reason = `CRITICAL HALT: Capital dropped below 20% threshold (${currency} ${currentCapital.toFixed(2)}). Next activation in 12 hours.`;
                shouldHalt = true; 
                criticalHalt = true; 
            }
            
            if(shouldHalt && sessionStatus === 'STARTED') {
                sessionStatus = 'HALTED';
                
                const currentSessionCount = tierDataStore[tier].sessionCount;
                tierDataStore[tier].haltHistory.push(`Session ${currentSessionCount} Halt: ${reason}`);
                
                if (criticalHalt) {
                    tierDataStore[tier].nextActivationTime = Date.now() + (12 * 60 * 60 * 1000); 
                    tierDataStore[tier].sessionCount = 0; 
                    clearTierData(tier, false);
                    alert("CRITICAL HALT: All history cleared and a 12-hour cooldown has been imposed due to capital depletion.");
                }
                
                saveState();
            }
        }

        function renderHaltHistory() {
            const haltLogBox = document.getElementById('session-halt-log-box');
            const historyToRender = tierDataStore[tier].haltHistory;

            haltLogBox.innerHTML = '';
            if (historyToRender.length === 0) {
                 haltLogBox.innerHTML = '<p>No halts recorded.</p>';
                 return;
            }
            for(let i = historyToRender.length - 1; i >= 0; i--) {
                haltLogBox.innerHTML += `<p>• ${historyToRender[i]}</p>`;
            }
        }
        
        function clearTierData(targetTier, fullReset = false) {
            tierDataStore[targetTier].tradeHistory = []; 
            tierDataStore[targetTier].haltHistory = []; 
            
            if (targetTier === tier) {
                 tradeCount = 0;
                 totalTrades = 0;
                 totalWins = 0;
                 accumulatedLoss = 0;
                 winningStreak = 0;
                 currentProfit = 0;
                 sessionStatus = 'IDLE';
                 currentCapital = parseFloat(initialCapitalInput.value);
                 maxCapital = currentCapital;
            }
            
            if (fullReset) {
                tierDataStore[targetTier].sessionCount = 0;
                tierDataStore[targetTier].nextActivationTime = 0;
            }
            
            if (targetTier === tier) {
                loadTierPersistentData(tier);
            }

            saveState();
        }

        function imposeTierLimitCooldown() {
            tierDataStore[tier].nextActivationTime = Date.now() + (12 * 60 * 60 * 1000); 
            sessionStatus = 'HALTED';
            
            const currentSessionCount = tierDataStore[tier].sessionCount;
            tierDataStore[tier].haltHistory.push(`Session Limit Reached (${tier} - ${maxSessionsPerDay} sessions). Imposing 12-hour cooldown. **Session count reset to 0.**`);
            
            tierDataStore[tier].sessionCount = 0;
            clearTierData(tier, false);
            
            alert(`Session limit of ${maxSessionsPerDay} reached for ${tier} Tier. A 12-hour cooldown has been imposed.`);
        }

        function softReset() {
            updateUI();
        }
        
        function dataReset() {
            if (!confirm("WARNING: This will erase ALL trade history, halt history, and reset current session for ALL TIERS. Session counts and cooldown timers will be preserved. Are you sure?")) return;
            
            ['Free', 'Pro', 'Unlimited'].forEach(t => {
                tierDataStore[t].tradeHistory = [];
                tierDataStore[t].haltHistory = [];
                
                if (t === 'Unlimited') {
                    tierDataStore[t].sessionCount = 0;
                }
            });
            
            initialCapitalInput.value = 300;
            targetProfitInput.value = 100;
            document.getElementById('max-daily-loss').value = 50;
            document.getElementById('max-drawdown').value = 160;
            payoutInput.value = 92;
            winRateInput.value = 60;
            manualCostValueInput.value = 2; 
            document.getElementById('default-radio').checked = true;
            subscriptionTierSelect.value = 'Free';
            
            tier = 'Free';
            previousTier = 'Free';
            setMaxSessionsPerDay();
            
            loadTierPersistentData('Free');
            
            updateUI();
            saveState();
        }

        function logoutLicense() {
            const loggedOutTier = tier;
            
            if (loggedOutTier === 'Free') return;
            
            if (sessionStatus === 'STARTED') {
                tierDataStore[loggedOutTier].haltHistory.push(`Session ${tierDataStore[loggedOutTier].sessionCount} Halt: License Abandoned during active session. Forced Halt.`);
                sessionStatus = 'HALTED';
                updateUI();
                alert("NOTICE: Your active session has been automatically HALTED to proceed with license logout.");
            }
            
            const warning = `⚠️ DOWNLOAD WARNING: Logging out of the **${loggedOutTier} Tier** will clear all current **${loggedOutTier} Tier** trade history and session logs. You will revert to the Free Tier. **Please download your data first if you wish to keep it. Do you wish to continue and clear all history for ${loggedOutTier}?**`;
            
            if (!confirm(warning)) {
                updateUI();
                return;
            }
            
            const freeSessionCount = tierDataStore['Free'].sessionCount;
            
            clearTierData(loggedOutTier, false);
            
            tier = 'Free';
            previousTier = 'Free';
            subscriptionTierSelect.value = 'Free';
            setMaxSessionsPerDay();
            
            tierDataStore['Free'].sessionCount = freeSessionCount;
            
            loadTierPersistentData('Free');
            
            alert(`License for ${loggedOutTier} successfully logged out. Trade history cleared. Reverting to Free Tier.`);
            updateUI();
        }

        // --- Event Handlers ---

        subscriptionTierSelect.addEventListener('change', async (e) => {
            const newTier = e.target.value;
            
            saveTierPersistentData(tier);

            if (newTier !== 'Free') {
                const licenseSuccess = await checkLicense(newTier);
                if (!licenseSuccess) {
                    e.target.value = previousTier;
                    return;
                }
            } else if (newTier === 'Free' && tier !== 'Free') {
                if (tierDataStore[tier].tradeHistory.length > 0) {
                    const warning = `WARNING: Reverting to the Free Tier will clear all current **${tier} Tier** trade history and session logs. Please download your data first if you wish to keep it. Do you wish to continue?`;
                    if (!confirm(warning)) {
                        e.target.value = tier;
                        updateUI();
                        return;
                    }
                    clearTierData(tier, true);
                }
                
                previousTier = 'Free';
                tier = 'Free';
                
            } else if (newTier === 'Free' && tier === 'Free') {
            }
            
            tier = newTier;
            previousTier = newTier;
            loadTierPersistentData(tier);
            setMaxSessionsPerDay();
            
            updateUI();
        });
        
        document.querySelectorAll('input[type="number"], select').forEach(input => {
            input.addEventListener('input', updateUI);
            input.addEventListener('change', saveState);
        });

        document.querySelectorAll('input[name="cost-type"]').forEach(radio => {
            radio.addEventListener('change', updateUI);
        });
        
        softResetBtn.addEventListener('click', softReset);
        dataResetBtn.addEventListener('click', dataReset);
        
        document.getElementById('activate-license-btn').addEventListener('click', handleLicenseActivation);
        document.getElementById('cancel-license-btn').addEventListener('click', handleLicenseCancel);
        document.getElementById('license-key-input').addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                e.preventDefault();
                handleLicenseActivation();
            }
        });
        
        document.getElementById('download-history').addEventListener('click', downloadTradeHistory);
        logoutLicenseBtn.addEventListener('click', logoutLicense);

        startSessionBtn.addEventListener('click', async () => {
            const selectedTier = subscriptionTierSelect.value;
            
            if (selectedTier !== tier) {
                alert(`Tier mismatch detected. Current active tier is **${tier}**. Please use the subscription tier dropdown to select your active tier.`);
                updateUI();
                return;
            }

            if (isTierInCooldown(tier)) {
                alert(`Session is in severe halt cooldown for the **${tier} Tier**. Wait for the timer to expire.`);
                return;
            }
            
            const currentSessionCount = tierDataStore[tier].sessionCount;
            if (tier !== 'Unlimited' && currentSessionCount >= maxSessionsPerDay) {
                imposeTierLimitCooldown();
                updateUI();
                return;
            }

            sessionInitialCapital = parseFloat(initialCapitalInput.value);
            sessionTargetProfit = parseFloat(targetProfitInput.value);
            sessionMaxDailyLossPercent = parseFloat(document.getElementById('max-daily-loss').value);
            sessionMaxDrawdown = parseFloat(document.getElementById('max-drawdown').value);

            loadTierPersistentData(tier);

            tierDataStore[tier].sessionCount++;
            sessionStatus = 'STARTED';

            const activeTradeHistory = tierDataStore[tier].tradeHistory;
            if (activeTradeHistory.length === 0 || activeTradeHistory[activeTradeHistory.length-1].result !== 'START') {
                 tradeHistory.push({
                    id: 0,
                    cost: 0.00,
                    result: 'START',
                    pnl: 0.00,
                    capitalAfter: currentCapital,
                    timestamp: new Date().toISOString()
                });
                tradeCount = 0;
            }

            updateUI();
        });

        logWinBtn.addEventListener('click', logWin);
        logLossBtn.addEventListener('click', logLoss);
        
        function downloadTradeHistory() {
            if (tier === 'Free') {
                alert("Download is not available in the Free Tier. Please upgrade to Pro or Unlimited.");
                return;
            }
            const historyToDownload = tierDataStore[tier].tradeHistory;

            if (historyToDownload.length <= 1) { 
                alert("Cannot download history. Please log at least one trade.");
                return;
            }

            const header = ["Trade #", "Date/Time", "Cost", "Result", "P&L", "Capital After (Currency)", "Next Cost"];
            
            const tradesForCSV = historyToDownload.filter(trade => trade.result !== 'START');

            const csvRows = tradesForCSV.map(trade => [
                    trade.id,
                    trade.timestamp,
                    trade.cost.toFixed(2),
                    trade.result,
                    trade.pnl.toFixed(2),
                    trade.capitalAfter.toFixed(2),
                    '---'
                ]);

            for(let i = 0; i < csvRows.length; i++) {
                const currentTradeId = csvRows[i][0];
                const nextTrade = historyToDownload.find(t => t.id === currentTradeId + 1);
                
                if (nextTrade) {
                    csvRows[i][6] = nextTrade.cost.toFixed(2);
                } else if (i === csvRows.length - 1) {
                     csvRows[i][6] = calculateNextTradeCost().toFixed(2);
                }
            }

            const csvContent = [
                header.join(","),
                ...csvRows.map(row => row.join(","))
            ].join("\n");

            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            
            const dateStr = new Date().toISOString().slice(0, 10);
            link.setAttribute('href', url);
            link.setAttribute('download', `ASTRONuri_Trade_Log_${dateStr}_${tier}.csv`);
            
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            alert(`Trade history downloaded as ASTRONuri_Trade_Log_${dateStr}_${tier}.csv`);
        }

        // --- Initialization ---
        function init() {
            loadState();
            setMaxSessionsPerDay(tier);
            
            sessionInitialCapital = parseFloat(initialCapitalInput.value);
            
            updateUI();
            
            setInterval(updateUI, 60000);
        }

        init();
    </script>
</body>
</html>

