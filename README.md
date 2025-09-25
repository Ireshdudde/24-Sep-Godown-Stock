<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Stock Details (24 Sep 2025)</title>
  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: #f5f7fa;
      color: #2c3e50;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background: linear-gradient(90deg, #0f2027, #203a43, #2c5364);
      color: #ffffff;
      padding: 1.2rem;
      text-align: center;
      font-size: 1.6rem;
      font-weight: 600;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
      letter-spacing: 0.8px;
    }

    .container {
      display: flex;
      flex: 1;
    }

    /* Sidebar (desktop/tablet) */
    .sidebar {
      background-color: #1e272e;
      color: #ffffff;
      width: 250px;
      padding: 1rem;
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
    }

    .sidebar button {
      background: transparent;
      border: none;
      color: #dcdde1;
      padding: 0.8rem 1rem;
      width: 100%;
      text-align: left;
      font-size: 1rem;
      cursor: pointer;
      border-left: 4px solid transparent;
      border-radius: 4px;
      transition: all 0.3s ease;
    }

    .sidebar button:hover,
    .sidebar button.active {
      background: #0abde3;
      color: #ffffff;
      border-left: 4px solid #00cec9;
      font-weight: bold;
    }

    /* Mobile-friendly horizontal menu */
    @media (max-width: 768px) {
      .container {
        flex-direction: column;
      }

      .sidebar {
        width: 100%;
        flex-direction: row;
        overflow-x: auto;
        padding: 0.5rem;
        gap: 0.5rem;
      }

      .sidebar button {
        flex: 1;
        min-width: max-content;
        text-align: center;
        border-left: none;
        border-bottom: 3px solid transparent;
      }

      .sidebar button:hover,
      .sidebar button.active {
        border-left: none;
        border-bottom: 3px solid #00cec9;
      }
    }

    .content {
      flex: 1;
      padding: 1rem;
      background: #f5f7fa;
      overflow-y: auto;
    }

    .location-title {
      font-size: 1.4rem;
      font-weight: bold;
      margin: 0 0 1rem;
      position: relative;
      padding-bottom: 0.5rem;
      text-transform: capitalize;
    }

    .location-title::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 4px;
      border-radius: 2px;
    }
    .location-title.akluj::after { background: #6c5ce7; }
    .location-title.jamner::after { background: #0984e3; }
    .location-title.narayangaon::after { background: #16a085; }
    .location-title.savda::after { background: #00b894; }
    .location-title.shirpur::after { background: #e17055; }

    .section-title {
      font-size: 1.2rem;
      margin: 1rem 0 0.5rem;
      color: #34495e;
      border-bottom: 2px solid #dcdde1;
      padding-bottom: 0.3rem;
    }

    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 1rem;
      margin-top: 0.8rem;
    }

    .card {
      background: #ffffff;
      border-left: 6px solid #3498db;
      border-radius: 6px;
      padding: 0.8rem;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.06);
      transition: transform 0.2s ease;
    }

    .card:hover { transform: translateY(-3px); }

    .card h4 {
      margin: 0;
      font-size: 0.95rem;
      font-weight: 600;
      color: #2c3e50;
    }

    .card p {
      margin: 0.3rem 0 0;
      font-size: 1.1rem;
      font-weight: bold;
      color: #2f3542;
    }

    .card p.negative { color: #e74c3c; }
  </style>
</head>
<body>
  <header>Stock Details (24 Sep 2025)</header>
  <div class="container">
    <div class="sidebar">
      <button onclick="showStock('akluj')" id="btn-akluj" class="active">Akluj</button>
      <button onclick="showStock('jamner')" id="btn-jamner">Jamner</button>
      <button onclick="showStock('narayangaon')" id="btn-narayangaon">Narayangaon</button>
      <button onclick="showStock('savda')" id="btn-savda">Savda</button>
      <button onclick="showStock('shirpur')" id="btn-shirpur">Shirpur</button>
      <button onclick="showStock('ramwadi')" id="btn-ramwadi">Ramwadi</button>
    </div>
    <div class="content" id="stockContent"></div>
  </div>

  <script>
    const createCards = (items) => {
      return items.map(item => {
        const isNegative = item.qty.toString().includes('-');
        return `
          <div class="card">
            <h4>${item.name}</h4>
            <p class="${isNegative ? 'negative' : ''}">${item.qty}</p>
          </div>
        `;
      }).join('');
    };

    const stockData = {
      savda: {
        balance: [
          { name: "King Brown Box (Nos)", qty: "2300" },
          { name: "Bandhan Premium", qty: "1500" },
          { name: "Alaa white Box (Nos)", qty: "500" },
          { name: "Roshana Box (Nos)", qty: "0" },
          { name: "Laibaah Box (Nos)", qty: "350" },
          { name: "Haniya Box (Nos)", qty: "800" },
          { name: "Shabad Box(Nos)", qty: "280" },
          { name: "Vaccum Bag 13kg", qty: "1720" },
          { name: "PE Form 1.5 MM (Nos)", qty: "0" },
          { name: "Sachets (Nos)", qty: "0" },
          { name: "Fevicol (kg)", qty: "0" },
          { name: "Germination Paper (kg)", qty: "850" },
          { name: "Fungicide (kg)", qty: "4" },
          { name: "Truti (kg)", qty: "0" },
          { name: "Bleaching Powder (g)", qty: "0" },
          { name: "Rubber (kg)", qty: "0" },
          { name: "King Sticker (Nos)", qty: "56000" },
          { name: "Alaa Sticker (Nos)", qty: "4650000" },
          { name: "Roshana Sticker (Nos)", qty: "1610000" },
          { name: "Other Sticker", qty: "2520000" }
        ]
      },
      akluj: {
        outward: [
          { name: "Roshana Box (Nos)", qty: "1325 nos" },
          { name: "laibaah Box", qty: "0 nos" },
          { name: "Haniya Box", qty: "0 nos" },
          { name: "Vaccum Bag 13kg", qty: "60.22727273 KG" },
          { name: "Vaccum Bag 7kg", qty: "0 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "9275 nos" },
          { name: "Sachets (Nos)", qty: "1325 nos" },
          { name: "fevicol (kg)", qty: "8 KG" },
          { name: "Germination Paper (kg)", qty: "26.5 KG" },
          { name: "Bavistin", qty: "3 KG" },
          { name: "Truti (kg)", qty: "10 KG" },
          { name: "Bleaching Powder (g)", qty: "0.2 KG" },
          { name: "Rubber (kg)", qty: "1 KG" },
          { name: "Roshana Sticker (Nos)", qty: "21200 nos" }
        ],
        balance: [
          { name: "Roshana Box (Nos)", qty: "200 nos" },
          { name: "laibaah Box", qty: "6069 nos" },
          { name: "Haniya Box", qty: "0 nos" },
          { name: "Vaccum Bag 13kg", qty: "840 KG" },
          { name: "Vaccum Bag 7kg", qty: "118.818 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "28000 nos" },
          { name: "Sachets (Nos)", qty: "9000 nos" },
          { name: "fevicol (kg)", qty: "10 KG" },
          { name: "Germination Paper (kg)", qty: "75 KG" },
          { name: "Bavistin", qty: "18 KG" },
          { name: "Truti (kg)", qty: "200 KG" },
          { name: "Bleaching Powder (g)", qty: "15 KG" },
          { name: "Rubber (kg)", qty: "25 KG" },
          { name: "Roshana Sticker (Nos)", qty: "200000 nos" }
        ]
      },
      ramwadi: {
        balance: [
          { name: "Roshana Box (Nos)", qty: "800 nos" },
          { name: "Laibaah Box", qty: "650 nos" },
          { name: "Haniya Box", qty: "0 nos" },
          { name: "Vaccum Bag 13kg", qty: "630 KG" },
          { name: "Vaccum Bag 7kg", qty: "210 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "28000 nos" },
          { name: "Sachets (Nos)", qty: "6500 nos" },
          { name: "fevicol (kg)", qty: "50 Packet" },
          { name: "Germination Paper (kg)", qty: "400 KG" },
          { name: "Fungicide (kg)", qty: "7 KG" },
          { name: "Truti (kg)", qty: "50 KG" },
          { name: "Bleaching Powder (g)", qty: "30 KG" },
          { name: "Rubber (kg)", qty: "10 KG" },
          { name: "Roshana Sticker", qty: "7 bundle" },
          { name: "King Sticker", qty: "5 bundle" },
          { name: "Bandhan Sticker", qty: "16 bundle" }
        ]
      },
      jamner: {
        outward: [
          { name: "Roshana Box (Nos)", qty: "2326 nos" },
          { name: "Vaccum Bag 13kg", qty: "105.7272727 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "16282 nos" },
          { name: "Sachets (Nos)", qty: "2326 nos" },
          { name: "fevicol (kg)", qty: "12 KG" },
          { name: "Germination Paper (kg)", qty: "46.52 KG" },
          { name: "Fungicide (kg)", qty: "4.5 KG" },
          { name: "Truti (kg)", qty: "15 KG" },
          { name: "Bleaching Powder (g)", qty: "0.3 G" },
          { name: "Rubber (kg)", qty: "1.5 KG" },
          { name: "Roshana Sticker (Nos)", qty: "37216" }
        ],
        balance: [
          { name: "Roshana Box (Nos)", qty: "17810 nos" },
          { name: "Vaccum Bag 13kg", qty: "1739.45 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "117784 nos" },
          { name: "Sachets (Nos)", qty: "19610 nos" },
          { name: "fevicol (kg)", qty: "208.5 KG" },
          { name: "Germination Paper (kg)", qty: "1079.78 KG" },
          { name: "Fungicide (kg)", qty: "0 KG" },
          { name: "Truti (kg)", qty: "452.8 KG" },
          { name: "Bleaching Powder (g)", qty: "5.4 KG" },
          { name: "Rubber (kg)", qty: "14.5 KG" },
          { name: "Roshana Sticker (Nos)", qty: "643470 nos" }
        ]
      },
      narayangaon: {
        outward: [
          { name: "Roshana Box (Nos)", qty: "649 nos" },
          { name: "Vaccum Bag 13kg", qty: "29.5 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "4543 nos" },
          { name: "Sachets (Nos)", qty: "649 nos" },
          { name: "fevicol (kg)", qty: "4 KG" },
          { name: "Germination Paper (kg)", qty: "12.98 KG" },
          { name: "Fungicide (kg)", qty: "1.5 KG" },
          { name: "Truti (kg)", qty: "5 KG" },
          { name: "Bleaching Powder (g)", qty: "0.1 KG" },
          { name: "Rubber (kg)", qty: "0.5 KG" },
          { name: "Roshana Sticker (Nos)", qty: "10384 nos" }
        ],
        balance: [
          { name: "Roshana Box (Nos)", qty: "3615 nos" },
          { name: "Vaccum Bag 13kg", qty: "901.5 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "112679 nos" },
          { name: "Sachets (Nos)", qty: "17888 nos" },
          { name: "fevicol (kg)", qty: "89.5 KG" },
          { name: "Germination Paper (kg)", qty: "209.02 KG" },
          { name: "Fungicide (kg)", qty: "39.5 KG" },
          { name: "Truti (kg)", qty: "135 KG" },
          { name: "Bleaching Powder (g)", qty: "9.7 KG" },
          { name: "Rubber (kg)", qty: "51.7 KG" },
          { name: "Roshana Sticker (Nos)", qty: "208404 nos" },
          { name: "King Sticker (Nos)", qty: "218788 nos" },
          { name: "King Brown Box", qty: "400 nos" }
        ]
      },
      shirpur: {
        outward: [
          { name: "Roshana Box (Nos)", qty: "493 nos" },
          { name: "Vaccum Bag 13kg", qty: "22.40909091 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "7888 nos" },
          { name: "Sachets (Nos)", qty: "493 nos" },
          { name: "fevicol (kg)", qty: "3 KG" },
          { name: "Germination Paper (kg)", qty: "9.86 KG" },
          { name: "Fungicide (kg)", qty: "1.5 KG" },
          { name: "Truti (kg)", qty: "5 KG" },
          { name: "Bleaching Powder (g)", qty: "0.1 G" },
          { name: "Rubber (kg)", qty: "0.4 KG" },
          { name: "Roshana Sticker (Nos)", qty: "7888" }
        ],
        balance: [
          { name: "Roshana Box (Nos)", qty: "1203 nos" },
          { name: "Vaccum Bag 13kg", qty: "211.106 KG" },
          { name: "PE Form 1.5 MM (Nos)", qty: "3526 nos" },
          { name: "Sachets (Nos)", qty: "5305 nos" },
          { name: "fevicol (kg)", qty: "64 KG" },
          { name: "Germination Paper (kg)", qty: "36.08 KG" },
          { name: "Fungicide (kg)", qty: "2.5 KG" },
          { name: "Truti (kg)", qty: "25 KG" },
          { name: "Bleaching Powder (g)", qty: "2.4 G" },
          { name: "Rubber (kg)", qty: "1.2 KG" },
          { name: "Roshana Sticker (Nos)", qty: "591100" }
        ]
      }
    };

    function showStock(area) {
      document.querySelectorAll(".sidebar button").forEach(btn => btn.classList.remove("active"));
      document.getElementById(`btn-${area}`).classList.add("active");

      const data = stockData[area];
      let html = `<div class="location-title ${area}">${area} Stock Details (24 Sep 2025)</div>`;

      if (data.inward) {
        html += `<div class="section-title">Inward</div><div class="card-grid">${createCards(data.inward)}</div>`;
      }
      if (data.outward) {
        html += `<div class="section-title">Outward</div><div class="card-grid">${createCards(data.outward)}</div>`;
      }
      if (data.balance) {
        html += `<div class="section-title">Balance</div><div class="card-grid">${createCards(data.balance)}</div>`;
      }

      document.getElementById("stockContent").innerHTML = html;
    }

    showStock("akluj");
  </script>
</body>
</html>
