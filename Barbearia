<!doctype html>
<html lang="pt-BR" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BarberPro - Sistema de Gestão para Barbearias</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&amp;display=swap" rel="stylesheet">
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Plus Jakarta Sans', 'system-ui', 'sans-serif'],
          },
          colors: {
            brand: {
              50: '#fef7ee',
              100: '#fdedd3',
              200: '#f9d7a5',
              300: '#f5bb6d',
              400: '#f09732',
              500: '#ec7a0f',
              600: '#dd6009',
              700: '#b7480a',
              800: '#923a10',
              900: '#763210',
            },
            dark: {
              800: '#1a1a2e',
              900: '#16162a',
              950: '#0f0f1a',
            }
          }
        }
      }
    }
  </script>
  <style>
    * { box-sizing: border-box; }
    html, body { height: 100%; margin: 0; padding: 0; }
    
    .sidebar-item {
      transition: all 0.2s ease;
    }
    .sidebar-item:hover {
      background: rgba(240, 151, 50, 0.1);
      border-left-color: #f09732;
    }
    .sidebar-item.active {
      background: rgba(240, 151, 50, 0.15);
      border-left-color: #f09732;
      color: #f09732;
    }
    
    .card {
      background: linear-gradient(145deg, #1e1e36 0%, #1a1a2e 100%);
      border: 1px solid rgba(255,255,255,0.05);
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .card:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 30px rgba(0,0,0,0.3);
    }
    
    .btn-primary {
      background: linear-gradient(135deg, #f09732 0%, #dd6009 100%);
      transition: all 0.2s ease;
    }
    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 4px 15px rgba(240, 151, 50, 0.4);
    }
    
    .input-field {
      background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,255,255,0.1);
      transition: all 0.2s ease;
    }
    .input-field:focus {
      border-color: #f09732;
      box-shadow: 0 0 0 3px rgba(240, 151, 50, 0.1);
      outline: none;
    }
    
    .status-scheduled { background: #3b82f6; }
    .status-completed { background: #22c55e; }
    .status-cancelled { background: #ef4444; }
    
    .fade-in {
      animation: fadeIn 0.3s ease forwards;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .slide-in {
      animation: slideIn 0.4s ease forwards;
    }
    @keyframes slideIn {
      from { opacity: 0; transform: translateX(-20px); }
      to { opacity: 1; transform: translateX(0); }
    }
    
    .pulse-glow {
      animation: pulseGlow 2s ease-in-out infinite;
    }
    @keyframes pulseGlow {
      0%, 100% { box-shadow: 0 0 5px rgba(240, 151, 50, 0.3); }
      50% { box-shadow: 0 0 20px rgba(240, 151, 50, 0.6); }
    }
    
    .table-row {
      transition: background 0.2s ease;
    }
    .table-row:hover {
      background: rgba(255,255,255,0.03);
    }
    
    ::-webkit-scrollbar { width: 8px; height: 8px; }
    ::-webkit-scrollbar-track { background: #1a1a2e; }
    ::-webkit-scrollbar-thumb { background: #3d3d5c; border-radius: 4px; }
    ::-webkit-scrollbar-thumb:hover { background: #4d4d6c; }
    
    .calendar-day {
      transition: all 0.2s ease;
    }
    .calendar-day:hover {
      background: rgba(240, 151, 50, 0.1);
    }
    .calendar-day.today {
      border: 2px solid #f09732;
    }
    .calendar-day.selected {
      background: rgba(240, 151, 50, 0.2);
    }
    
    .time-slot {
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .time-slot:hover {
      background: rgba(240, 151, 50, 0.1);
      border-color: #f09732;
    }
    .time-slot.booked {
      cursor: default;
    }
    
    .modal-overlay {
      background: rgba(0,0,0,0.7);
      backdrop-filter: blur(4px);
    }
    
    .toast {
      animation: toastIn 0.3s ease forwards;
    }
    @keyframes toastIn {
      from { opacity: 0; transform: translateX(100%); }
      to { opacity: 1; transform: translateX(0); }
    }
  </style>
  <style>body { box-sizing: border-box; }</style>
 </head>
 <body class="h-full bg-dark-950 text-gray-100 font-sans overflow-hidden"><!-- Login Screen -->
  <div id="loginScreen" class="h-full flex items-center justify-center p-4" style="background: radial-gradient(ellipse at center, #1a1a2e 0%, #0f0f1a 100%);">
   <div class="w-full max-w-md fade-in">
    <div class="text-center mb-8">
     <div class="w-20 h-20 mx-auto mb-4 rounded-2xl bg-gradient-to-br from-brand-400 to-brand-600 flex items-center justify-center pulse-glow">
      <svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.121 14.121L19 19m-7-7l7-7m-7 7l-2.879 2.879M12 12L9.121 9.121m0 5.758a3 3 0 10-4.243 4.243 3 3 0 004.243-4.243zm0-5.758a3 3 0 10-4.243-4.243 3 3 0 004.243 4.243z" />
      </svg>
     </div>
     <h1 id="loginShopName" class="text-3xl font-bold text-white mb-2">BarberPro</h1>
     <p class="text-gray-400">Sistema de Gestão para Barbearias</p>
    </div>
    <div class="card rounded-2xl p-8">
     <form id="loginForm" class="space-y-6">
      <div><label for="loginEmail" class="block text-sm font-medium text-gray-300 mb-2">Email</label> <input type="email" id="loginEmail" class="input-field w-full px-4 py-3 rounded-xl text-white placeholder-gray-500" placeholder="seu@email.com" required>
      </div>
      <div><label for="loginPassword" class="block text-sm font-medium text-gray-300 mb-2">Senha</label> <input type="password" id="loginPassword" class="input-field w-full px-4 py-3 rounded-xl text-white placeholder-gray-500" placeholder="••••••••" required>
      </div><button type="submit" class="btn-primary w-full py-3 rounded-xl text-white font-semibold text-lg"> Entrar </button>
     </form>
     <div class="mt-6 text-center"><a href="#" class="text-brand-400 hover:text-brand-300 text-sm transition-colors">Esqueci minha senha</a>
     </div>
    </div>
    <p class="text-center text-gray-500 text-sm mt-6">© 2024 BarberPro. Todos os direitos reservados.</p>
   </div>
  </div><!-- Main App -->
  <div id="mainApp" class="h-full flex hidden"><!-- Sidebar -->
   <aside id="sidebar" class="w-64 bg-dark-900 border-r border-gray-800 flex flex-col h-full shrink-0 transition-all duration-300 z-20">
    <div class="p-6 border-b border-gray-800">
     <div class="flex items-center gap-3">
      <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-brand-400 to-brand-600 flex items-center justify-center">
       <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.121 14.121L19 19m-7-7l7-7m-7 7l-2.879 2.879M12 12L9.121 9.121m0 5.758a3 3 0 10-4.243 4.243 3 3 0 004.243-4.243zm0-5.758a3 3 0 10-4.243-4.243 3 3 0 004.243 4.243z" />
       </svg>
      </div><span id="sidebarShopName" class="text-lg font-bold text-white">BarberPro</span>
     </div>
    </div>
    <nav class="flex-1 py-4 overflow-y-auto">
     <ul class="space-y-1 px-3">
      <li><button onclick="navigateTo('dashboard')" class="sidebar-item w-full flex items-center gap-3 px-4 py-3 rounded-xl text-gray-300 border-l-4 border-transparent active" data-page="dashboard">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z" />
        </svg><span class="font-medium">Dashboard</span> </button></li>
      <li><button onclick="navigateTo('agenda')" class="sidebar-item w-full flex items-center gap-3 px-4 py-3 rounded-xl text-gray-300 border-l-4 border-transparent" data-page="agenda">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
        </svg><span class="font-medium">Agenda</span> </button></li>
      <li><button onclick="navigateTo('clients')" class="sidebar-item w-full flex items-center gap-3 px-4 py-3 rounded-xl text-gray-300 border-l-4 border-transparent" data-page="clients">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
        </svg><span class="font-medium">Clientes</span> </button></li>
      <li><button onclick="navigateTo('services')" class="sidebar-item w-full flex items-center gap-3 px-4 py-3 rounded-xl text-gray-300 border-l-4 border-transparent" data-page="services">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-6 9l2 2 4-4" />
        </svg><span class="font-medium">Serviços</span> </button></li>
      <li><button onclick="navigateTo('reports')" class="sidebar-item w-full flex items-center gap-3 px-4 py-3 rounded-xl text-gray-300 border-l-4 border-transparent" data-page="reports">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
        </svg><span class="font-medium">Relatórios</span> </button></li>
      <li><button onclick="navigateTo('settings')" class="sidebar-item w-full flex items-center gap-3 px-4 py-3 rounded-xl text-gray-300 border-l-4 border-transparent" data-page="settings">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
        </svg><span class="font-medium">Configurações</span> </button></li>
     </ul>
    </nav>
    <div class="p-4 border-t border-gray-800"><button onclick="logout()" class="w-full flex items-center gap-3 px-4 py-3 rounded-xl text-red-400 hover:bg-red-500/10 transition-colors">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1" />
      </svg><span class="font-medium">Sair</span> </button>
    </div>
   </aside><!-- Main Content Area -->
   <div class="flex-1 flex flex-col h-full overflow-hidden"><!-- Header -->
    <header class="bg-dark-900 border-b border-gray-800 px-6 py-4 flex items-center justify-between shrink-0">
     <div class="flex items-center gap-4"><button id="menuToggle" onclick="toggleSidebar()" class="lg:hidden p-2 rounded-lg hover:bg-gray-800 transition-colors">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
       </svg></button>
      <div>
       <h1 id="pageTitle" class="text-xl font-bold text-white">Dashboard</h1>
       <p id="welcomeMessage" class="text-sm text-gray-400">Bem-vindo de volta!</p>
      </div>
     </div>
     <div class="flex items-center gap-4"><button class="relative p-2 rounded-lg hover:bg-gray-800 transition-colors">
       <svg class="w-6 h-6 text-gray-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
       </svg><span class="absolute top-1 right-1 w-2 h-2 bg-brand-500 rounded-full"></span> </button>
      <div class="flex items-center gap-3">
       <div class="w-10 h-10 rounded-full bg-gradient-to-br from-brand-400 to-brand-600 flex items-center justify-center text-white font-bold">
        A
       </div>
       <div class="hidden sm:block">
        <p class="text-sm font-medium text-white">Admin</p>
        <p class="text-xs text-gray-400">Administrador</p>
       </div>
      </div>
     </div>
    </header><!-- Content Pages -->
    <main class="flex-1 overflow-y-auto p-6 bg-dark-950"><!-- Dashboard Page -->
     <div id="dashboardPage" class="page fade-in"><!-- Stats Cards -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
       <div class="card rounded-2xl p-6">
        <div class="flex items-center justify-between mb-4">
         <div class="w-12 h-12 rounded-xl bg-blue-500/20 flex items-center justify-center">
          <svg class="w-6 h-6 text-blue-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
          </svg>
         </div><span class="text-green-400 text-sm font-medium">+12%</span>
        </div>
        <h3 class="text-3xl font-bold text-white mb-1" id="todayAppointments">0</h3>
        <p class="text-gray-400 text-sm">Atendimentos hoje</p>
       </div>
       <div class="card rounded-2xl p-6">
        <div class="flex items-center justify-between mb-4">
         <div class="w-12 h-12 rounded-xl bg-green-500/20 flex items-center justify-center">
          <svg class="w-6 h-6 text-green-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
         </div><span class="text-green-400 text-sm font-medium">+8%</span>
        </div>
        <h3 class="text-3xl font-bold text-white mb-1" id="todayRevenue">R$ 0</h3>
        <p class="text-gray-400 text-sm">Faturamento hoje</p>
       </div>
       <div class="card rounded-2xl p-6">
        <div class="flex items-center justify-between mb-4">
         <div class="w-12 h-12 rounded-xl bg-purple-500/20 flex items-center justify-center">
          <svg class="w-6 h-6 text-purple-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
          </svg>
         </div><span class="text-green-400 text-sm font-medium">+5%</span>
        </div>
        <h3 class="text-3xl font-bold text-white mb-1" id="totalClients">0</h3>
        <p class="text-gray-400 text-sm">Total de clientes</p>
       </div>
       <div class="card rounded-2xl p-6">
        <div class="flex items-center justify-between mb-4">
         <div class="w-12 h-12 rounded-xl bg-brand-500/20 flex items-center justify-center">
          <svg class="w-6 h-6 text-brand-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
         </div>
        </div>
        <h3 class="text-lg font-bold text-white mb-1 truncate" id="nextClient">Nenhum agendamento</h3>
        <p class="text-gray-400 text-sm">Próximo cliente</p>
       </div>
      </div><!-- Charts and Recent -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
       <div class="lg:col-span-2 card rounded-2xl p-6">
        <h3 class="text-lg font-bold text-white mb-6">Faturamento Semanal</h3>
        <div class="h-64">
         <canvas id="weeklyChart"></canvas>
        </div>
       </div>
       <div class="card rounded-2xl p-6">
        <h3 class="text-lg font-bold text-white mb-6">Próximos Atendimentos</h3>
        <div id="upcomingAppointments" class="space-y-4 max-h-64 overflow-y-auto">
         <p class="text-gray-400 text-sm">Nenhum atendimento agendado</p>
        </div>
       </div>
      </div><!-- Top Services -->
      <div class="mt-6 card rounded-2xl p-6">
       <h3 class="text-lg font-bold text-white mb-6">Serviços Mais Vendidos</h3>
       <div id="topServices" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
        <p class="text-gray-400 text-sm col-span-full">Nenhum serviço cadastrado</p>
       </div>
      </div>
     </div><!-- Agenda Page -->
     <div id="agendaPage" class="page hidden">
      <div class="flex flex-col lg:flex-row gap-6"><!-- Calendar -->
       <div class="lg:w-80 card rounded-2xl p-6 shrink-0">
        <div class="flex items-center justify-between mb-6">
         <h3 class="text-lg font-bold text-white" id="currentMonth">Janeiro 2024</h3>
         <div class="flex gap-2"><button onclick="changeMonth(-1)" class="p-2 rounded-lg hover:bg-gray-700 transition-colors">
           <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
           </svg></button> <button onclick="changeMonth(1)" class="p-2 rounded-lg hover:bg-gray-700 transition-colors">
           <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
           </svg></button>
         </div>
        </div>
        <div class="grid grid-cols-7 gap-1 mb-2">
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Dom
         </div>
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Seg
         </div>
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Ter
         </div>
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Qua
         </div>
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Qui
         </div>
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Sex
         </div>
         <div class="text-center text-xs text-gray-500 font-medium py-2">
          Sáb
         </div>
        </div>
        <div id="calendarGrid" class="grid grid-cols-7 gap-1"><!-- Calendar days will be generated here -->
        </div><button onclick="openAppointmentModal()" class="btn-primary w-full mt-6 py-3 rounded-xl text-white font-semibold flex items-center justify-center gap-2">
         <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
         </svg> Novo Agendamento </button>
       </div><!-- Day Schedule -->
       <div class="flex-1 card rounded-2xl p-6">
        <div class="flex items-center justify-between mb-6">
         <div>
          <h3 class="text-lg font-bold text-white" id="selectedDateTitle">Hoje</h3>
          <p class="text-sm text-gray-400" id="selectedDateSubtitle"></p>
         </div>
         <div class="flex gap-2"><button onclick="setView('day')" class="px-4 py-2 rounded-lg bg-brand-500/20 text-brand-400 font-medium text-sm" id="viewDayBtn">Dia</button> <button onclick="setView('week')" class="px-4 py-2 rounded-lg hover:bg-gray-700 text-gray-400 font-medium text-sm transition-colors" id="viewWeekBtn">Semana</button>
         </div>
        </div>
        <div id="scheduleView" class="space-y-2 max-h-96 overflow-y-auto"><!-- Time slots will be generated here -->
        </div>
       </div>
      </div>
     </div><!-- Clients Page -->
     <div id="clientsPage" class="page hidden">
      <div class="card rounded-2xl p-6 mb-6">
       <div class="flex flex-col sm:flex-row gap-4 items-start sm:items-center justify-between">
        <div class="flex-1 max-w-md">
         <div class="relative">
          <svg class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
          </svg><input type="text" id="clientSearch" placeholder="Buscar cliente..." class="input-field w-full pl-10 pr-4 py-3 rounded-xl text-white placeholder-gray-500" oninput="filterClients()">
         </div>
        </div><button onclick="openClientModal()" class="btn-primary px-6 py-3 rounded-xl text-white font-semibold flex items-center gap-2 shrink-0">
         <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
         </svg> Novo Cliente </button>
       </div>
      </div>
      <div class="card rounded-2xl overflow-hidden">
       <div class="overflow-x-auto">
        <table class="w-full">
         <thead>
          <tr class="border-b border-gray-800">
           <th class="text-left px-6 py-4 text-sm font-semibold text-gray-400">Nome</th>
           <th class="text-left px-6 py-4 text-sm font-semibold text-gray-400">Telefone</th>
           <th class="text-left px-6 py-4 text-sm font-semibold text-gray-400 hidden sm:table-cell">Email</th>
           <th class="text-left px-6 py-4 text-sm font-semibold text-gray-400 hidden lg:table-cell">Atendimentos</th>
           <th class="text-right px-6 py-4 text-sm font-semibold text-gray-400">Ações</th>
          </tr>
         </thead>
         <tbody id="clientsTableBody">
          <tr>
           <td colspan="5" class="px-6 py-8 text-center text-gray-400">Nenhum cliente cadastrado</td>
          </tr>
         </tbody>
        </table>
       </div>
      </div>
     </div><!-- Services Page -->
     <div id="servicesPage" class="page hidden">
      <div class="card rounded-2xl p-6 mb-6">
       <div class="flex flex-col sm:flex-row gap-4 items-start sm:items-center justify-between">
        <div class="flex-1 max-w-md">
         <div class="relative">
          <svg class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
          </svg><input type="text" id="serviceSearch" placeholder="Buscar serviço..." class="input-field w-full pl-10 pr-4 py-3 rounded-xl text-white placeholder-gray-500" oninput="filterServices()">
         </div>
        </div><button onclick="openServiceModal()" class="btn-primary px-6 py-3 rounded-xl text-white font-semibold flex items-center gap-2 shrink-0">
         <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
         </svg> Novo Serviço </button>
       </div>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="servicesGrid">
       <div class="card rounded-2xl p-6 text-center">
        <p class="text-gray-400">Nenhum serviço cadastrado</p>
       </div>
      </div>
     </div><!-- Reports Page -->
     <div id="reportsPage" class="page hidden">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
       <div class="card rounded-2xl p-6">
        <div class="flex items-center gap-3 mb-4">
         <div class="w-10 h-10 rounded-lg bg-green-500/20 flex items-center justify-center">
          <svg class="w-5 h-5 text-green-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
         </div><span class="text-sm text-gray-400">Faturamento Diário</span>
        </div>
        <h3 class="text-2xl font-bold text-white" id="dailyRevenueReport">R$ 0</h3>
       </div>
       <div class="card rounded-2xl p-6">
        <div class="flex items-center gap-3 mb-4">
         <div class="w-10 h-10 rounded-lg bg-blue-500/20 flex items-center justify-center">
          <svg class="w-5 h-5 text-blue-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
          </svg>
         </div><span class="text-sm text-gray-400">Faturamento Mensal</span>
        </div>
        <h3 class="text-2xl font-bold text-white" id="monthlyRevenueReport">R$ 0</h3>
       </div>
       <div class="card rounded-2xl p-6">
        <div class="flex items-center gap-3 mb-4">
         <div class="w-10 h-10 rounded-lg bg-purple-500/20 flex items-center justify-center">
          <svg class="w-5 h-5 text-purple-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
          </svg>
         </div><span class="text-sm text-gray-400">Serviços Realizados</span>
        </div>
        <h3 class="text-2xl font-bold text-white" id="servicesCountReport">0</h3>
       </div>
       <div class="card rounded-2xl p-6">
        <div class="flex items-center gap-3 mb-4">
         <div class="w-10 h-10 rounded-lg bg-brand-500/20 flex items-center justify-center">
          <svg class="w-5 h-5 text-brand-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
          </svg>
         </div><span class="text-sm text-gray-400">Clientes Atendidos</span>
        </div>
        <h3 class="text-2xl font-bold text-white" id="clientsServedReport">0</h3>
       </div>
      </div>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
       <div class="card rounded-2xl p-6">
        <h3 class="text-lg font-bold text-white mb-6">Faturamento Mensal</h3>
        <div class="h-64">
         <canvas id="monthlyRevenueChart"></canvas>
        </div>
       </div>
       <div class="card rounded-2xl p-6">
        <h3 class="text-lg font-bold text-white mb-6">Serviços Mais Vendidos</h3>
        <div class="h-64">
         <canvas id="servicesChart"></canvas>
        </div>
       </div>
      </div>
     </div><!-- Settings Page -->
     <div id="settingsPage" class="page hidden">
      <div class="max-w-2xl">
       <div class="card rounded-2xl p-6 mb-6">
        <h3 class="text-lg font-bold text-white mb-6">Informações da Barbearia</h3>
        <form id="settingsForm" class="space-y-4">
         <div><label class="block text-sm font-medium text-gray-300 mb-2">Nome da Barbearia</label> <input type="text" id="settingsShopName" class="input-field w-full px-4 py-3 rounded-xl text-white" value="BarberPro">
         </div>
         <div><label class="block text-sm font-medium text-gray-300 mb-2">Endereço</label> <input type="text" id="settingsAddress" class="input-field w-full px-4 py-3 rounded-xl text-white" placeholder="Rua, número, bairro">
         </div>
         <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <div><label class="block text-sm font-medium text-gray-300 mb-2">Telefone</label> <input type="tel" id="settingsPhone" class="input-field w-full px-4 py-3 rounded-xl text-white" placeholder="(00) 00000-0000">
          </div>
          <div><label class="block text-sm font-medium text-gray-300 mb-2">Email</label> <input type="email" id="settingsEmail" class="input-field w-full px-4 py-3 rounded-xl text-white" placeholder="contato@barberpro.com">
          </div>
         </div><button type="submit" class="btn-primary px-6 py-3 rounded-xl text-white font-semibold"> Salvar Alterações </button>
        </form>
       </div>
       <div class="card rounded-2xl p-6">
        <h3 class="text-lg font-bold text-white mb-6">Horário de Funcionamento</h3>
        <div class="space-y-3" id="workingHours">
         <div class="flex items-center justify-between py-2"><span class="text-gray-300">Segunda a Sexta</span> <span class="text-white font-medium">08:00 - 20:00</span>
         </div>
         <div class="flex items-center justify-between py-2 border-t border-gray-800"><span class="text-gray-300">Sábado</span> <span class="text-white font-medium">08:00 - 18:00</span>
         </div>
         <div class="flex items-center justify-between py-2 border-t border-gray-800"><span class="text-gray-300">Domingo</span> <span class="text-red-400 font-medium">Fechado</span>
         </div>
        </div>
       </div>
      </div>
     </div>
    </main>
   </div>
  </div><!-- Modals --> <!-- Client Modal -->
  <div id="clientModal" class="fixed inset-0 z-50 hidden">
   <div class="modal-overlay absolute inset-0" onclick="closeClientModal()"></div>
   <div class="absolute inset-0 flex items-center justify-center p-4 pointer-events-none">
    <div class="card rounded-2xl p-6 w-full max-w-md pointer-events-auto fade-in">
     <div class="flex items-center justify-between mb-6">
      <h3 class="text-xl font-bold text-white" id="clientModalTitle">Novo Cliente</h3><button onclick="closeClientModal()" class="p-2 rounded-lg hover:bg-gray-700 transition-colors">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div>
     <form id="clientForm" class="space-y-4"><input type="hidden" id="clientId">
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Nome *</label> <input type="text" id="clientName" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
      </div>
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Telefone *</label> <input type="tel" id="clientPhone" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
      </div>
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Email</label> <input type="email" id="clientEmail" class="input-field w-full px-4 py-3 rounded-xl text-white">
      </div>
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Observações</label> <textarea id="clientNotes" rows="3" class="input-field w-full px-4 py-3 rounded-xl text-white resize-none"></textarea>
      </div>
      <div class="flex gap-3 pt-4"><button type="button" onclick="closeClientModal()" class="flex-1 px-4 py-3 rounded-xl border border-gray-600 text-gray-300 font-medium hover:bg-gray-800 transition-colors"> Cancelar </button> <button type="submit" id="clientSubmitBtn" class="flex-1 btn-primary px-4 py-3 rounded-xl text-white font-semibold"> Salvar </button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Service Modal -->
  <div id="serviceModal" class="fixed inset-0 z-50 hidden">
   <div class="modal-overlay absolute inset-0" onclick="closeServiceModal()"></div>
   <div class="absolute inset-0 flex items-center justify-center p-4 pointer-events-none">
    <div class="card rounded-2xl p-6 w-full max-w-md pointer-events-auto fade-in">
     <div class="flex items-center justify-between mb-6">
      <h3 class="text-xl font-bold text-white" id="serviceModalTitle">Novo Serviço</h3><button onclick="closeServiceModal()" class="p-2 rounded-lg hover:bg-gray-700 transition-colors">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div>
     <form id="serviceForm" class="space-y-4"><input type="hidden" id="serviceId">
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Nome do Serviço *</label> <input type="text" id="serviceName" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
      </div>
      <div class="grid grid-cols-2 gap-4">
       <div><label class="block text-sm font-medium text-gray-300 mb-2">Valor (R$) *</label> <input type="number" id="servicePrice" step="0.01" min="0" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
       </div>
       <div><label class="block text-sm font-medium text-gray-300 mb-2">Duração (min) *</label> <input type="number" id="serviceDuration" min="5" step="5" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
       </div>
      </div>
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Categoria</label> <select id="serviceCategory" class="input-field w-full px-4 py-3 rounded-xl text-white"> <option value="corte">Corte</option> <option value="barba">Barba</option> <option value="combo">Combo</option> <option value="tratamento">Tratamento</option> <option value="outros">Outros</option> </select>
      </div>
      <div class="flex gap-3 pt-4"><button type="button" onclick="closeServiceModal()" class="flex-1 px-4 py-3 rounded-xl border border-gray-600 text-gray-300 font-medium hover:bg-gray-800 transition-colors"> Cancelar </button> <button type="submit" id="serviceSubmitBtn" class="flex-1 btn-primary px-4 py-3 rounded-xl text-white font-semibold"> Salvar </button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Appointment Modal -->
  <div id="appointmentModal" class="fixed inset-0 z-50 hidden">
   <div class="modal-overlay absolute inset-0" onclick="closeAppointmentModal()"></div>
   <div class="absolute inset-0 flex items-center justify-center p-4 pointer-events-none">
    <div class="card rounded-2xl p-6 w-full max-w-md pointer-events-auto fade-in">
     <div class="flex items-center justify-between mb-6">
      <h3 class="text-xl font-bold text-white" id="appointmentModalTitle">Novo Agendamento</h3><button onclick="closeAppointmentModal()" class="p-2 rounded-lg hover:bg-gray-700 transition-colors">
       <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div>
     <form id="appointmentForm" class="space-y-4"><input type="hidden" id="appointmentId">
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Cliente *</label> <select id="appointmentClient" class="input-field w-full px-4 py-3 rounded-xl text-white" required> <option value="">Selecione um cliente</option> </select>
      </div>
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Serviço *</label> <select id="appointmentService" class="input-field w-full px-4 py-3 rounded-xl text-white" required> <option value="">Selecione um serviço</option> </select>
      </div>
      <div class="grid grid-cols-2 gap-4">
       <div><label class="block text-sm font-medium text-gray-300 mb-2">Data *</label> <input type="date" id="appointmentDate" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
       </div>
       <div><label class="block text-sm font-medium text-gray-300 mb-2">Horário *</label> <input type="time" id="appointmentTime" class="input-field w-full px-4 py-3 rounded-xl text-white" required>
       </div>
      </div>
      <div><label class="block text-sm font-medium text-gray-300 mb-2">Status</label> <select id="appointmentStatus" class="input-field w-full px-4 py-3 rounded-xl text-white"> <option value="scheduled">Agendado</option> <option value="completed">Concluído</option> <option value="cancelled">Cancelado</option> </select>
      </div>
      <div class="flex gap-3 pt-4"><button type="button" onclick="closeAppointmentModal()" class="flex-1 px-4 py-3 rounded-xl border border-gray-600 text-gray-300 font-medium hover:bg-gray-800 transition-colors"> Cancelar </button> <button type="submit" id="appointmentSubmitBtn" class="flex-1 btn-primary px-4 py-3 rounded-xl text-white font-semibold"> Salvar </button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Delete Confirmation Modal -->
  <div id="deleteModal" class="fixed inset-0 z-50 hidden">
   <div class="modal-overlay absolute inset-0" onclick="closeDeleteModal()"></div>
   <div class="absolute inset-0 flex items-center justify-center p-4 pointer-events-none">
    <div class="card rounded-2xl p-6 w-full max-w-sm pointer-events-auto fade-in text-center">
     <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-red-500/20 flex items-center justify-center">
      <svg class="w-8 h-8 text-red-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
      </svg>
     </div>
     <h3 class="text-xl font-bold text-white mb-2">Confirmar Exclusão</h3>
     <p class="text-gray-400 mb-6" id="deleteModalText">Tem certeza que deseja excluir este item?</p>
     <div class="flex gap-3"><button onclick="closeDeleteModal()" class="flex-1 px-4 py-3 rounded-xl border border-gray-600 text-gray-300 font-medium hover:bg-gray-800 transition-colors"> Cancelar </button> <button onclick="confirmDelete()" id="deleteConfirmBtn" class="flex-1 px-4 py-3 rounded-xl bg-red-500 hover:bg-red-600 text-white font-semibold transition-colors"> Excluir </button>
     </div>
    </div>
   </div>
  </div><!-- Toast Container -->
  <div id="toastContainer" class="fixed bottom-4 right-4 z-50 space-y-2"></div>
  <script>
    // ============================================
    // STATE MANAGEMENT
    // ============================================
    let appData = {
      clients: [],
      services: [],
      appointments: []
    };
    
    let currentPage = 'dashboard';
    let selectedDate = new Date();
    let currentMonth = new Date();
    let deleteCallback = null;
    let weeklyChart = null;
    let monthlyRevenueChart = null;
    let servicesChart = null;
    
    const defaultConfig = {
      shop_name: 'BarberPro',
      welcome_message: 'Bem-vindo de volta!'
    };
    
    let config = { ...defaultConfig };

    // ============================================
    // SDK INITIALIZATION
    // ============================================
    const dataHandler = {
      onDataChanged(data) {
        appData.clients = data.filter(d => d.type === 'client');
        appData.services = data.filter(d => d.type === 'service');
        appData.appointments = data.filter(d => d.type === 'appointment');
        
        updateDashboard();
        renderClients();
        renderServices();
        renderSchedule();
        updateReports();
        updateAppointmentSelects();
      }
    };

    async function initApp() {
      if (window.elementSdk) {
        window.elementSdk.init({
          defaultConfig,
          onConfigChange: async (newConfig) => {
            config = { ...defaultConfig, ...newConfig };
            applyConfig();
          },
          mapToCapabilities: (cfg) => ({
            recolorables: [],
            borderables: [],
            fontEditable: undefined,
            fontSizeable: undefined
          }),
          mapToEditPanelValues: (cfg) => new Map([
            ['shop_name', cfg.shop_name || defaultConfig.shop_name],
            ['welcome_message', cfg.welcome_message || defaultConfig.welcome_message]
          ])
        });
        config = { ...defaultConfig, ...window.elementSdk.config };
      }
      
      if (window.dataSdk) {
        const result = await window.dataSdk.init(dataHandler);
        if (!result.isOk) {
          console.error('Failed to initialize Data SDK');
        }
      }
      
      applyConfig();
      initCalendar();
      initCharts();
    }

    function applyConfig() {
      const shopName = config.shop_name || defaultConfig.shop_name;
      const welcomeMsg = config.welcome_message || defaultConfig.welcome_message;
      
      document.getElementById('loginShopName').textContent = shopName;
      document.getElementById('sidebarShopName').textContent = shopName;
      document.getElementById('welcomeMessage').textContent = welcomeMsg;
    }

    // ============================================
    // AUTHENTICATION
    // ============================================
    document.getElementById('loginForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const email = document.getElementById('loginEmail').value;
      const password = document.getElementById('loginPassword').value;
      
      if (email && password) {
        document.getElementById('loginScreen').classList.add('hidden');
        document.getElementById('mainApp').classList.remove('hidden');
        showToast('Login realizado com sucesso!', 'success');
      }
    });

    function logout() {
      document.getElementById('mainApp').classList.add('hidden');
      document.getElementById('loginScreen').classList.remove('hidden');
      document.getElementById('loginForm').reset();
      showToast('Você saiu do sistema', 'info');
    }

    // ============================================
    // NAVIGATION
    // ============================================
    function navigateTo(page) {
      currentPage = page;
      
      document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
      document.querySelectorAll('.sidebar-item').forEach(item => item.classList.remove('active'));
      
      const pageElement = document.getElementById(page + 'Page');
      const menuItem = document.querySelector(`[data-page="${page}"]`);
      
      if (pageElement) {
        pageElement.classList.remove('hidden');
        pageElement.classList.add('fade-in');
      }
      if (menuItem) {
        menuItem.classList.add('active');
      }
      
      const titles = {
        dashboard: 'Dashboard',
        agenda: 'Agenda',
        clients: 'Clientes',
        services: 'Serviços',
        reports: 'Relatórios',
        settings: 'Configurações'
      };
      
      document.getElementById('pageTitle').textContent = titles[page] || page;
      
      if (window.innerWidth < 1024) {
        document.getElementById('sidebar').classList.add('-translate-x-full');
      }
      
      if (page === 'reports') {
        setTimeout(() => {
          updateReportCharts();
        }, 100);
      }
    }

    function toggleSidebar() {
      const sidebar = document.getElementById('sidebar');
      sidebar.classList.toggle('-translate-x-full');
    }

    // ============================================
    // DASHBOARD
    // ============================================
    function updateDashboard() {
      const today = new Date().toISOString().split('T')[0];
      const todayAppts = appData.appointments.filter(a => a.appointment_date === today);
      const completedToday = todayAppts.filter(a => a.appointment_status === 'completed');
      
      document.getElementById('todayAppointments').textContent = todayAppts.length;
      document.getElementById('totalClients').textContent = appData.clients.length;
      
      let todayRevenue = 0;
      completedToday.forEach(appt => {
        const service = appData.services.find(s => s.service_name === appt.appointment_service);
        if (service) todayRevenue += service.service_price;
      });
      document.getElementById('todayRevenue').textContent = `R$ ${todayRevenue.toFixed(2)}`;
      
      const upcomingAppts = appData.appointments
        .filter(a => a.appointment_status === 'scheduled' && a.appointment_date >= today)
        .sort((a, b) => {
          if (a.appointment_date !== b.appointment_date) {
            return a.appointment_date.localeCompare(b.appointment_date);
          }
          return a.appointment_time.localeCompare(b.appointment_time);
        });
      
      if (upcomingAppts.length > 0) {
        document.getElementById('nextClient').textContent = upcomingAppts[0].appointment_client;
      } else {
        document.getElementById('nextClient').textContent = 'Nenhum agendamento';
      }
      
      renderUpcomingAppointments(upcomingAppts.slice(0, 5));
      renderTopServices();
      updateWeeklyChart();
    }

    function renderUpcomingAppointments(appointments) {
      const container = document.getElementById('upcomingAppointments');
      
      if (appointments.length === 0) {
        container.innerHTML = '<p class="text-gray-400 text-sm">Nenhum atendimento agendado</p>';
        return;
      }
      
      container.innerHTML = appointments.map(appt => {
        const statusColors = {
          scheduled: 'bg-blue-500',
          completed: 'bg-green-500',
          cancelled: 'bg-red-500'
        };
        
        return `
          <div class="flex items-center gap-3 p-3 rounded-xl bg-dark-950/50">
            <div class="w-2 h-2 rounded-full ${statusColors[appt.appointment_status] || 'bg-gray-500'}"></div>
            <div class="flex-1 min-w-0">
              <p class="text-white font-medium truncate">${appt.appointment_client}</p>
              <p class="text-gray-400 text-sm">${appt.appointment_service}</p>
            </div>
            <div class="text-right">
              <p class="text-brand-400 font-medium">${appt.appointment_time}</p>
              <p class="text-gray-500 text-xs">${formatDate(appt.appointment_date)}</p>
            </div>
          </div>
        `;
      }).join('');
    }

    function renderTopServices() {
      const container = document.getElementById('topServices');
      const serviceCount = {};
      
      appData.appointments.filter(a => a.appointment_status === 'completed').forEach(appt => {
        serviceCount[appt.appointment_service] = (serviceCount[appt.appointment_service] || 0) + 1;
      });
      
      const sortedServices = Object.entries(serviceCount)
        .sort((a, b) => b[1] - a[1])
        .slice(0, 4);
      
      if (sortedServices.length === 0) {
        container.innerHTML = '<p class="text-gray-400 text-sm col-span-full">Nenhum serviço realizado ainda</p>';
        return;
      }
      
      container.innerHTML = sortedServices.map(([name, count], index) => {
        const service = appData.services.find(s => s.service_name === name);
        const colors = ['from-brand-400 to-brand-600', 'from-blue-400 to-blue-600', 'from-purple-400 to-purple-600', 'from-green-400 to-green-600'];
        
        return `
          <div class="bg-dark-950/50 rounded-xl p-4">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-10 h-10 rounded-lg bg-gradient-to-br ${colors[index]} flex items-center justify-center text-white font-bold">
                ${index + 1}
              </div>
              <div class="flex-1 min-w-0">
                <p class="text-white font-medium truncate">${name}</p>
                <p class="text-gray-400 text-sm">${count} realizados</p>
              </div>
            </div>
            ${service ? `<p class="text-brand-400 font-semibold">R$ ${service.service_price.toFixed(2)}</p>` : ''}
          </div>
        `;
      }).join('');
    }

    // ============================================
    // CHARTS
    // ============================================
    function initCharts() {
      const weeklyCtx = document.getElementById('weeklyChart');
      if (weeklyCtx) {
        weeklyChart = new Chart(weeklyCtx, {
          type: 'bar',
          data: {
            labels: ['Dom', 'Seg', 'Ter', 'Qua', 'Qui', 'Sex', 'Sáb'],
            datasets: [{
              label: 'Faturamento',
              data: [0, 0, 0, 0, 0, 0, 0],
              backgroundColor: 'rgba(240, 151, 50, 0.8)',
              borderRadius: 8,
              borderSkipped: false
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
                beginAtZero: true,
                grid: { color: 'rgba(255,255,255,0.05)' },
                ticks: { color: '#9ca3af' }
              },
              x: {
                grid: { display: false },
                ticks: { color: '#9ca3af' }
              }
            }
          }
        });
      }
    }

    function updateWeeklyChart() {
      if (!weeklyChart) return;
      
      const today = new Date();
      const weekData = [0, 0, 0, 0, 0, 0, 0];
      
      for (let i = 0; i < 7; i++) {
        const date = new Date(today);
        date.setDate(today.getDate() - today.getDay() + i);
        const dateStr = date.toISOString().split('T')[0];
        
        appData.appointments
          .filter(a => a.appointment_date === dateStr && a.appointment_status === 'completed')
          .forEach(appt => {
            const service = appData.services.find(s => s.service_name === appt.appointment_service);
            if (service) weekData[i] += service.service_price;
          });
      }
      
      weeklyChart.data.datasets[0].data = weekData;
      weeklyChart.update();
    }

    function updateReportCharts() {
      const monthlyCtx = document.getElementById('monthlyRevenueChart');
      const servicesCtx = document.getElementById('servicesChart');
      
      if (monthlyCtx && !monthlyRevenueChart) {
        const monthLabels = ['Jan', 'Fev', 'Mar', 'Abr', 'Mai', 'Jun', 'Jul', 'Ago', 'Set', 'Out', 'Nov', 'Dez'];
        const monthData = new Array(12).fill(0);
        
        appData.appointments.filter(a => a.appointment_status === 'completed').forEach(appt => {
          const month = new Date(appt.appointment_date).getMonth();
          const service = appData.services.find(s => s.service_name === appt.appointment_service);
          if (service) monthData[month] += service.service_price;
        });
        
        monthlyRevenueChart = new Chart(monthlyCtx, {
          type: 'line',
          data: {
            labels: monthLabels,
            datasets: [{
              label: 'Faturamento',
              data: monthData,
              borderColor: '#f09732',
              backgroundColor: 'rgba(240, 151, 50, 0.1)',
              fill: true,
              tension: 0.4
            }]
          },
          options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: { legend: { display: false } },
            scales: {
              y: {
                beginAtZero: true,
                grid: { color: 'rgba(255,255,255,0.05)' },
                ticks: { color: '#9ca3af' }
              },
              x: {
                grid: { display: false },
                ticks: { color: '#9ca3af' }
              }
            }
          }
        });
      }
      
      if (servicesCtx && !servicesChart) {
        const serviceCount = {};
        appData.appointments.filter(a => a.appointment_status === 'completed').forEach(appt => {
          serviceCount[appt.appointment_service] = (serviceCount[appt.appointment_service] || 0) + 1;
        });
        
        const sortedServices = Object.entries(serviceCount).sort((a, b) => b[1] - a[1]).slice(0, 5);
        
        servicesChart = new Chart(servicesCtx, {
          type: 'doughnut',
          data: {
            labels: sortedServices.map(s => s[0]) || ['Nenhum serviço'],
            datasets: [{
              data: sortedServices.map(s => s[1]) || [1],
              backgroundColor: ['#f09732', '#3b82f6', '#22c55e', '#a855f7', '#ef4444']
            }]
          },
          options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
              legend: {
                position: 'bottom',
                labels: { color: '#9ca3af', padding: 20 }
              }
            }
          }
        });
      }
    }

    // ============================================
    // REPORTS
    // ============================================
    function updateReports() {
      const today = new Date();
      const todayStr = today.toISOString().split('T')[0];
      const currentMonth = today.getMonth();
      const currentYear = today.getFullYear();
      
      let dailyRevenue = 0;
      let monthlyRevenue = 0;
      let servicesCount = 0;
      const clientsServed = new Set();
      
      appData.appointments.filter(a => a.appointment_status === 'completed').forEach(appt => {
        const apptDate = new Date(appt.appointment_date);
        const service = appData.services.find(s => s.service_name === appt.appointment_service);
        
        if (appt.appointment_date === todayStr && service) {
          dailyRevenue += service.service_price;
        }
        
        if (apptDate.getMonth() === currentMonth && apptDate.getFullYear() === currentYear) {
          if (service) monthlyRevenue += service.service_price;
          servicesCount++;
          clientsServed.add(appt.appointment_client);
        }
      });
      
      document.getElementById('dailyRevenueReport').textContent = `R$ ${dailyRevenue.toFixed(2)}`;
      document.getElementById('monthlyRevenueReport').textContent = `R$ ${monthlyRevenue.toFixed(2)}`;
      document.getElementById('servicesCountReport').textContent = servicesCount;
      document.getElementById('clientsServedReport').textContent = clientsServed.size;
    }

    // ============================================
    // CALENDAR & AGENDA
    // ============================================
    function initCalendar() {
      renderCalendar();
      renderSchedule();
    }

    function renderCalendar() {
      const grid = document.getElementById('calendarGrid');
      const year = currentMonth.getFullYear();
      const month = currentMonth.getMonth();
      
      const monthNames = ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'];
      document.getElementById('currentMonth').textContent = `${monthNames[month]} ${year}`;
      
      const firstDay = new Date(year, month, 1).getDay();
      const daysInMonth = new Date(year, month + 1, 0).getDate();
      const today = new Date();
      
      let html = '';
      
      for (let i = 0; i < firstDay; i++) {
        html += '<div class="p-2"></div>';
      }
      
      for (let day = 1; day <= daysInMonth; day++) {
        const date = new Date(year, month, day);
        const dateStr = date.toISOString().split('T')[0];
        const isToday = date.toDateString() === today.toDateString();
        const isSelected = date.toDateString() === selectedDate.toDateString();
        const hasAppointment = appData.appointments.some(a => a.appointment_date === dateStr);
        
        html += `
          <button onclick="selectDate(${year}, ${month}, ${day})" 
                  class="calendar-day p-2 rounded-lg text-center relative ${isToday ? 'today' : ''} ${isSelected ? 'selected' : ''}">
            <span class="text-sm ${isSelected ? 'text-brand-400 font-bold' : 'text-gray-300'}">${day}</span>
            ${hasAppointment ? '<div class="absolute bottom-1 left-1/2 -translate-x-1/2 w-1 h-1 rounded-full bg-brand-500"></div>' : ''}
          </button>
        `;
      }
      
      grid.innerHTML = html;
    }

    function selectDate(year, month, day) {
      selectedDate = new Date(year, month, day);
      renderCalendar();
      renderSchedule();
    }

    function changeMonth(delta) {
      currentMonth.setMonth(currentMonth.getMonth() + delta);
      renderCalendar();
    }

    function renderSchedule() {
      const container = document.getElementById('scheduleView');
      const dateStr = selectedDate.toISOString().split('T')[0];
      
      const dayNames = ['Domingo', 'Segunda-feira', 'Terça-feira', 'Quarta-feira', 'Quinta-feira', 'Sexta-feira', 'Sábado'];
      document.getElementById('selectedDateTitle').textContent = dayNames[selectedDate.getDay()];
      document.getElementById('selectedDateSubtitle').textContent = formatDate(dateStr);
      
      const dayAppointments = appData.appointments
        .filter(a => a.appointment_date === dateStr)
        .sort((a, b) => a.appointment_time.localeCompare(b.appointment_time));
      
      const timeSlots = [];
      for (let hour = 8; hour < 20; hour++) {
        timeSlots.push(`${hour.toString().padStart(2, '0')}:00`);
        timeSlots.push(`${hour.toString().padStart(2, '0')}:30`);
      }
      
      container.innerHTML = timeSlots.map(time => {
        const appointment = dayAppointments.find(a => a.appointment_time === time);
        
        if (appointment) {
          const statusColors = {
            scheduled: 'border-blue-500 bg-blue-500/10',
            completed: 'border-green-500 bg-green-500/10',
            cancelled: 'border-red-500 bg-red-500/10'
          };
          const statusLabels = {
            scheduled: 'Agendado',
            completed: 'Concluído',
            cancelled: 'Cancelado'
          };
          
          return `
            <div class="time-slot booked flex items-center gap-4 p-4 rounded-xl border-l-4 ${statusColors[appointment.appointment_status]}" onclick="editAppointment('${appointment.__backendId}')">
              <span class="text-gray-400 font-mono text-sm w-14">${time}</span>
              <div class="flex-1">
                <p class="text-white font-medium">${appointment.appointment_client}</p>
                <p class="text-gray-400 text-sm">${appointment.appointment_service}</p>
              </div>
              <span class="px-3 py-1 rounded-full text-xs font-medium status-${appointment.appointment_status} text-white">
                ${statusLabels[appointment.appointment_status]}
              </span>
            </div>
          `;
        }
        
        return `
          <div class="time-slot flex items-center gap-4 p-4 rounded-xl border border-gray-800 hover:border-brand-500/50" onclick="quickAppointment('${time}')">
            <span class="text-gray-400 font-mono text-sm w-14">${time}</span>
            <span class="text-gray-500 text-sm">Horário disponível</span>
          </div>
        `;
      }).join('');
    }

    function setView(view) {
      document.getElementById('viewDayBtn').className = view === 'day' ? 'px-4 py-2 rounded-lg bg-brand-500/20 text-brand-400 font-medium text-sm' : 'px-4 py-2 rounded-lg hover:bg-gray-700 text-gray-400 font-medium text-sm transition-colors';
      document.getElementById('viewWeekBtn').className = view === 'week' ? 'px-4 py-2 rounded-lg bg-brand-500/20 text-brand-400 font-medium text-sm' : 'px-4 py-2 rounded-lg hover:bg-gray-700 text-gray-400 font-medium text-sm transition-colors';
    }

    function quickAppointment(time) {
      document.getElementById('appointmentDate').value = selectedDate.toISOString().split('T')[0];
      document.getElementById('appointmentTime').value = time;
      openAppointmentModal();
    }

    // ============================================
    // CLIENTS CRUD
    // ============================================
    function renderClients() {
      const tbody = document.getElementById('clientsTableBody');
      const searchTerm = document.getElementById('clientSearch')?.value?.toLowerCase() || '';
      
      const filteredClients = appData.clients.filter(c => 
        c.name.toLowerCase().includes(searchTerm) ||
        c.phone?.toLowerCase().includes(searchTerm) ||
        c.email?.toLowerCase().includes(searchTerm)
      );
      
      if (filteredClients.length === 0) {
        tbody.innerHTML = '<tr><td colspan="5" class="px-6 py-8 text-center text-gray-400">Nenhum cliente encontrado</td></tr>';
        return;
      }
      
      tbody.innerHTML = filteredClients.map(client => {
        const appointments = appData.appointments.filter(a => a.appointment_client === client.name).length;
        
        return `
          <tr class="table-row border-b border-gray-800/50">
            <td class="px-6 py-4">
              <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-full bg-gradient-to-br from-brand-400 to-brand-600 flex items-center justify-center text-white font-bold">
                  ${client.name.charAt(0).toUpperCase()}
                </div>
                <span class="text-white font-medium">${client.name}</span>
              </div>
            </td>
            <td class="px-6 py-4 text-gray-300">${client.phone || '-'}</td>
            <td class="px-6 py-4 text-gray-300 hidden sm:table-cell">${client.email || '-'}</td>
            <td class="px-6 py-4 text-gray-300 hidden lg:table-cell">${appointments} atendimento${appointments !== 1 ? 's' : ''}</td>
            <td class="px-6 py-4 text-right">
              <button onclick="editClient('${client.__backendId}')" class="p-2 rounded-lg hover:bg-gray-700 transition-colors text-gray-400 hover:text-white">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"/>
                </svg>
              </button>
              <button onclick="deleteClient('${client.__backendId}')" class="p-2 rounded-lg hover:bg-red-500/20 transition-colors text-gray-400 hover:text-red-400">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
                </svg>
              </button>
            </td>
          </tr>
        `;
      }).join('');
    }

    function filterClients() {
      renderClients();
    }

    function openClientModal(client = null) {
      document.getElementById('clientModal').classList.remove('hidden');
      document.getElementById('clientForm').reset();
      document.getElementById('clientId').value = '';
      document.getElementById('clientModalTitle').textContent = 'Novo Cliente';
      
      if (client) {
        document.getElementById('clientId').value = client.__backendId;
        document.getElementById('clientName').value = client.name;
        document.getElementById('clientPhone').value = client.phone || '';
        document.getElementById('clientEmail').value = client.email || '';
        document.getElementById('clientNotes').value = client.notes || '';
        document.getElementById('clientModalTitle').textContent = 'Editar Cliente';
      }
    }

    function closeClientModal() {
      document.getElementById('clientModal').classList.add('hidden');
    }

    function editClient(id) {
      const client = appData.clients.find(c => c.__backendId === id);
      if (client) openClientModal(client);
    }

    function deleteClient(id) {
      const client = appData.clients.find(c => c.__backendId === id);
      if (client) {
        document.getElementById('deleteModalText').textContent = `Tem certeza que deseja excluir o cliente "${client.name}"?`;
        deleteCallback = async () => {
          const btn = document.getElementById('deleteConfirmBtn');
          btn.disabled = true;
          btn.textContent = 'Excluindo...';
          
          const result = await window.dataSdk.delete(client);
          
          btn.disabled = false;
          btn.textContent = 'Excluir';
          
          if (result.isOk) {
            showToast('Cliente excluído com sucesso!', 'success');
          } else {
            showToast('Erro ao excluir cliente', 'error');
          }
          closeDeleteModal();
        };
        document.getElementById('deleteModal').classList.remove('hidden');
      }
    }

    document.getElementById('clientForm').addEventListener('submit', async function(e) {
      e.preventDefault();
      
      const btn = document.getElementById('clientSubmitBtn');
      btn.disabled = true;
      btn.textContent = 'Salvando...';
      
      const clientId = document.getElementById('clientId').value;
      const clientData = {
        type: 'client',
        name: document.getElementById('clientName').value,
        phone: document.getElementById('clientPhone').value,
        email: document.getElementById('clientEmail').value,
        notes: document.getElementById('clientNotes').value,
        created_at: new Date().toISOString()
      };
      
      let result;
      if (clientId) {
        const existingClient = appData.clients.find(c => c.__backendId === clientId);
        result = await window.dataSdk.update({ ...existingClient, ...clientData });
      } else {
        if (appData.clients.length + appData.services.length + appData.appointments.length >= 999) {
          showToast('Limite de registros atingido (999)', 'error');
          btn.disabled = false;
          btn.textContent = 'Salvar';
          return;
        }
        result = await window.dataSdk.create(clientData);
      }
      
      btn.disabled = false;
      btn.textContent = 'Salvar';
      
      if (result.isOk) {
        showToast(clientId ? 'Cliente atualizado!' : 'Cliente cadastrado!', 'success');
        closeClientModal();
      } else {
        showToast('Erro ao salvar cliente', 'error');
      }
    });

    // ============================================
    // SERVICES CRUD
    // ============================================
    function renderServices() {
      const grid = document.getElementById('servicesGrid');
      const searchTerm = document.getElementById('serviceSearch')?.value?.toLowerCase() || '';
      
      const filteredServices = appData.services.filter(s =>
        s.service_name.toLowerCase().includes(searchTerm) ||
        s.service_category?.toLowerCase().includes(searchTerm)
      );
      
      if (filteredServices.length === 0) {
        grid.innerHTML = '<div class="card rounded-2xl p-6 text-center col-span-full"><p class="text-gray-400">Nenhum serviço encontrado</p></div>';
        return;
      }
      
      const categoryIcons = {
        corte: '✂️',
        barba: '🧔',
        combo: '💈',
        tratamento: '💆',
        outros: '🎯'
      };
      
      grid.innerHTML = filteredServices.map(service => `
        <div class="card rounded-2xl p-6 group">
          <div class="flex items-start justify-between mb-4">
            <div class="w-12 h-12 rounded-xl bg-brand-500/20 flex items-center justify-center text-2xl">
              ${categoryIcons[service.service_category] || '💈'}
            </div>
            <div class="flex gap-1 opacity-0 group-hover:opacity-100 transition-opacity">
              <button onclick="editService('${service.__backendId}')" class="p-2 rounded-lg hover:bg-gray-700 transition-colors text-gray-400 hover:text-white">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"/>
                </svg>
              </button>
              <button onclick="deleteService('${service.__backendId}')" class="p-2 rounded-lg hover:bg-red-500/20 transition-colors text-gray-400 hover:text-red-400">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
                </svg>
              </button>
            </div>
          </div>
          <h4 class="text-lg font-bold text-white mb-2">${service.service_name}</h4>
          <div class="flex items-center gap-4 text-sm text-gray-400 mb-4">
            <span class="flex items-center gap-1">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
              </svg>
              ${service.service_duration} min
            </span>
            <span class="capitalize px-2 py-1 rounded-md bg-gray-800 text-xs">${service.service_category}</span>
          </div>
          <p class="text-2xl font-bold text-brand-400">R$ ${service.service_price.toFixed(2)}</p>
        </div>
      `).join('');
    }

    function filterServices() {
      renderServices();
    }

    function openServiceModal(service = null) {
      document.getElementById('serviceModal').classList.remove('hidden');
      document.getElementById('serviceForm').reset();
      document.getElementById('serviceId').value = '';
      document.getElementById('serviceModalTitle').textContent = 'Novo Serviço';
      
      if (service) {
        document.getElementById('serviceId').value = service.__backendId;
        document.getElementById('serviceName').value = service.service_name;
        document.getElementById('servicePrice').value = service.service_price;
        document.getElementById('serviceDuration').value = service.service_duration;
        document.getElementById('serviceCategory').value = service.service_category || 'outros';
        document.getElementById('serviceModalTitle').textContent = 'Editar Serviço';
      }
    }

    function closeServiceModal() {
      document.getElementById('serviceModal').classList.add('hidden');
    }

    function editService(id) {
      const service = appData.services.find(s => s.__backendId === id);
      if (service) openServiceModal(service);
    }

    function deleteService(id) {
      const service = appData.services.find(s => s.__backendId === id);
      if (service) {
        document.getElementById('deleteModalText').textContent = `Tem certeza que deseja excluir o serviço "${service.service_name}"?`;
        deleteCallback = async () => {
          const btn = document.getElementById('deleteConfirmBtn');
          btn.disabled = true;
          btn.textContent = 'Excluindo...';
          
          const result = await window.dataSdk.delete(service);
          
          btn.disabled = false;
          btn.textContent = 'Excluir';
          
          if (result.isOk) {
            showToast('Serviço excluído com sucesso!', 'success');
          } else {
            showToast('Erro ao excluir serviço', 'error');
          }
          closeDeleteModal();
        };
        document.getElementById('deleteModal').classList.remove('hidden');
      }
    }

    document.getElementById('serviceForm').addEventListener('submit', async function(e) {
      e.preventDefault();
      
      const btn = document.getElementById('serviceSubmitBtn');
      btn.disabled = true;
      btn.textContent = 'Salvando...';
      
      const serviceId = document.getElementById('serviceId').value;
      const serviceData = {
        type: 'service',
        service_name: document.getElementById('serviceName').value,
        service_price: parseFloat(document.getElementById('servicePrice').value),
        service_duration: parseInt(document.getElementById('serviceDuration').value),
        service_category: document.getElementById('serviceCategory').value,
        created_at: new Date().toISOString()
      };
      
      let result;
      if (serviceId) {
        const existingService = appData.services.find(s => s.__backendId === serviceId);
        result = await window.dataSdk.update({ ...existingService, ...serviceData });
      } else {
        if (appData.clients.length + appData.services.length + appData.appointments.length >= 999) {
          showToast('Limite de registros atingido (999)', 'error');
          btn.disabled = false;
          btn.textContent = 'Salvar';
          return;
        }
        result = await window.dataSdk.create(serviceData);
      }
      
      btn.disabled = false;
      btn.textContent = 'Salvar';
      
      if (result.isOk) {
        showToast(serviceId ? 'Serviço atualizado!' : 'Serviço cadastrado!', 'success');
        closeServiceModal();
      } else {
        showToast('Erro ao salvar serviço', 'error');
      }
    });

    // ============================================
    // APPOINTMENTS CRUD
    // ============================================
    function updateAppointmentSelects() {
      const clientSelect = document.getElementById('appointmentClient');
      const serviceSelect = document.getElementById('appointmentService');
      
      clientSelect.innerHTML = '<option value="">Selecione um cliente</option>' +
        appData.clients.map(c => `<option value="${c.name}">${c.name}</option>`).join('');
      
      serviceSelect.innerHTML = '<option value="">Selecione um serviço</option>' +
        appData.services.map(s => `<option value="${s.service_name}">${s.service_name} - R$ ${s.service_price.toFixed(2)}</option>`).join('');
    }

    function openAppointmentModal(appointment = null) {
      document.getElementById('appointmentModal').classList.remove('hidden');
      document.getElementById('appointmentForm').reset();
      document.getElementById('appointmentId').value = '';
      document.getElementById('appointmentModalTitle').textContent = 'Novo Agendamento';
      document.getElementById('appointmentDate').value = selectedDate.toISOString().split('T')[0];
      
      if (appointment) {
        document.getElementById('appointmentId').value = appointment.__backendId;
        document.getElementById('appointmentClient').value = appointment.appointment_client;
        document.getElementById('appointmentService').value = appointment.appointment_service;
        document.getElementById('appointmentDate').value = appointment.appointment_date;
        document.getElementById('appointmentTime').value = appointment.appointment_time;
        document.getElementById('appointmentStatus').value = appointment.appointment_status;
        document.getElementById('appointmentModalTitle').textContent = 'Editar Agendamento';
      }
    }

    function closeAppointmentModal() {
      document.getElementById('appointmentModal').classList.add('hidden');
    }

    function editAppointment(id) {
      const appointment = appData.appointments.find(a => a.__backendId === id);
      if (appointment) openAppointmentModal(appointment);
    }

    document.getElementById('appointmentForm').addEventListener('submit', async function(e) {
      e.preventDefault();
      
      const btn = document.getElementById('appointmentSubmitBtn');
      btn.disabled = true;
      btn.textContent = 'Salvando...';
      
      const appointmentId = document.getElementById('appointmentId').value;
      const appointmentData = {
        type: 'appointment',
        appointment_client: document.getElementById('appointmentClient').value,
        appointment_service: document.getElementById('appointmentService').value,
        appointment_date: document.getElementById('appointmentDate').value,
        appointment_time: document.getElementById('appointmentTime').value,
        appointment_status: document.getElementById('appointmentStatus').value,
        created_at: new Date().toISOString()
      };
      
      let result;
      if (appointmentId) {
        const existingAppointment = appData.appointments.find(a => a.__backendId === appointmentId);
        result = await window.dataSdk.update({ ...existingAppointment, ...appointmentData });
      } else {
        if (appData.clients.length + appData.services.length + appData.appointments.length >= 999) {
          showToast('Limite de registros atingido (999)', 'error');
          btn.disabled = false;
          btn.textContent = 'Salvar';
          return;
        }
        result = await window.dataSdk.create(appointmentData);
      }
      
      btn.disabled = false;
      btn.textContent = 'Salvar';
      
      if (result.isOk) {
        showToast(appointmentId ? 'Agendamento atualizado!' : 'Agendamento criado!', 'success');
        closeAppointmentModal();
      } else {
        showToast('Erro ao salvar agendamento', 'error');
      }
    });

    // ============================================
    // DELETE MODAL
    // ============================================
    function closeDeleteModal() {
      document.getElementById('deleteModal').classList.add('hidden');
      deleteCallback = null;
    }

    function confirmDelete() {
      if (deleteCallback) deleteCallback();
    }

    // ============================================
    // SETTINGS
    // ============================================
    document.getElementById('settingsForm').addEventListener('submit', function(e) {
      e.preventDefault();
      showToast('Configurações salvas com sucesso!', 'success');
    });

    // ============================================
    // UTILITIES
    // ============================================
    function formatDate(dateStr) {
      const date = new Date(dateStr + 'T00:00:00');
      return date.toLocaleDateString('pt-BR', { day: '2-digit', month: '2-digit', year: 'numeric' });
    }

    function showToast(message, type = 'info') {
      const container = document.getElementById('toastContainer');
      const toast = document.createElement('div');
      
      const colors = {
        success: 'bg-green-500',
        error: 'bg-red-500',
        info: 'bg-blue-500',
        warning: 'bg-yellow-500'
      };
      
      toast.className = `toast flex items-center gap-3 px-4 py-3 rounded-xl ${colors[type]} text-white shadow-lg`;
      toast.innerHTML = `
        <span>${message}</span>
        <button onclick="this.parentElement.remove()" class="ml-2 opacity-70 hover:opacity-100">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
      `;
      
      container.appendChild(toast);
      
      setTimeout(() => {
        toast.remove();
      }, 4000);
    }

    // Initialize app
    initApp();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9d8bdb8d11e7f203',t:'MTc3MjkxMDE3OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
