<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>India — Favourite Movie Poll 2025</title>
  <style>
    :root{
      --bg:#0f1724; --card:#0b1220; --accent:#06b6d4; --muted:#94a3b8;
      --radius:14px;
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      color-scheme: dark;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      background: linear-gradient(180deg,#071022 0%, #061826 100%);
      color: #e6eef6;
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:20px;
      flex-direction:column;
    }
    .container{
      width:100%;
      max-width:900px;
      background: rgba(255,255,255,0.03);
      border-radius:18px;
      padding:20px;
      box-shadow: 0 6px 30px rgba(2,6,23,0.6);
    }
    header{ text-align:center; margin-bottom:20px; }
    header h1{ font-size:22px; margin:0 }
    header p{ margin:0; color:var(--muted); font-size:14px }
    .card{ background:var(--card); padding:16px; border-radius:var(--radius); margin-top:15px; }
    label{ font-size:14px; color:var(--muted); display:block; margin-bottom:6px; }
    input[type="text"]{
      width:100%; padding:10px; border:none; border-radius:10px;
      background:#1e293b; color:white; font-size:14px;
    }
    button{
      width:100%; padding:12px; border:none; border-radius:10px;
      background:var(--accent); color:black; font-weight:600; cursor:pointer;
      transition:0.2s;
    }
    button:hover{ opacity:0.85; }
    table{ width:100%; border-collapse:collapse; margin-top:10px; }
    th, td{ padding:8px; border-bottom:1px solid #1e293b; text-align:left; font-size:14px }
    th{ color:var(--accent); }
  </style>
</head>
<body>
  <!-- Background Music (hidden) -->
  <audio autoplay loop hidden>
    <source src="clideo-editor-55a1f6339e3f4308ad3789ada3f4074b_tIsGsZo8.mp3" type="audio/mpeg">
    Your browser does not support audio.
  </audio>

  <div class="container">
    <header>
      <h1>🇮🇳 Favourite Movie Poll — 2025</h1>
      <p>Enter your name & your favourite movie from anywhere in India!</p>
    </header>

    <div class="card">
      <form id="pollForm">
        <label>Name</label>
        <input type="text" id="name" placeholder="Enter your name" required>
        <label>Favourite Movie</label>
        <input type="text" id="movie" placeholder="Enter your favourite movie" required>
        <br>
        <button type="submit">Submit</button>
      </form>
    </div>

    <div class="card">
      <h2>📊 Live Results</h2>
      <table id="resultsTable">
        <thead>
          <tr><th>Movie</th><th>Votes</th></tr>
        </thead>
        <tbody></tbody>
      </table>
    </div>
  </div>

  <script>
    const form = document.getElementById("pollForm");
    const resultsTable = document.querySelector("#resultsTable tbody");

    // Load saved data
    let votes = JSON.parse(localStorage.getItem("votes2025")) || {};

    function updateTable(){
      resultsTable.innerHTML = "";
      const sorted = Object.entries(votes).sort((a,b)=>b[1]-a[1]);
      sorted.forEach(([movie,count])=>{
        let row = `<tr><td>${movie}</td><td>${count}</td></tr>`;
        resultsTable.innerHTML += row;
      });
    }
    updateTable();

    form.addEventListener("submit", e=>{
      e.preventDefault();
      let name = document.getElementById("name").value.trim();
      let movie = document.getElementById("movie").value.trim();
      if(!name || !movie) return;

      // Save vote
      votes[movie] = (votes[movie]||0)+1;
      localStorage.setItem("votes2025", JSON.stringify(votes));

      updateTable();
      form.reset();
      alert("Thanks " + name + "! Your vote has been recorded.");
    });
  </script>
</body>
</html>
