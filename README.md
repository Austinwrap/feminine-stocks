<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Feminine Stock Exchange & Options Simulator</title>
  <style>
    /* Base Styles – Soft background with a cute, sleek vibe */
    body {
      background: linear-gradient(135deg, #ffe6f2, #fff0f5);
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
      color: #333;
    }
    /* Neon Ticker Styles (top and bottom) with flashing neon effect */
    #ticker-top, #ticker-bottom {
      background: linear-gradient(45deg, #000, #330033);
      border: 2px solid #ff66cc;
      box-shadow: 0 0 10px #ff66cc;
      overflow: hidden;
      padding: 5px 0;
    }
    .ticker-content {
      white-space: nowrap;
      display: inline-block;
      padding-left: 100%;
      animation: tickerAnimation 15s linear infinite;
      font-size: 1.2em;
    }
    /* Each company span will flash with a neon effect */
    .ticker-content span {
      margin-right: 20px;
      padding: 0 10px;
      animation: neonFlicker 1.5s infinite alternate;
    }
    @keyframes tickerAnimation {
      from { transform: translateX(0); }
      to { transform: translateX(-100%); }
    }
    @keyframes neonFlicker {
      from { text-shadow: 0 0 5px currentColor; }
      to { text-shadow: 0 0 20px currentColor; }
    }
    /* Section Container – common styling for each section */
    .section {
      background: #ffffff;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      margin: 20px 15px;
      padding: 20px;
    }
    h1, h2, h3 {
      text-align: center;
      color: #d63384;
    }
    p {
      text-align: center;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 10px 0;
    }
    table, th, td {
      border: 1px solid #f1c0e8;
    }
    th, td {
      padding: 8px;
      text-align: center;
    }
    form {
      margin: 10px 0;
    }
    label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
      color: #555;
    }
    select, input[type="number"] {
      width: 100%;
      padding: 8px;
      margin: 5px 0;
      border: 1px solid #f1c0e8;
      border-radius: 4px;
      box-sizing: border-box;
    }
    button {
      width: 100%;
      padding: 10px;
      background: #d63384;
      color: #fff;
      border: none;
      border-radius: 4px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 10px;
    }
    button:hover {
      background: #b02c6d;
    }
    .log, .explanation {
      background: #fff5f7;
      border: 1px solid #f1c0e8;
      border-radius: 6px;
      padding: 10px;
      max-height: 200px;
      overflow-y: auto;
      font-size: 14px;
      margin-top: 10px;
    }
    /* Responsive design for mobile devices */
    @media (max-width: 768px) {
      .section { margin: 10px; }
    }
  </style>
