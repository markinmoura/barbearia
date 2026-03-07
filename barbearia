<!DOCTYPE html>
<html lang="pt-BR">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Sistema Barbearia</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

body{
margin:0;
font-family:Arial;
background:#f4f4f4;
}

header{
background:#111;
color:white;
padding:15px;
display:flex;
justify-content:space-between;
}

.layout{
display:flex;
height:100vh;
}

.sidebar{
width:200px;
background:#1f1f1f;
display:flex;
flex-direction:column;
}

.sidebar button{
padding:15px;
border:none;
background:none;
color:white;
text-align:left;
cursor:pointer;
}

main{
flex:1;
padding:20px;
}

.cards{
display:flex;
gap:20px;
margin-bottom:20px;
}

.card{
background:white;
padding:20px;
border-radius:8px;
box-shadow:0 3px 10px rgba(0,0,0,0.1);
}

table{
width:100%;
border-collapse:collapse;
background:white;
}

th,td{
padding:10px;
border-bottom:1px solid #ddd;
}

.hidden{
display:none;
}

.login{
display:flex;
justify-content:center;
align-items:center;
height:100vh;
background:#111;
}

.login-box{
background:white;
padding:40px;
border-radius:8px;
width:300px;
}

input{
width:100%;
padding:10px;
margin:10px 0;
}

button{
padding:10px;
cursor:pointer;
}

</style>

</head>

<body>

<div id="login" class="login">

<div class="login-box">

<h2>Sistema Barbearia</h2>

<input placeholder="Email">
<input placeholder="Senha" type="password">

<button onclick="entrar()">Entrar</button>

</div>

</div>

<div id="sistema" class="hidden">

<header>

<h2>Painel Barbearia</h2>

<button onclick="logout()">Sair</button>

</header>

<div class="layout">

<nav class="sidebar">

<button onclick="abrir('dashboard')">Dashboard</button>
<button onclick="abrir('agenda')">Agenda</button>
<button onclick="abrir('clientes')">Clientes</button>
<button onclick="abrir('servicos')">Serviços</button>
<button onclick="abrir('relatorios')">Relatórios</button>

</nav>

<main>

<section id="dashboard">

<div class="cards">

<div class="card">
<h3>Atendimentos Hoje</h3>
<p id="atendimentos">0</p>
</div>

<div class="card">
<h3>Faturamento</h3>
<p id="faturamento">R$0</p>
</div>

<div class="card">
<h3>Clientes</h3>
<p id="totalClientes">0</p>
</div>

</div>

<canvas id="grafico"></canvas>

</section>

<section id="agenda" class="hidden">

<h2>Agenda</h2>

<input id="clienteAgenda" placeholder="Cliente">
<input id="servicoAgenda" placeholder="Serviço">
<input id="horaAgenda" placeholder="Horário">

<button onclick="agendar()">Agendar</button>

<table>

<tr>
<th>Cliente</th>
<th>Serviço</th>
<th>Horário</th>
</tr>

<tbody id="listaAgenda"></tbody>

</table>

</section>

<section id="clientes" class="hidden">

<h2>Clientes</h2>

<input id="nomeCliente" placeholder="Nome">
<input id="telefoneCliente" placeholder="Telefone">

<button onclick="addCliente()">Cadastrar</button>

<ul id="listaClientes"></ul>

</section>

<section id="servicos" class="hidden">

<h2>Serviços</h2>

<input id="nomeServico" placeholder="Serviço">
<input id="valorServico" placeholder="Valor">

<button onclick="addServico()">Adicionar</button>

<ul id="listaServicos"></ul>

</section>

<section id="relatorios" class="hidden">

<h2>Relatórios</h2>

<canvas id="graficoRelatorio"></canvas>

</section>

</main>

</div>

</div>

<script>

let clientes=[]
let servicos=[]
let agenda=[]

function entrar(){

document.getElementById("login").style.display="none"
document.getElementById("sistema").classList.remove("hidden")

}

function logout(){

location.reload()

}

function abrir(sec){

document.querySelectorAll("main section").forEach(s=>s.classList.add("hidden"))

document.getElementById(sec).classList.remove("hidden")

}

function addCliente(){

let nome=document.getElementById("nomeCliente").value
let tel=document.getElementById("telefoneCliente").value

clientes.push({nome,tel})

renderClientes()

}

function renderClientes(){

let html=""

clientes.forEach(c=>{
html+=`<li>${c.nome} - ${c.tel}</li>`
})

document.getElementById("listaClientes").innerHTML=html
document.getElementById("totalClientes").innerText=clientes.length

}

function addServico(){

let nome=document.getElementById("nomeServico").value
let valor=document.getElementById("valorServico").value

servicos.push({nome,valor})

renderServicos()

}

function renderServicos(){

let html=""

servicos.forEach(s=>{
html+=`<li>${s.nome} - R$${s.valor}</li>`
})

document.getElementById("listaServicos").innerHTML=html

}

function agendar(){

let cliente=document.getElementById("clienteAgenda").value
let servico=document.getElementById("servicoAgenda").value
let hora=document.getElementById("horaAgenda").value

agenda.push({cliente,servico,hora})

renderAgenda()

}

function renderAgenda(){

let html=""

agenda.forEach(a=>{

html+=`
<tr>
<td>${a.cliente}</td>
<td>${a.servico}</td>
<td>${a.hora}</td>
</tr>
`

})

document.getElementById("listaAgenda").innerHTML=html
document.getElementById("atendimentos").innerText=agenda.length

}

const ctx=document.getElementById("grafico")

new Chart(ctx,{

type:"bar",

data:{

labels:["Seg","Ter","Qua","Qui","Sex","Sab"],

datasets:[{

label:"Faturamento",

data:[200,300,250,400,350,500]

}]

}

})

</script>

</body>
</html>
