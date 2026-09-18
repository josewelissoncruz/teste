```Ruby

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>RetiraJá | Solicitações de Retirada</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --primary: #2563eb;
      --primary-dark: #1d4ed8;
      --sidebar: #111827;
      --background: #f4f6fa;
      --card: #ffffff;
      --text: #172033;
      --muted: #6b7280;
      --border: #e5e7eb;

      --green: #16a34a;
      --green-bg: #dcfce7;

      --orange: #d97706;
      --orange-bg: #fef3c7;

      --blue: #2563eb;
      --blue-bg: #dbeafe;

      --red: #dc2626;
      --red-bg: #fee2e2;

      --purple: #7c3aed;
      --purple-bg: #ede9fe;
    }

    body {
      font-family: Inter, Arial, sans-serif;
      background: var(--background);
      color: var(--text);
    }

    button,
    input,
    select,
    textarea {
      font-family: inherit;
    }

    button {
      cursor: pointer;
    }

    /* =========================
        LAYOUT
    ========================= */

    .app {
      display: flex;
      min-height: 100vh;
    }

    /* =========================
        SIDEBAR
    ========================= */

    .sidebar {
      width: 250px;
      min-width: 250px;
      background: var(--sidebar);
      color: white;
      padding: 24px 16px;

      display: flex;
      flex-direction: column;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 10px 35px;
    }

    .logo-icon {
      width: 42px;
      height: 42px;

      display: flex;
      align-items: center;
      justify-content: center;

      border-radius: 10px;

      background: var(--primary);

      font-size: 20px;
      font-weight: 800;
    }

    .logo-text strong {
      display: block;
      font-size: 17px;
    }

    .logo-text span {
      display: block;
      margin-top: 2px;

      color: #9ca3af;
      font-size: 11px;
    }

    .navigation {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }

    .menu-item {
      color: #9ca3af;
      text-decoration: none;

      padding: 12px;

      border-radius: 8px;

      display: flex;
      align-items: center;
      gap: 12px;

      font-size: 14px;

      transition: .2s;
    }

    .menu-item:hover {
      color: white;
      background: #1f2937;
    }

    .menu-item.active {
      color: white;
      background: var(--primary);
    }

    .menu-icon {
      width: 20px;
      text-align: center;
    }

    .sidebar-bottom {
      margin-top: auto;
    }

    .user {
      margin-top: 20px;
      padding: 18px 8px 5px;

      border-top: 1px solid #273244;

      display: flex;
      align-items: center;
      gap: 10px;
    }

    .avatar {
      width: 36px;
      height: 36px;

      border-radius: 50%;

      background: #334155;

      display: flex;
      align-items: center;
      justify-content: center;

      font-size: 11px;
      font-weight: 700;
    }

    .user strong {
      display: block;
      font-size: 13px;
    }

    .user small {
      display: block;
      margin-top: 2px;

      color: #9ca3af;
      font-size: 11px;
    }

    /* =========================
        MAIN
    ========================= */

    .main {
      flex: 1;
      min-width: 0;
      padding: 32px 40px;
    }

    .header {
      display: flex;
      align-items: center;
      justify-content: space-between;

      margin-bottom: 28px;
    }

    .header h1 {
      font-size: 27px;
      letter-spacing: -.5px;
    }

    .header p {
      margin-top: 5px;
      color: var(--muted);
      font-size: 14px;
    }

    /* =========================
        BUTTONS
    ========================= */

    .primary-button {
      border: none;
      border-radius: 8px;

      padding: 11px 18px;

      background: var(--primary);
      color: white;

      font-size: 14px;
      font-weight: 600;

      transition: .2s;
    }

    .primary-button:hover {
      background: var(--primary-dark);
    }

    .secondary-button {
      border: 1px solid var(--border);
      border-radius: 8px;

      padding: 10px 18px;

      background: white;
      color: var(--text);

      font-size: 14px;
    }

    .secondary-button:hover {
      background: #f8fafc;
    }

    .danger-button {
      border: none;
      border-radius: 8px;
      padding: 10px 18px;
      background: var(--red);
      color: white;
      font-size: 14px;
      font-weight: 600;
      transition: .2s;
    }
    .danger-button:hover {
      background: #b91c1c;
    }

    /* =========================
        CARDS
    ========================= */

    .stats {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 18px;

      margin-bottom: 24px;
    }

    .stat-card {
      padding: 20px;

      background: var(--card);

      border: 1px solid var(--border);
      border-radius: 12px;

      display: flex;
      align-items: center;
      gap: 15px;
    }

    .stat-icon {
      width: 46px;
      height: 46px;

      flex-shrink: 0;

      border-radius: 10px;

      display: flex;
      align-items: center;
      justify-content: center;

      font-size: 19px;
    }

    .stat-icon.blue {
      background: var(--blue-bg);
    }

    .stat-icon.orange {
      background: var(--orange-bg);
    }

    .stat-icon.purple {
      background: var(--purple-bg);
    }

    .stat-icon.green {
      background: var(--green-bg);
    }

    .stat-card span {
      display: block;

      margin-bottom: 4px;

      color: var(--muted);

      font-size: 12px;
    }

    .stat-card strong {
      font-size: 23px;
    }

    /* =========================
        CONTENT CARD
    ========================= */

    .content-card {
      overflow: hidden;

      background: white;

      border: 1px solid var(--border);
      border-radius: 12px;
    }

    .content-header {
      padding: 22px 24px;

      display: flex;
      align-items: center;
      justify-content: space-between;

      border-bottom: 1px solid var(--border);
    }

    .content-header h2 {
      font-size: 17px;
    }

    .results {
      display: block;

      margin-top: 4px;

      color: var(--muted);

      font-size: 12px;
    }

    .filters {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .search {
      width: 280px;
      height: 40px;

      padding: 0 11px;

      display: flex;
      align-items: center;

      border: 1px solid var(--border);
      border-radius: 8px;

      color: var(--muted);
    }

    .search input {
      width: 100%;

      padding: 0 8px;

      border: none;
      outline: none;

      font-size: 13px;
    }

    select, input[type="text"], input[type="date"], textarea {
      height: 40px;
      padding: 0 12px;
      border: 1px solid var(--border);
      border-radius: 8px;
      background: white;
      color: #4b5563;
      outline: none;
      font-size: 13px;
    }

    textarea {
      height: auto;
      padding: 10px 12px;
      resize: vertical;
    }

    /* =========================
        TABLE
    ========================= */

    .table-container {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
    }

    thead {
      background: #f9fafb;
    }

    th {
      padding: 13px 20px;
      text-align: left;
      color: #9ca3af;
      font-size: 10px;
      font-weight: 700;
      letter-spacing: .5px;
      white-space: nowrap;
    }

    td {
      padding: 16px 20px;
      border-top: 1px solid #f0f1f3;
      font-size: 13px;
      white-space: nowrap;
    }

    tbody tr {
      transition: .15s;
    }

    tbody tr:hover {
      background: #fafbfc;
    }

    .protocol {
      color: var(--primary);
      font-weight: 700;
    }

    .client {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .client-avatar {
      width: 34px;
      height: 34px;
      flex-shrink: 0;
      border-radius: 50%;
      background: #eff6ff;
      color: var(--primary);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 10px;
      font-weight: 700;
    }

    .client-name {
      display: block;
      font-weight: 600;
    }

    .client-document {
      display: block;
      margin-top: 2px;
      color: var(--muted);
      font-size: 10px;
    }

    .material {
      font-weight: 500;
    }

    .quantity {
      font-weight: 600;
    }

    /* =========================
        STATUS
    ========================= */

    .status {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 6px 10px;
      border-radius: 20px;
      font-size: 11px;
      font-weight: 600;
    }

    .status::before {
      content: "";
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: currentColor;
    }

    .status.aguardando {
      color: var(--orange);
      background: var(--orange-bg);
    }

    .status.transporte {
      color: var(--blue);
      background: var(--blue-bg);
    }

    .status.concluida {
      color: var(--green);
      background: var(--green-bg);
    }

    .status.cancelada {
      color: var(--red);
      background: var(--red-bg);
    }

    /* =========================
        ACTION
    ========================= */

    .action-button {
      width: 32px;
      height: 32px;
      border: 1px solid var(--border);
      border-radius: 7px;
      background: white;
      color: #64748b;
      font-size: 18px;
    }

    .action-button:hover {
      border-color: #bfdbfe;
      background: #eff6ff;
      color: var(--primary);
    }

    /* =========================
        EMPTY STATE
    ========================= */

    .empty-state {
      display: none;
      padding: 70px 20px;
      text-align: center;
      color: var(--muted);
    }

    .empty-state .empty-icon {
      margin-bottom: 12px;
      font-size: 42px;
    }

    .empty-state strong {
      display: block;
      margin-bottom: 5px;
      color: var(--text);
      font-size: 15px;
    }

    .empty-state span {
      font-size: 13px;
    }

    /* =========================
        MODAL
    ========================= */

    .modal-overlay {
      position: fixed;
      inset: 0;
      z-index: 1000;
      padding: 20px;
      background: rgba(15, 23, 42, .55);
      display: none;
      align-items: center;
      justify-content: center;
    }

    .modal-overlay.show {
      display: flex;
    }

    .modal {
      width: 100%;
      max-width: 650px;
      max-height: 90vh;
      overflow-y: auto;
      border-radius: 14px;
      background: white;
      box-shadow: 0 20px 60px rgba(0,0,0,.2);
      animation: modalIn .2s ease;
    }

    @keyframes modalIn {
      from {
        opacity: 0;
        transform: translateY(12px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .modal-header {
      padding: 24px;
      border-bottom: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
    }

    .modal-label {
      color: var(--primary);
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 1px;
    }

    .modal-header h2 {
      margin-top: 5px;
      font-size: 20px;
    }

    .close-button {
      width: 32px;
      height: 32px;
      border: none;
      border-radius: 7px;
      background: #f1f5f9;
      color: #64748b;
      font-size: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .modal-body {
      padding: 24px;
    }

    .detail-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    .detail span {
      display: block;
      margin-bottom: 5px;
      color: var(--muted);
      font-size: 11px;
    }

    .detail strong {
      font-size: 14px;
    }

    .observation {
      margin-top: 24px;
      padding: 15px;
      border-radius: 8px;
      background: #f8fafc;
    }

    .observation span {
      display: block;
      margin-bottom: 5px;
      color: var(--muted);
      font-size: 11px;
    }

    .observation p {
      color: #475569;
      font-size: 13px;
      line-height: 1.5;
    }

    .form-group {
      margin-bottom: 16px;
    }

    .form-group label {
      display: block;
      margin-bottom: 6px;
      font-size: 12px;
      font-weight: 600;
      color: var(--text);
    }

    .form-group input,
    .form-group select,
    .form-group textarea {
      width: 100%;
    }

    .modal-footer {
      padding: 18px 24px;
      border-top: 1px solid var(--border);
      display: flex;
      justify-content: flex-end;
      gap: 10px;
    }

    /* =========================
        TOAST
    ========================= */

    .toast {
      position: fixed;
      right: 25px;
      bottom: 25px;
      z-index: 2000;
      padding: 14px 18px;
      border-radius: 9px;
      background: #111827;
      color: white;
      font-size: 13px;
      box-shadow: 0 10px 30px rgba(0,0,0,.2);
      opacity: 0;
      transform: translateY(15px);
      pointer-events: none;
      transition: .25s;
    }

    .toast.show {
      opacity: 1;
      transform: translateY(0);
    }

    /* =========================
        RESPONSIVE
    ========================= */

    @media (max-width: 1200px) {
      .stats {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    @media (max-width: 900px) {
      .sidebar {
        width: 72px;
        min-width: 72px;
        padding: 20px 10px;
      }
      .logo {
        justify-content: center;
        padding: 0 0 30px;
      }
      .logo-text {
        display: none;
      }
      .menu-item {
        justify-content: center;
        padding: 13px 8px;
      }
      .menu-text {
        display: none;
      }
      .user {
        justify-content: center;
      }
      .user-info {
        display: none;
      }
      .main {
        padding: 25px 20px;
      }
    }

    @media (max-width: 700px) {
      .header {
        align-items: flex-start;
        flex-direction: column;
        gap: 15px;
      }
      .stats {
        grid-template-columns: 1fr;
      }
      .content-header {
        align-items: flex-start;
        flex-direction: column;
        gap: 15px;
      }
      .filters {
        width: 100%;
        flex-direction: column;
      }
      .search {
        width: 100%;
      }
      select {
        width: 100%;
      }
      .detail-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>

<body>
  <div class="app">
    <!-- SIDEBAR -->
    <aside class="sidebar">
      <div class="logo">
        <div class="logo-icon">R</div>
        <div class="logo-text">
          <strong>RetiraJá</strong>
          <span>Gestão de Logística</span>
        </div>
      </div>

      <nav class="navigation">
        <a href="#" class="menu-item active" data-section="solicitacoes">
          <span class="menu-icon">▣</span>
          <span class="menu-text">Solicitações</span>
        </a>
        <a href="#" class="menu-item" data-section="clientes">
          <span class="menu-icon">�</span>
          <span class="menu-text">Clientes</span>
        </a>
        <a href="#" class="menu-item" data-section="retiradas">
          <span class="menu-icon">�</span>
          <span class="menu-text">Retiradas</span>
        </a>
        <a href="#" class="menu-item" data-section="materiais">
          <span class="menu-icon">�</span>
          <span class="menu-text">Materiais</span>
        </a>
        <a href="#" class="menu-item" data-section="relatorios">
          <span class="menu-icon">�</span>
          <span class="menu-text">Relatórios</span>
        </a>
      </nav>

      <div class="sidebar-bottom">
        <a href="#" class="menu-item" data-section="configuracoes">
          <span class="menu-icon">⚙</span>
          <span class="menu-text">Configurações</span>
        </a>
        <div class="user">
          <div class="avatar">JS</div>
          <div class="user-info">
            <strong>João Silva</strong>
            <small>Administrador</small>
          </div>
        </div>
      </div>
    </aside>

    <!-- MAIN -->
    <main class="main">
      <header class="header">
        <div>
          <h1 id="sectionTitle">Solicitações de retirada</h1>
          <p id="sectionSubtitle">Gerencie as solicitações de retirada de materiais dos clientes.</p>
        </div>
        <button class="primary-button" id="newRequestButton">
          + Nova solicitação
        </button>
      </header>

      <!-- INDICADORES -->
      <section class="stats" id="statsContainer">
        <div class="stat-card">
          <div class="stat-icon blue">�</div>
          <div>
            <span>Total de solicitações</span>
            <strong id="totalRequests">0</strong>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon orange">⏳</div>
          <div>
            <span>Aguardando retirada</span>
            <strong id="pendingRequests">0</strong>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon purple">�</div>
          <div>
            <span>Em transporte</span>
            <strong id="transportRequests">0</strong>
          </div>
        </div>

        <div class="stat-card">
          <div class="stat-icon green">✓</div>
          <div>
            <span>Concluídas</span>
            <strong id="completedRequests">0</strong>
          </div>
        </div>
      </section>

      <!-- CONTEÚDO DINÂMICO -->
      <section class="content-card" id="mainContentCard">
        <div class="content-header">
          <div>
            <h2 id="tableCardTitle">Solicitações de retirada</h2>
            <span class="results" id="resultsCount">0 solicitações</span>
          </div>

          <div class="filters" id="tableFilters">
            <div class="search">
              <span>⌕</span>
              <input type="text" id="searchInput" placeholder="Buscar cliente, protocolo ou material...">
            </div>

            <select id="statusFilter">
              <option value="todos">Todos os status</option>
              <option value="aguardando">Aguardando retirada</option>
              <option value="transporte">Em transporte</option>
              <option value="concluida">Concluída</option>
              <option value="cancelada">Cancelada</option>
            </select>
          </div>
        </div>

        <div class="table-container" id="tableContainerWrapper">
          <table>
            <thead>
              <tr>
                <th>PROTOCOLO</th>
                <th>CLIENTE</th>
                <th>MATERIAL</th>
                <th>QUANTIDADE</th>
                <th>SOLICITAÇÃO</th>
                <th>RETIRADA</th>
                <th>STATUS</th>
                <th></th>
              </tr>
            </thead>
            <tbody id="requestsTable"></tbody>
          </table>

          <div class="empty-state" id="emptyState">
            <div class="empty-icon">�</div>
            <strong>Nenhuma solicitação encontrada</strong>
            <span>Tente alterar os filtros ou realizar uma nova busca.</span>
          </div>
        </div>
      </section>
    </main>
  </div>

  <!-- MODAL DE DETALHES / EDIÇÃO / CRIAÇÃO -->
  <div class="modal-overlay" id="modal">
    <div class="modal">
      <div class="modal-header">
        <div>
          <span class="modal-label" id="modalLabelTag">DETALHES DA SOLICITAÇÃO</span>
          <h2 id="modalTitle">Solicitação</h2>
        </div>
        <button class="close-button" id="closeModal">×</button>
      </div>

      <div class="modal-body" id="modalBodyContent">
        <!-- Preenchido via JS -->
      </div>

      <div class="modal-footer" id="modalFooterContent">
        <button class="secondary-button" id="closeModalButton">Fechar</button>
        <button class="primary-button" id="editRequestButton">Editar solicitação</button>
      </div>
    </div>
  </div>

  <!-- TOAST -->
  <div class="toast" id="toast">Ação realizada com sucesso!</div>

  <!-- JAVASCRIPT LOGIC -->
  <script>
    let requests = [
      {
        id: 1,
        protocol: "RET-2026-00125",
        client: "Metalúrgica São Paulo",
        document: "CNPJ: 12.345.678/0001-90",
        material: "Sucata metálica",
        quantity: "2.450 kg",
        requestDate: "16/09/2026",
        pickupDate: "19/09/2026",
        status: "aguardando",
        address: "Av. Industrial, 1250 - Distrito Industrial",
        observation: "Material separado e disponível para retirada."
      },
      {
        id: 2,
        protocol: "RET-2026-00124",
        client: "Construtora Horizonte",
        document: "CNPJ: 23.456.789/0001-81",
        material: "Resíduos de construção",
        quantity: "8.200 kg",
        requestDate: "16/09/2026",
        pickupDate: "18/09/2026",
        status: "transporte",
        address: "Rua das Palmeiras, 450 - Centro",
        observation: "Motorista já foi direcionado para a coleta."
      },
      {
        id: 3,
        protocol: "RET-2026-00123",
        client: "Indústria Nova Era",
        document: "CNPJ: 34.567.890/0001-72",
        material: "Papelão",
        quantity: "1.800 kg",
        requestDate: "15/09/2026",
        pickupDate: "17/09/2026",
        status: "concluida",
        address: "Rod. BR-364, Km 12 - Zona Industrial",
        observation: "Retirada realizada com sucesso."
      },
      {
        id: 4,
        protocol: "RET-2026-00122",
        client: "Supermercado Central",
        document: "CNPJ: 45.678.901/0001-63",
        material: "Plástico reciclável",
        quantity: "950 kg",
        requestDate: "15/09/2026",
        pickupDate: "20/09/2026",
        status: "aguardando",
        address: "Av. Central, 850 - Centro",
        observation: "Coleta programada para o período da manhã."
      },
      {
        id: 5,
        protocol: "RET-2026-00121",
        client: "Agropecuária Boa Safra",
        document: "CNPJ: 56.789.012/0001-54",
        material: "Embalagens",
        quantity: "620 kg",
        requestDate: "14/09/2026",
        pickupDate: "16/09/2026",
        status: "concluida",
        address: "Rua do Comércio, 780 - Setor Agropecuário",
        observation: "Material coletado e conferido."
      },
      {
        id: 6,
        protocol: "RET-2026-00120",
        client: "Distribuidora Alfa",
        document: "CNPJ: 67.890.123/0001-45",
        material: "Pallets de madeira",
        quantity: "320 un.",
        requestDate: "14/09/2026",
        pickupDate: "21/09/2026",
        status: "aguardando",
        address: "Rua A, 340 - Distrito Industrial",
        observation: "Cliente solicitou veículo com capacidade para pallets."
      },
      {
        id: 7,
        protocol: "RET-2026-00119",
        client: "Fábrica Brasil",
        document: "CNPJ: 78.901.234/0001-36",
        material: "Sucata eletrônica",
        quantity: "410 kg",
        requestDate: "13/09/2026",
        pickupDate: "17/09/2026",
        status: "cancelada",
        address: "Av. Brasil, 1900 - Zona Industrial",
        observation: "Solicitação cancelada pelo cliente."
      },
      {
        id: 8,
        protocol: "RET-2026-00118",
        client: "Comercial União",
        document: "CNPJ: 89.012.345/0001-27",
        material: "Papel e papelão",
        quantity: "1.250 kg",
        requestDate: "12/09/2026",
        pickupDate: "19/09/2026",
        status: "aguardando",
        address: "Rua Goiás, 520 - Centro",
        observation: "Material acondicionado e pronto para coleta."
      }
    ];

    const table = document.getElementById("requestsTable");
    const searchInput = document.getElementById("searchInput");
    const statusFilter = document.getElementById("statusFilter");
    const resultsCount = document.getElementById("resultsCount");
    const emptyState = document.getElementById("emptyState");
    const totalRequests = document.getElementById("totalRequests");
    const pendingRequests = document.getElementById("pendingRequests");
    const transportRequests = document.getElementById("transportRequests");
    const completedRequests = document.getElementById("completedRequests");
    
    const modal = document.getElementById("modal");
    const closeModalBtn = document.getElementById("closeModal");
    const modalLabelTag = document.getElementById("modalLabelTag");
    const modalTitle = document.getElementById("modalTitle");
    const modalBodyContent = document.getElementById("modalBodyContent");
    const modalFooterContent = document.getElementById("modalFooterContent");
    const toast = document.getElementById("toast");
    const newRequestButton = document.getElementById("newRequestButton");

    let currentActiveId = null;
    let modalMode = "view"; // "view", "edit", "create"
    let currentSection = "solicitacoes";

    function getStatusLabel(status) {
      const labels = {
        aguardando: "Aguardando retirada",
        transporte: "Em transporte",
        concluida: "Concluída",
        cancelada: "Cancelada"
      };
      return labels[status] || status;
    }

    function getInitials(name) {
      if (!name) return "EX";
      const words = name.split(" ").filter(word => word.length > 2);
      if (words.length === 0) return name.substring(0, 2).toUpperCase();
      if (words.length === 1) return words[0].substring(0, 2).toUpperCase();
      return (words[0][0] + words[words.length - 1][0]).toUpperCase();
    }

    function showToast(message) {
      toast.textContent = message;
      toast.classList.add("show");
      setTimeout(() => {
        toast.classList.remove("show");
      }, 3000);
    }

    function updateStats() {
      totalRequests.textContent = requests.length;
      pendingRequests.textContent = requests.filter(item => item.status === "aguardando").length;
      transportRequests.textContent = requests.filter(item => item.status === "transporte").length;
      completedRequests.textContent = requests.filter(item => item.status === "concluida").length;
    }

    function renderRequests() {
      if (currentSection !== "solicitacoes" && currentSection !== "retiradas") {
        return; // Only table view active for these sections in this mockup
      }

      const search = searchInput.value.toLowerCase().trim();
      const selectedStatus = statusFilter.value;

      const filtered = requests.filter(request => {
        const matchesSearch =
          request.client.toLowerCase().includes(search) ||
          request.protocol.toLowerCase().includes(search) ||
          request.material.toLowerCase().includes(search);

        const matchesStatus = selectedStatus === "todos" || request.status === selectedStatus;
        return matchesSearch && matchesStatus;
      });

      table.innerHTML = "";

      filtered.forEach(request => {
        const row = document.createElement("tr");
        row.innerHTML = `
          <td><span class="protocol">${request.protocol}</span></td>
          <td>
            <div class="client">
              <div class="client-avatar">${getInitials(request.client)}</div>
              <div>
                <span class="client-name">${request.client}</span>
                <span class="client-document">${request.document}</span>
              </div>
            </div>
          </td>
          <td><span class="material">${request.material}</span></td>
          <td><span class="quantity">${request.quantity}</span></td>
          <td>${request.requestDate}</td>
          <td>${request.pickupDate}</td>
          <td><span class="status ${request.status}">${getStatusLabel(request.status)}</span></td>
          <td>
            <button class="action-button" data-id="${request.id}" title="Ver detalhes">⋮</button>
          </td>
        `;
        table.appendChild(row);
      });

      resultsCount.textContent = `${filtered.length} ${filtered.length === 1 ? "solicitação" : "solicitações"}`;
      emptyState.style.display = filtered.length === 0 ? "block" : "none";

      document.querySelectorAll(".action-button").forEach(button => {
        button.addEventListener("click", function () {
          const id = Number(this.dataset.id);
          openDetails(id);
        });
      });

      updateStats();
    }

    function closeModal() {
      modal.classList.remove("show");
    }

    function openDetails(id) {
      currentActiveId = id;
      modalMode = "view";
      const req = requests.find(r => r.id === id);
      if (!req) return;

      modalLabelTag.textContent = "DETALHES DA SOLICITAÇÃO";
      modalTitle.textContent = req.protocol;

      modalBodyContent.innerHTML = `
        <div class="detail-grid">
          <div class="detail">
            <span>Cliente</span>
            <strong>${req.client}</strong>
          </div>
          <div class="detail">
            <span>Protocolo</span>
            <strong>${req.protocol}</strong>
          </div>
          <div class="detail">
            <span>Material</span>
            <strong>${req.material}</strong>
          </div>
          <div class="detail">
            <span>Quantidade</span>
            <strong>${req.quantity}</strong>
          </div>
          <div class="detail">
            <span>Endereço de retirada</span>
            <strong>${req.address}</strong>
          </div>
          <div class="detail">
            <span>Data prevista</span>
            <strong>${req.pickupDate}</strong>
          </div>
          <div class="detail">
            <span>Status atual</span>
            <strong><span class="status ${req.status}">${getStatusLabel(req.status)}</span></strong>
          </div>
        </div>
        <div class="observation">
          <span>Observações</span>
          <p>${req.observation || "Nenhuma observação registrada."}</p>
        </div>
      `;

      modalFooterContent.innerHTML = `
        <button class="danger-button" id="deleteRequestBtn">Excluir</button>
        <button class="secondary-button" id="closeModalButton">Fechar</button>
        <button class="primary-button" id="editRequestButton">Editar solicitação</button>
      `;

      document.getElementById("deleteRequestBtn").addEventListener("click", () => deleteRequest(id));
      document.getElementById("closeModalButton").addEventListener("click", closeModal);
      document.getElementById("editRequestButton").addEventListener("click", () => openEditForm(id));

      modal.classList.add("show");
    }

    function openEditForm(id) {
      modalMode = "edit";
      currentActiveId = id;
      const req = requests.find(r => r.id === id);
      if (!req) return;

      modalLabelTag.textContent = "EDITAR SOLICITAÇÃO";
      modalTitle.textContent = `Editar ${req.protocol}`;

      modalBodyContent.innerHTML = `
        <form id="editForm" onsubmit="handleEditSubmit(event, ${id})">
          <div class="form-group">
            <label>Cliente</label>
            <input type="text" id="editClient" value="${req.client}" required>
          </div>
          <div class="form-group">
            <label>CNPJ / Documento</label>
            <input type="text" id="editDocument" value="${req.document}" required>
          </div>
          <div class="form-group">
            <label>Material</label>
            <input type="text" id="editMaterial" value="${req.material}" required>
          </div>
          <div class="form-group">
            <label>Quantidade</label>
            <input type="text" id="editQuantity" value="${req.quantity}" required>
          </div>
          <div class="form-group">
            <label>Status</label>
            <select id="editStatus">
              <option value="aguardando" ${req.status === 'aguardando' ? 'selected' : ''}>Aguardando retirada</option>
              <option value="transporte" ${req.status === 'transporte' ? 'selected' : ''}>Em transporte</option>
              <option value="concluida" ${req.status === 'concluida' ? 'selected' : ''}>Concluída</option>
              <option value="cancelada" ${req.status === 'cancelada' ? 'selected' : ''}>Cancelada</option>
            </select>
          </div>
          <div class="form-group">
            <label>Endereço de Retirada</label>
            <input type="text" id="editAddress" value="${req.address}" required>
          </div>
          <div class="form-group">
            <label>Data Prevista</label>
            <input type="text" id="editPickupDate" value="${req.pickupDate}" required>
          </div>
          <div class="form-group">
            <label>Observações</label>
            <textarea id="editObservation" rows="3">${req.observation || ""}</textarea>
          </div>
        </form>
      `;

      modalFooterContent.innerHTML = `
        <button class="secondary-button" id="closeModalButton">Cancelar</button>
        <button class="primary-button" form="editForm" type="submit">Salvar alterações</button>
      `;

      document.getElementById("closeModalButton").addEventListener("click", closeModal);
    }

    function handleEditSubmit(event, id) {
      event.preventDefault();
      const reqIndex = requests.findIndex(r => r.id === id);
      if (reqIndex === -1) return;

      requests[reqIndex] = {
        ...requests[reqIndex],
        client: document.getElementById("editClient").value,
        document: document.getElementById("editDocument").value,
        material: document.getElementById("editMaterial").value,
        quantity: document.getElementById("editQuantity").value,
        status: document.getElementById("editStatus").value,
        address: document.getElementById("editAddress").value,
        pickupDate: document.getElementById("editPickupDate").value,
        observation: document.getElementById("editObservation").value
      };

      closeModal();
      renderRequests();
      showToast("Solicitação atualizada com sucesso!");
    }

    function openCreateForm() {
      modalMode = "create";
      modalLabelTag.textContent = "NOVA SOLICITAÇÃO";
      modalTitle.textContent = "Cadastrar Retirada";

      const today = new Date();
      const reqDateStr = String(today.getDate()).padStart(2, '0') + '/' + String(today.getMonth() + 1).padStart(2, '0') + '/' + today.getFullYear();

      modalBodyContent.innerHTML = `
        <form id="createForm" onsubmit="handleCreateSubmit(event)">
          <div class="form-group">
            <label>Cliente</label>
            <input type="text" id="createClient" placeholder="Ex: Indústria XYZ" required>
          </div>
          <div class="form-group">
            <label>CNPJ / Documento</label>
            <input type="text" id="createDocument" placeholder="Ex: CNPJ: 11.222.333/0001-44" required>
          </div>
          <div class="form-group">
            <label>Material</label>
            <input type="text" id="createMaterial" placeholder="Ex: Papelão e plástico" required>
          </div>
          <div class="form-group">
            <label>Quantidade</label>
            <input type="text" id="createQuantity" placeholder="Ex: 500 kg" required>
          </div>
          <div class="form-group">
            <label>Endereço de Retirada</label>
            <input type="text" id="createAddress" placeholder="Ex: Rua das Indústrias, 100" required>
          </div>
          <div class="form-group">
            <label>Data Prevista</label>
            <input type="text" id="createPickupDate" placeholder="Ex: 25/09/2026" required>
          </div>
          <div class="form-group">
            <label>Observações</label>
            <textarea id="createObservation" rows="3" placeholder="Informações adicionais para o motorista..."></textarea>
          </div>
        </form>
      `;

      modalFooterContent.innerHTML = `
        <button class="secondary-button" id="closeModalButton">Cancelar</button>
        <button class="primary-button" form="createForm" type="submit">Cadastrar solicitação</button>
      `;

      document.getElementById("closeModalButton").addEventListener("click", closeModal);
      modal.classList.add("show");
    }

    function handleCreateSubmit(event) {
      event.preventDefault();
      const newId = requests.length > 0 ? Math.max(...requests.map(r => r.id)) + 1 : 1;
      const randomSeq = String(Math.floor(100 + Math.random() * 900));

      const today = new Date();
      const reqDateStr = String(today.getDate()).padStart(2, '0') + '/' + String(today.getMonth() + 1).padStart(2, '0') + '/' + today.getFullYear();

      const newReq = {
        id: newId,
        protocol: `RET-2026-00${125 + newId}`,
        client: document.getElementById("createClient").value,
        document: document.getElementById("createDocument").value,
        material: document.getElementById("createMaterial").value,
        quantity: document.getElementById("createQuantity").value,
        requestDate: reqDateStr,
        pickupDate: document.getElementById("createPickupDate").value,
        status: "aguardando",
        address: document.getElementById("createAddress").value,
        observation: document.getElementById("createObservation").value
      };

      requests.unshift(newReq);
      closeModal();
      renderRequests();
      showToast("Nova solicitação cadastrada com sucesso!");
    }

    function deleteRequest(id) {
      if (confirm("Tem certeza que deseja excluir esta solicitação?")) {
        requests = requests.filter(r => r.id !== id);
        closeModal();
        renderRequests();
        showToast("Solicitação excluída com sucesso!");
      }
    }

    searchInput.addEventListener("input", renderRequests);
    statusFilter.addEventListener("change", renderRequests);
    closeModalBtn.addEventListener("click", closeModal);
    newRequestButton.addEventListener("click", openCreateForm);

    modal.addEventListener("click", (e) => {
      if (e.target === modal) closeModal();
    });

    // Simulated Navigation between sidebar items
    const menuItems = document.querySelectorAll(".menu-item[data-section]");
    const sectionTitle = document.getElementById("sectionTitle");
    const sectionSubtitle = document.getElementById("sectionSubtitle");
    const mainContentCard = document.getElementById("mainContentCard");
    const statsContainer = document.getElementById("statsContainer");

    menuItems.forEach(item => {
      item.addEventListener("click", function(e) {
        e.preventDefault();
        menuItems.forEach(mi => mi.classList.remove("active"));
        this.classList.add("active");

        const section = this.dataset.section;
        currentSection = section;

        if (section === "solicitacoes") {
          sectionTitle.textContent = "Solicitações de retirada";
          sectionSubtitle.textContent = "Gerencie as solicitações de retirada de materiais dos clientes.";
          statsContainer.style.display = "grid";
          mainContentCard.style.display = "block";
          document.getElementById("tableCardTitle").textContent = "Solicitações de retirada";
          document.getElementById("tableFilters").style.display = "flex";
          renderRequests();
        } else if (section === "clientes") {
          sectionTitle.textContent = "Clientes Cadastrados";
          sectionSubtitle.textContent = "Lista de empresas parceiras e geradores de resíduos.";
          statsContainer.style.display = "none";
          mainContentCard.style.display = "block";
          document.getElementById("tableCardTitle").textContent = "Base de Clientes";
          document.getElementById("tableFilters").style.display = "none";
          
          // Render mock clients
          table.innerHTML = "";
          const uniqueClients = [...new Set(requests.map(r => r.client))];
          uniqueClients.forEach((clientName, idx) => {
            const req = requests.find(r => r.client === clientName);
            const row = document.createElement("tr");
            row.innerHTML = `
              <td><span class="protocol">CLI-00${idx + 1}</span></td>
              <td>
                <div class="client">
                  <div class="client-avatar">${getInitials(clientName)}</div>
                  <div>
                    <span class="client-name">${clientName}</span>
                    <span class="client-document">${req ? req.document : 'CNPJ: 00.000.000/0001-00'}</span>
                  </div>
                </div>
              </td>
              <td><span class="material">${req ? req.address : 'Endereço não informado'}</span></td>
              <td><span class="quantity">Ativo</span></td>
              <td>16/09/2026</td>
              <td>-</td>
              <td><span class="status concluida">Regular</span></td>
              <td><button class="action-button" title="Ver cliente">⋮</button></td>
            `;
            table.appendChild(row);
          });
          resultsCount.textContent = `${uniqueClients.length} clientes`;
          emptyState.style.display = "none";
        } else if (section === "retiradas") {
          sectionTitle.textContent = "Retiradas em Andamento";
          sectionSubtitle.textContent = "Acompanhe as coletas em transporte ou agendadas.";
          statsContainer.style.display = "grid";
          mainContentCard.style.display = "block";
          document.getElementById("tableCardTitle").textContent = "Operações de Transporte";
          document.getElementById("tableFilters").style.display = "flex";
          renderRequests();
        } else if (section === "materiais") {
          sectionTitle.textContent = "Catálogo de Materiais";
          sectionSubtitle.textContent = "Tipos de materiais recicláveis e resíduos aceitos.";
          statsContainer.style.display = "none";
          mainContentCard.style.display = "block";
          document.getElementById("tableCardTitle").textContent = "Tipos de Materiais";
          document.getElementById("tableFilters").style.display = "none";

          const materialsList = [
            { name: "Sucata metálica", category: "Metais", avgWeight: "2.400 kg/lote", demand: "Alta" },
            { name: "Resíduos de construção", category: "Construção Civil", avgWeight: "7.500 kg/lote", demand: "Média" },
            { name: "Papelão", category: "Papel e Papelão", avgWeight: "1.500 kg/lote", demand: "Alta" },
            { name: "Plástico reciclável", category: "Polímeros", avgWeight: "800 kg/lote", demand: "Alta" },
            { name: "Pallets de madeira", category: "Embalagens", avgWeight: "300 un.", demand: "Média" },
            { name: "Sucata eletrônica", category: "Eletrônicos", avgWeight: "400 kg/lote", demand: "Baixa" }
          ];

          table.innerHTML = "";
          materialsList.forEach((mat, idx) => {
            const row = document.createElement("tr");
            row.innerHTML = `
              <td><span class="protocol">MAT-00${idx + 1}</span></td>
              <td><div class="client"><div class="client-avatar">�</div><div><span class="client-name">${mat.name}</span><span class="client-document">Categoria: ${mat.category}</span></div></div></td>
              <td><span class="material">${mat.category}</span></td>
              <td><span class="quantity">${mat.avgWeight}</span></td>
              <td>Demanda: ${mat.demand}</td>
              <td>Disponível</td>
              <td><span class="status transporte">Ativo</span></td>
              <td><button class="action-button" title="Detalhes">⋮</button></td>
            `;
            table.appendChild(row);
          });
          resultsCount.textContent = `${materialsList.length} materiais`;
          emptyState.style.display = "none";
        } else {
          sectionTitle.textContent = "Configurações e Relatórios";
          sectionSubtitle.textContent = "Painel de controle geral e indicadores de desempenho.";
          statsContainer.style.display = "grid";
          mainContentCard.style.display = "block";
          document.getElementById("tableCardTitle").textContent = "Resumo Operacional";
          document.getElementById("tableFilters").style.display = "none";
          renderRequests();
        }
      });
    });

    // Initial render on load
    window.onload = function () {
      renderRequests();
    };
  </script>
</body>
</html>