</head>
<body>
  <!-- Neon Ticker at Top -->
  <div id="ticker-top">
    <div class="ticker-content" id="tickerTopContent">Loading ticker...</div>
  </div>
  
  <!-- Account Summary Section -->
  <div class="section" id="accountSummary">
    <h2>Account Summary</h2>
    <p>Bank Balance: $<span id="bankBalance">1000000.00</span></p>
    <p>Portfolio Value: $<span id="portfolioValue">0.00</span></p>
    <p>Total Account Value: $<span id="totalValue">1000000.00</span></p>
    <p>Profit/Loss: $<span id="profitLoss">0.00</span></p>
  </div>
  
  <!-- Live Market Section -->
  <div class="section" id="liveMarket">
    <h2>Live Market</h2>
    <table id="liveMarketTable">
      <thead>
        <tr>
          <th>Ticker</th>
          <th>Company</th>
          <th>Price ($)</th>
          <th>Change</th>
          <th>% Change</th>
        </tr>
      </thead>
      <tbody>
        <!-- Live market data will be inserted here -->
      </tbody>
    </table>
  </div>
  
  <!-- Stock Trading Section -->
  <div class="section" id="stockTrading">
    <h2>Stock Trading</h2>
    <form id="stockForm">
      <label for="stockAction">Action:</label>
      <select id="stockAction">
        <option value="buy">Buy Stock</option>
        <option value="sell">Sell Stock</option>
      </select>
      <label for="stockSelect">Select Company:</label>
      <select id="stockSelect">
        <!-- Options will be inserted here -->
      </select>
      <label for="stockShares">Number of Shares:</label>
      <input type="number" id="stockShares" min="1" value="1">
      <button type="button" id="stockTradeButton">Execute Stock Trade</button>
    </form>
    <h3>Your Portfolio</h3>
    <table id="portfolioTable">
      <thead>
        <tr>
          <th>Company</th>
          <th>Shares Owned</th>
          <th>Current Price</th>
          <th>Total Value</th>
        </tr>
      </thead>
      <tbody>
        <!-- Portfolio rows will be inserted here -->
      </tbody>
    </table>
    <div class="log" id="stockLog">
      <p>Stock trade log will appear here.</p>
    </div>
  </div>
  
  <!-- Extra Space before Options Trading Section -->
  <div style="height: 30px;"></div>
  
  <!-- Options Trading Section -->
  <div class="section" id="optionsTrading">
    <h2>Options Trading</h2>
    <form id="optionsForm">
      <label for="optionAction">Action:</label>
      <select id="optionAction">
        <option value="buy_call">Buy Call Option</option>
        <option value="buy_put">Buy Put Option</option>
        <option value="sell_call">Sell Call Option</option>
        <option value="sell_put">Sell Put Option</option>
      </select>
      <label for="optionStockSelect">Select Company:</label>
      <select id="optionStockSelect">
        <!-- Options will be inserted here -->
      </select>
      <label for="optionContracts">Number of Contracts (1 contract = 100 shares):</label>
      <input type="number" id="optionContracts" min="1" value="1">
      <button type="button" id="optionTradeButton">Execute Options Trade</button>
    </form>
    <div class="log" id="optionsLog">
      <p>Options trade log will appear here.</p>
    </div>
  </div>
  
  <!-- Trade Explanation Section -->
  <div class="section" id="tradeExplanation">
    <h2>Trade Explanation</h2>
    <div class="explanation" id="explanation">
      <p>Detailed explanations of your trades will appear here.</p>
    </div>
  </div>
  
  <!-- Neon Ticker at Bottom -->
  <div id="ticker-bottom">
    <div class="ticker-content" id="tickerBottomContent">Loading ticker...</div>
  </div>
  
  <script>
    // ============================================
    // Global Data & Variables
    // ============================================
    let bank = 1000000;
    const startingBank = 1000000;
    const premiumRate = 0.05; // Options premium: 5% per share

    // 25 Feminine companies (Ticker: { name, price, prevPrice })
    const companies = {
      "SEPH": { name: "Sephora", price: 120.00, prevPrice: 120.00 },
      "ULTA": { name: "Ulta Beauty", price: 200.00, prevPrice: 200.00 },
      "VSEC": { name: "Victoria's Secret", price: 80.00, prevPrice: 80.00 },
      "BBBY": { name: "Bed Bath & Beyond", price: 30.00, prevPrice: 30.00 },
      "KATE": { name: "Kate Spade", price: 50.00, prevPrice: 50.00 },
      "GLOS": { name: "Glossier", price: 90.00, prevPrice: 90.00 },
      "LULU": { name: "Lululemon", price: 300.00, prevPrice: 300.00 },
      "TORY": { name: "Tory Burch", price: 110.00, prevPrice: 110.00 },
      "HUDA": { name: "Huda Beauty", price: 75.00, prevPrice: 75.00 },
      "BENF": { name: "Benefit Cosmetics", price: 65.00, prevPrice: 65.00 },
      "FENT": { name: "Fenty Beauty", price: 85.00, prevPrice: 85.00 },
      "REVL": { name: "Revolve", price: 150.00, prevPrice: 150.00 },
      "ANTH": { name: "Anthropologie", price: 95.00, prevPrice: 95.00 },
      "FREE": { name: "Free People", price: 70.00, prevPrice: 70.00 },
      "COAC": { name: "Coach", price: 100.00, prevPrice: 100.00 },
      "MKOR": { name: "Michael Kors", price: 140.00, prevPrice: 140.00 },
      "MJAC": { name: "Marc Jacobs", price: 130.00, prevPrice: 130.00 },
      "ELDR": { name: "Estée Lauder", price: 160.00, prevPrice: 160.00 },
      "CLIN": { name: "Clinique", price: 110.00, prevPrice: 110.00 },
      "MAYB": { name: "Maybelline", price: 45.00, prevPrice: 45.00 },
      "SALY": { name: "Sally Hansen", price: 55.00, prevPrice: 55.00 },
      "TOOF": { name: "Too Faced", price: 95.00, prevPrice: 95.00 },
      "URBN": { name: "Urban Decay", price: 85.00, prevPrice: 85.00 },
      "NYXC": { name: "NYX Cosmetics", price: 40.00, prevPrice: 40.00 },
      "BMIN": { name: "BareMinerals", price: 75.00, prevPrice: 75.00 }
    };

    // Portfolio: track shares owned for each company (initially 0)
    let portfolio = {
      "SEPH": 0, "ULTA": 0, "VSEC": 0, "BBBY": 0, "KATE": 0,
      "GLOS": 0, "LULU": 0, "TORY": 0, "HUDA": 0, "BENF": 0,
      "FENT": 0, "REVL": 0, "ANTH": 0, "FREE": 0, "COAC": 0,
      "MKOR": 0, "MJAC": 0, "ELDR": 0, "CLIN": 0, "MAYB": 0,
      "SALY": 0, "TOOF": 0, "URBN": 0, "NYXC": 0, "BMIN": 0
    };

    // ============================================
    // Ticker & Display Updates
    // ============================================
    // Update the neon ticker with flashing spans that change color based on price movement.
    function updateTicker() {
      let tickerHTML = "";
      for (const symbol in companies) {
        const comp = companies[symbol];
        const change = comp.price - comp.prevPrice;
        let color;
        if (change > 0) {
          color = "lime";
        } else if (change < 0) {
          color = "red";
        } else {
          color = "#ff66cc";
        }
        tickerHTML += `<span style="color:${color};">${symbol} (${comp.name}): $${comp.price.toFixed(2)}</span>`;
      }
      document.getElementById("tickerTopContent").innerHTML = tickerHTML;
      document.getElementById("tickerBottomContent").innerHTML = tickerHTML;
    }
    
    // Animate bank balance changes (rolling effect)
    function animateValue(element, start, end, duration) {
      let startTime = null;
      function animate(currentTime) {
        if (!startTime) startTime = currentTime;
        const progress = currentTime - startTime;
        const value = start + (end - start) * (progress / duration);
        element.innerText = value.toFixed(2);
        if (progress < duration) {
          requestAnimationFrame(animate);
        } else {
          element.innerText = end.toFixed(2);
        }
      }
      requestAnimationFrame(animate);
    }
    function updateBankDisplay(oldBank, newBank) {
      const bankElement = document.getElementById("bankBalance");
      animateValue(bankElement, oldBank, newBank, 500);
      updateAccountSummary();
    }
    
    // Update Account Summary: portfolio value, total account value, profit/loss
    function updateAccountSummary() {
      let portfolioValue = 0;
      for (const symbol in portfolio) {
        portfolioValue += portfolio[symbol] * companies[symbol].price;
      }
      const totalValue = bank + portfolioValue;
      const profitLoss = totalValue - startingBank;
      document.getElementById("portfolioValue").innerText = portfolioValue.toFixed(2);
      document.getElementById("totalValue").innerText = totalValue.toFixed(2);
      document.getElementById("profitLoss").innerText = profitLoss.toFixed(2);
    }
    
    // Update the Live Market table with current prices, change, and percent change.
    function updateLiveMarket() {
      const tbody = document.querySelector("#liveMarketTable tbody");
      tbody.innerHTML = "";
      for (const symbol in companies) {
        const comp = companies[symbol];
        const change = comp.price - comp.prevPrice;
        const percentChange = (change / comp.prevPrice) * 100;
        let changeColor = change >= 0 ? "green" : "red";
        const row = document.createElement("tr");
        row.innerHTML = `<td>${symbol}</td>
                         <td>${comp.name}</td>
                         <td>$${comp.price.toFixed(2)}</td>
                         <td style="color: ${changeColor};">${change >= 0 ? "+" : ""}${change.toFixed(2)}</td>
                         <td style="color: ${changeColor};">${change >= 0 ? "+" : ""}${percentChange.toFixed(2)}%</td>`;
        tbody.appendChild(row);
      }
    }
    
    // Update Portfolio Table
    function updatePortfolioDisplay() {
      const tbody = document.querySelector("#portfolioTable tbody");
      tbody.innerHTML = "";
      for (const symbol in portfolio) {
        const shares = portfolio[symbol];
        const price = companies[symbol].price;
        const totalValue = shares * price;
        if (shares > 0) {
          const row = document.createElement("tr");
          row.innerHTML = `<td>${companies[symbol].name} (${symbol})</td>
                           <td>${shares}</td>
                           <td>$${price.toFixed(2)}</td>
                           <td>$${totalValue.toFixed(2)}</td>`;
          tbody.appendChild(row);
        }
      }
      if (tbody.innerHTML === "") {
        tbody.innerHTML = "<tr><td colspan='4'>No stocks owned yet.</td></tr>";
      }
    }
    
    // Log messages for stock trading
    function logStockMessage(message) {
      const logDiv = document.getElementById("stockLog");
      const p = document.createElement("p");
      p.innerHTML = message;
      logDiv.appendChild(p);
      logDiv.scrollTop = logDiv.scrollHeight;
    }
    
    // Log messages for options trading
    function logOptionsMessage(message) {
      const logDiv = document.getElementById("optionsLog");
      const p = document.createElement("p");
      p.innerHTML = message;
      logDiv.appendChild(p);
      logDiv.scrollTop = logDiv.scrollHeight;
    }
    
    // Update the Trade Explanation sidebar
    function updateExplanation(text) {
      const explanationDiv = document.getElementById("explanation");
      explanationDiv.innerHTML = `<p>${text}</p>`;
    }
    
    // ============================================
    // Simulate Market Price Movements
    // ============================================
    // For the live market, we use smaller fluctuations (±1%)
    function simulatePriceMovement(price) {
      const pctChange = (Math.random() * 0.02) - 0.01;
      const newPrice = price * (1 + pctChange);
      return parseFloat(newPrice.toFixed(2));
    }
    
    // Periodically update market prices every 5 seconds
    function updateMarketPrices() {
      for (const symbol in companies) {
        companies[symbol].prevPrice = companies[symbol].price;
        companies[symbol].price = simulatePriceMovement(companies[symbol].price);
      }
      updateTicker();
      updateLiveMarket();
      updatePortfolioDisplay();
      updateAccountSummary();
    }
    
    // ============================================
    // Populate Dropdown Options
    // ============================================
    function populateStockOptions() {
      const stockSelect = document.getElementById("stockSelect");
      const optionStockSelect = document.getElementById("optionStockSelect");
      stockSelect.innerHTML = "";
      optionStockSelect.innerHTML = "";
      for (const symbol in companies) {
        const option1 = document.createElement("option");
        option1.value = symbol;
        option1.innerText = `${companies[symbol].name} (${symbol})`;
        stockSelect.appendChild(option1);
        const option2 = document.createElement("option");
        option2.value = symbol;
        option2.innerText = `${companies[symbol].name} (${symbol})`;
        optionStockSelect.appendChild(option2);
      }
    }
    
    // ============================================
    // STOCK TRADING HANDLER
    // ============================================
    document.getElementById("stockTradeButton").addEventListener("click", function() {
      const action = document.getElementById("stockAction").value;
      const symbol = document.getElementById("stockSelect").value;
      const shares = parseInt(document.getElementById("stockShares").value);
      if (shares <= 0) {
        alert("Enter a valid number of shares.");
        return;
      }
      const price = companies[symbol].price;
      const totalCost = price * shares;
      let explanation = "";
      let oldBank = bank;
      
      if (action === "buy") {
        if (bank < totalCost) {
          alert("Not enough funds to buy.");
          return;
        }
        bank -= totalCost;
        portfolio[symbol] += shares;
        explanation = `You <strong>bought</strong> ${shares} shares of ${companies[symbol].name} (${symbol}) at $${price.toFixed(2)} each for a total of $${totalCost.toFixed(2)}. This company is known for its fabulous products and trends!`;
        logStockMessage(`Bought ${shares} shares of ${companies[symbol].name} (${symbol}) at $${price.toFixed(2)} each. Total cost: $${totalCost.toFixed(2)}.`);
      } else if (action === "sell") {
        if (portfolio[symbol] < shares) {
          alert("You don't own that many shares to sell.");
          return;
        }
        bank += totalCost;
        portfolio[symbol] -= shares;
        explanation = `You <strong>sold</strong> ${shares} shares of ${companies[symbol].name} (${symbol}) at $${price.toFixed(2)} each, earning $${totalCost.toFixed(2)}. Great job capitalizing on market trends!`;
        logStockMessage(`Sold ${shares} shares of ${companies[symbol].name} (${symbol}) at $${price.toFixed(2)} each. Total gain: $${totalCost.toFixed(2)}.`);
      }
      
      // Simulate a post-trade price movement for the traded stock
      const newPrice = simulatePriceMovement(price);
      companies[symbol].prevPrice = companies[symbol].price;
      companies[symbol].price = newPrice;
      explanation += ` After your trade, the price of ${companies[symbol].name} changed from $${price.toFixed(2)} to $${newPrice.toFixed(2)}.`;
      
      updateBankDisplay(oldBank, bank);
      updatePortfolioDisplay();
      updateExplanation(explanation);
      updateTicker();
    });
    
    // ============================================
    // OPTIONS TRADING HANDLER
    // ============================================
    document.getElementById("optionTradeButton").addEventListener("click", function() {
      const action = document.getElementById("optionAction").value;
      const symbol = document.getElementById("optionStockSelect").value;
      const contracts = parseInt(document.getElementById("optionContracts").value);
      if (contracts <= 0) {
        alert("Enter a valid number of contracts.");
        return;
      }
      
      const currentPrice = companies[symbol].price;
      const strike = currentPrice; // Using current price as the strike
      const premiumPerContract = premiumRate * strike * 100;
      const totalPremium = premiumPerContract * contracts;
      let explanation = "";
      let logMsg = `<strong>Options Trade:</strong> ${action.replace('_', ' ')} on ${companies[symbol].name} (${symbol}) for ${contracts} contract(s).<br>`;
      logMsg += `<em>Strike Price:</em> $${strike.toFixed(2)} | <em>Premium/Contract:</em> $${premiumPerContract.toFixed(2)} | <em>Total Premium:</em> $${totalPremium.toFixed(2)}<br>`;
      let oldBank = bank;
      
      // Process funds for options: buying costs premium; selling collects premium.
      if (action.startsWith("buy")) {
        if (bank < totalPremium) {
          alert("Not enough funds for this options trade.");
          return;
        }
        bank -= totalPremium;
        logMsg += `Premium paid: -$${totalPremium.toFixed(2)}<br>`;
      } else if (action.startsWith("sell")) {
        bank += totalPremium;
        logMsg += `Premium collected: +$${totalPremium.toFixed(2)}<br>`;
      }
      
      // Simulate market movement for the underlying stock
      const prevPrice = companies[symbol].price;
      const newPrice = simulatePriceMovement(prevPrice);
      companies[symbol].prevPrice = prevPrice;
      companies[symbol].price = newPrice;
      const pctChange = ((newPrice - prevPrice) / prevPrice) * 100;
      logMsg += `<em>Market Movement:</em> Price moved from $${prevPrice.toFixed(2)} to $${newPrice.toFixed(2)} (${pctChange.toFixed(2)}%)<br>`;
      
      // Calculate options outcome
      let payoff = 0, cost = 0, profit = 0;
      if (action === "buy_call") {
        const intrinsicValue = Math.max(newPrice - strike, 0);
        payoff = intrinsicValue * 100 * contracts;
        profit = payoff - totalPremium;
        logMsg += `Call Option Payoff: $${payoff.toFixed(2)}<br>`;
        explanation = `You <strong>bought a call option</strong> on ${companies[symbol].name} (${symbol}). This option gives you the right to buy the stock at $${strike.toFixed(2)}. Since the stock moved to $${newPrice.toFixed(2)}, its intrinsic value is $${(intrinsicValue * 100 * contracts).toFixed(2)}. After paying a premium of $${totalPremium.toFixed(2)}, your net result is $${profit.toFixed(2)}.`;
      } else if (action === "buy_put") {
        const intrinsicValue = Math.max(strike - newPrice, 0);
        payoff = intrinsicValue * 100 * contracts;
        profit = payoff - totalPremium;
        logMsg += `Put Option Payoff: $${payoff.toFixed(2)}<br>`;
        explanation = `You <strong>bought a put option</strong> on ${companies[symbol].name} (${symbol}). This option gives you the right to sell the stock at $${strike.toFixed(2)}. With the stock falling to $${newPrice.toFixed(2)}, its intrinsic value is $${(intrinsicValue * 100 * contracts).toFixed(2)}. After paying the premium of $${totalPremium.toFixed(2)}, your net profit/loss is $${profit.toFixed(2)}.`;
      } else if (action === "sell_call") {
        const intrinsicValue = Math.max(newPrice - strike, 0);
        cost = intrinsicValue * 100 * contracts;
        profit = totalPremium - cost;
        logMsg += `Call Option Obligation Cost: $${cost.toFixed(2)}<br>`;
        explanation = `You <strong>sold a call option</strong> on ${companies[symbol].name} (${symbol}). You collected a premium of $${totalPremium.toFixed(2)}, but you must sell the stock at $${strike.toFixed(2)} if exercised. With the stock at $${newPrice.toFixed(2)}, your obligation cost is $${cost.toFixed(2)}, resulting in a net profit/loss of $${profit.toFixed(2)}.`;
      } else if (action === "sell_put") {
        const intrinsicValue = Math.max(strike - newPrice, 0);
        cost = intrinsicValue * 100 * contracts;
        profit = totalPremium - cost;
        logMsg += `Put Option Obligation Cost: $${cost.toFixed(2)}<br>`;
        explanation = `You <strong>sold a put option</strong> on ${companies[symbol].name} (${symbol}). You received a premium of $${totalPremium.toFixed(2)}, but if exercised, you must buy the stock at $${strike.toFixed(2)}. With the stock at $${newPrice.toFixed(2)}, your cost is $${cost.toFixed(2)}, giving you a net profit/loss of $${profit.toFixed(2)}.`;
      }
      
      logMsg += `<strong>Net Profit/Loss:</strong> $${profit.toFixed(2)}<br>`;
      
      // Adjust bank based on the options outcome.
      if (action === "buy_call" || action === "buy_put") {
        bank += payoff;
      } else if (action === "sell_call" || action === "sell_put") {
        bank -= cost;
      }
      
      updateBankDisplay(oldBank, bank);
      logOptionsMessage(logMsg);
      updateExplanation(explanation);
      updateTicker();
      updatePortfolioDisplay();
    });
    
    // ============================================
    // Periodic Market Updates
    // ============================================
    // Update the simulated live market every 5 seconds
    setInterval(updateMarketPrices, 5000);
    
    // ============================================
    // Initial Setup on Page Load
    // ============================================
    window.onload = function() {
      updateTicker();
      populateStockOptions();
      updateLiveMarket();
      updatePortfolioDisplay();
      updateAccountSummary();
      updateBankDisplay(bank, bank);
    }
  </script>
</body>
</html>
