<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
    
<title>Monthly Performance Dashboard</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

body{
    font-family:Arial,Helvetica,sans-serif;
    margin:40px;
    background:#f5f7fa;
    color:#222;
}

.container{
    max-width:1200px;
    margin:auto;
}

.header{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:25px;
}

h1{
    margin:0;
    font-size:42px;
}

.subtitle{
    color:#666;
    margin-top:8px;
}

select{
    padding:10px;
    border-radius:8px;
    border:1px solid #ddd;
}

.cards{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:20px;
    margin-bottom:30px;
}

.card{
    background:white;
    border-radius:12px;
    padding:20px;
    box-shadow:0 2px 10px rgba(0,0,0,.08);
}

.card h2{
    margin-top:0;
}

.chart{
    background:white;
    border-radius:12px;
    padding:20px;
    margin-bottom:30px;
    box-shadow:0 2px 10px rgba(0,0,0,.08);
}

.bottom{
    display:grid;
    grid-template-columns:2fr 1fr;
    gap:20px;
}

table{
    width:100%;
    border-collapse:collapse;
}

th,td{
    padding:12px;
    border-bottom:1px solid #eee;
}

th{
    text-align:left;
}

.positive{
    color:#009879;
    font-weight:bold;
}

</style>

</head>

<body>

<div class="container">

<div class="header">

<div>

<h1>Monthly Performance</h1>

<div class="subtitle">
Portfolio results as of 31 Jul 2026
</div>

</div>

<select>

<option>July 2026</option>
<option>June 2026</option>

</select>

</div>


<div class="cards">

<div class="card">

<h2>Manager Commentary</h2>

<p>

The fund returned <b>+2.84%</b> during July, outperforming the benchmark.

Performance was driven by global quality equities while infrastructure continued to contribute positively.

</p>

</div>

<div class="card">

<h2>Market Outlook</h2>

<p>

Markets remain resilient despite elevated volatility.

We continue to favor quality companies with strong cash flow generation.

</p>

</div>

</div>



<div class="chart">

<h2>Cumulative Return</h2>

<canvas id="performance"></canvas>

</div>



<div class="bottom">

<div class="card">

<h2>Top Holdings</h2>

<table>

<tr>

<th>Holding</th>

<th>Weight</th>

<th>Return</th>

</tr>

<tr>

<td>Northstar Global Equity</td>

<td>14.8%</td>

<td class="positive">+4.2%</td>

</tr>

<tr>

<td>US Treasury 4.25%</td>

<td>9.6%</td>

<td class="positive">+1.1%</td>

</tr>

<tr>

<td>Global Infrastructure ETF</td>

<td>8.3%</td>

<td class="positive">+2.0%</td>

</tr>

</table>

</div>



<div class="card">

<h2>Net Investor Flows</h2>

<canvas id="flows"></canvas>

</div>

</div>

</div>



<script>

new Chart(document.getElementById('performance'),{

type:'line',

data:{

labels:['Feb','Mar','Apr','May','Jun','Jul'],

datasets:[

{

label:'Fund',

data:[1,2.5,2.0,4.5,5.8,7.9],

borderColor:'#0d9488',

tension:.4

},

{

label:'Benchmark',

data:[1,2.1,1.9,3.5,4.6,6.2],

borderColor:'#999',

borderDash:[5,5],

tension:.4

}

]

}

});


new Chart(document.getElementById('flows'),{

type:'bar',

data:{

labels:['Feb','Mar','Apr','May','Jun','Jul'],

datasets:[{

label:'Flows',

data:[3,4,-1,5,3,7]

}]

}

});

</script>

</body>
</html>
