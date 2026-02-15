<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Finanças — Renan & Isabel</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        :root {
            --primary: #10b981;
            --primary-dark: #059669;
            --secondary: #6366f1;
            --danger: #ef4444;
            --warning: #f59e0b;
            --success: #10b981;
            --dark: #1f2937;
            --dark-light: #374151;
            --gray: #6b7280;
            --gray-light: #f3f4f6;
            --white: #ffffff;
            --border: #e5e7eb;
            --shadow: 0 1px 3px rgba(0,0,0,0.1);
            --shadow-lg: 0 10px 25px rgba(0,0,0,0.08);
            --radius: 12px;
            --radius-sm: 8px;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }
        
        .app-container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        /* Header */
        .header {
            background: var(--white);
            padding: 30px 40px;
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            margin-bottom: 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
        }
        
        .header-title {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .header-title h1 {
            font-size: 28px;
            color: var(--dark);
            font-weight: 700;
        }
        
        .badge {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .header-date {
            color: var(--gray);
            font-size: 14px;
            font-weight: 500;
        }
        
        /* Cards Grid */
        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-bottom: 24px;
        }
        
        .summary-card {
            background: var(--white);
            padding: 24px;
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            border-left: 4px solid;
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: default;
        }
        
        .summary-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 30px rgba(0,0,0,0.12);
        }
        
        .summary-card.income { border-left-color: var(--primary); }
        .summary-card.paid { border-left-color: var(--secondary); }
        .summary-card.pending { border-left-color: var(--warning); }
        .summary-card.balance { border-left-color: var(--primary-dark); }
        
        .summary-card-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 12px;
        }
        
        .summary-card-icon {
            width: 40px;
            height: 40px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
        }
        
        .summary-card.income .summary-card-icon { background: #d1fae5; }
        .summary-card.paid .summary-card-icon { background: #e0e7ff; }
        .summary-card.pending .summary-card-icon { background: #fef3c7; }
        .summary-card.balance .summary-card-icon { background: #d1fae5; }
        
        .summary-card-title {
            font-size: 14px;
            color: var(--gray);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .summary-card-value {
            font-size: 32px;
            font-weight: 700;
            color: var(--dark);
            margin-top: 8px;
        }
        
        /* Section */
        .section {
            background: var(--white);
            padding: 30px;
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            margin-bottom: 24px;
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
            padding-bottom: 16px;
            border-bottom: 2px solid var(--gray-light);
        }
        
        .section-title {
            font-size: 20px;
            font-weight: 700;
            color: var(--dark);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .section-title-icon {
            font-size: 24px;
        }
        
        /* Table */
        .table-container {
            overflow-x: auto;
            margin-bottom: 16px;
        }
        
        table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0;
        }
        
        thead {
            background: var(--gray-light);
        }
        
        th {
            padding: 14px 16px;
            text-align: left;
            font-size: 12px;
            font-weight: 700;
            color: var(--gray);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        th:first-child { border-radius: var(--radius-sm) 0 0 0; }
        th:last-child { border-radius: 0 var(--radius-sm) 0 0; }
        
        tbody tr {
            border-bottom: 1px solid var(--border);
            transition: background-color 0.2s;
        }
        
        tbody tr:hover {
            background: #fafafa;
        }
        
        tbody tr.highlight {
            background: #fffbeb;
        }
        
        td {
            padding: 16px;
            color: var(--dark);
        }
        
        /* Input */
        .input-wrapper {
            position: relative;
            display: flex;
            align-items: center;
        }
        
        .input-prefix {
            position: absolute;
            left: 14px;
            color: var(--gray);
            font-weight: 600;
            pointer-events: none;
            z-index: 1;
        }
        
        input[type="text"] {
            width: 100%;
            padding: 10px 14px;
            border: 2px solid var(--border);
            border-radius: var(--radius-sm);
            font-size: 15px;
            font-weight: 500;
            transition: all 0.2s;
            background: var(--white);
        }
        
        input[type="text"].with-prefix {
            padding-left: 38px;
        }
        
        input[type="text"]:focus {
            outline: none;
            border-color: var(--primary);
            background: #f0fdf4;
            box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.1);
        }
        
        input[type="text"]::placeholder {
            color: #d1d5db;
        }
        
        /* Checkbox */
        .checkbox-wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        input[type="checkbox"] {
            width: 22px;
            height: 22px;
            cursor: pointer;
            accent-color: var(--primary);
        }
        
        /* Buttons */
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: var(--radius-sm);
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            text-transform: none;
            letter-spacing: 0.3px;
        }
        
        .btn:hover {
            transform: translateY(-1px);
            box-shadow: var(--shadow-lg);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .btn-primary {
            background: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background: var(--primary-dark);
        }
        
        .btn-secondary {
            background: var(--secondary);
            color: white;
        }
        
        .btn-secondary:hover {
            background: #4f46e5;
        }
        
        .btn-warning {
            background: var(--warning);
            color: white;
        }
        
        .btn-warning:hover {
            background: #d97706;
        }
        
        .btn-danger {
            background: transparent;
            color: var(--danger);
            padding: 6px 12px;
            font-size: 13px;
            border: 2px solid var(--danger);
        }
        
        .btn-danger:hover {
            background: var(--danger);
            color: white;
        }
        
        .btn-outline {
            background: transparent;
            border: 2px solid var(--border);
            color: var(--gray);
        }
        
        .btn-outline:hover {
            border-color: var(--primary);
            color: var(--primary);
            background: #f0fdf4;
        }
        
        /* Distribution Panel */
        .distribution-panel {
            background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
            padding: 30px;
            border-radius: var(--radius);
            margin-bottom: 24px;
        }
        
        .distribution-title {
            font-size: 20px;
            font-weight: 700;
            color: var(--dark);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .distribution-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 16px;
        }
        
        .distribution-item {
            background: white;
            padding: 20px;
            border-radius: var(--radius-sm);
            box-shadow: var(--shadow);
        }
        
        .distribution-item-label {
            font-size: 13px;
            color: var(--gray);
            font-weight: 600;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .distribution-item-value {
            font-size: 24px;
            font-weight: 700;
            color: var(--dark);
        }
        
        .distribution-item.personal {
            background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
        }
        
        /* Dashboard */
        .dashboard {
            background: linear-gradient(135deg, var(--dark) 0%, var(--dark-light) 100%);
            padding: 40px;
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            color: white;
        }
        
        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }
        
        .dashboard-title {
            font-size: 24px;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .dashboard-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .dashboard-stat {
            background: rgba(255, 255, 255, 0.1);
            padding: 24px;
            border-radius: var(--radius-sm);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .dashboard-stat-label {
            font-size: 13px;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 8px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .dashboard-stat-value {
            font-size: 32px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .dashboard-history-title {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 20px;
        }
        
        .dashboard table {
            background: rgba(255, 255, 255, 0.05);
            border-radius: var(--radius-sm);
            overflow: hidden;
        }
        
        .dashboard th {
            background: rgba(255, 255, 255, 0.1);
            color: rgba(255, 255, 255, 0.9);
        }
        
        .dashboard td {
            color: rgba(255, 255, 255, 0.9);
            border-color: rgba(255, 255, 255, 0.1);
        }
        
        .dashboard tbody tr:hover {
            background: rgba(255, 255, 255, 0.05);
        }
        
        /* Action Buttons */
        .action-buttons {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
        }
        
        .action-buttons .btn {
            flex: 1;
            min-width: 200px;
            justify-content: center;
            padding: 16px 24px;
            font-size: 16px;
        }
        
        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 40px;
            color: rgba(255, 255, 255, 0.6);
        }
        
        .empty-state-icon {
            font-size: 48px;
            margin-bottom: 16px;
            opacity: 0.5;
        }
        
        /* Animations */
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .section, .summary-card {
            animation: slideIn 0.3s ease-out;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            body { padding: 12px; }
            .header { padding: 20px; }
            .section { padding: 20px; }
            .dashboard { padding: 24px; }
            .summary-card-value { font-size: 24px; }
            .dashboard-stat-value { font-size: 24px; }
            .action-buttons .btn { min-width: 100%; }
            th, td { padding: 12px 8px; font-size: 13px; }
        }
        
        /* Print */
        @media print {
            body { background: white; padding: 0; }
            .btn, .btn-danger, .action-buttons { display: none; }
            .section, .summary-card, .dashboard { box-shadow: none; page-break-inside: avoid; }
        }
        
        /* Success Message */
        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: white;
            padding: 16px 24px;
            border-radius: var(--radius-sm);
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            display: flex;
            align-items: center;
            gap: 12px;
            z-index: 1000;
            animation: slideInRight 0.3s ease-out;
        }
        
        @keyframes slideInRight {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
        
        .toast.success {
            border-left: 4px solid var(--success);
        }
        
        .toast.error {
            border-left: 4px solid var(--danger);
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Header -->
        <div class="header">
            <div class="header-title">
                <h1>💰 Controle Financeiro</h1>
                <span class="badge">Renan ❤️ Isabel</span>
            </div>
            <div class="header-date" id="current-date"></div>
        </div>

        <!-- Summary Cards -->
        <div class="cards-grid">
            <div class="summary-card income">
                <div class="summary-card-header">
                    <div class="summary-card-icon">📈</div>
                    <span class="summary-card-title">Total de Entradas</span>
                </div>
                <div class="summary-card-value" id="total-receita">R$ 0,00</div>
            </div>
            
            <div class="summary-card paid">
                <div class="summary-card-header">
                    <div class="summary-card-icon">✅</div>
                    <span class="summary-card-title">Total Pago</span>
                </div>
                <div class="summary-card-value" id="total-pago">R$ 0,00</div>
            </div>
            
            <div class="summary-card pending">
                <div class="summary-card-header">
                    <div class="summary-card-icon">⏳</div>
                    <span class="summary-card-title">Pendente</span>
                </div>
                <div class="summary-card-value" id="total-a-pagar">R$ 0,00</div>
            </div>
            
            <div class="summary-card balance">
                <div class="summary-card-header">
                    <div class="summary-card-icon">💎</div>
                    <span class="summary-card-title">Sobra Total</span>
                </div>
                <div class="summary-card-value" id="sobra-total">R$ 0,00</div>
            </div>
        </div>

        <!-- Receitas -->
        <div class="section">
            <div class="section-header">
                <h2 class="section-title">
                    <span class="section-title-icon">💵</span>
                    Receitas (Entradas)
                </h2>
                <button class="btn btn-primary" onclick="addLinha('tabela-entradas', 'entrada-valor')">
                    ➕ Nova Entrada
                </button>
            </div>
            <div class="table-container">
                <table id="tabela-entradas">
                    <thead>
                        <tr>
                            <th>Descrição</th>
                            <th style="width: 200px;">Valor</th>
                            <th style="width: 80px; text-align: center;">Ação</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><input type="text" value="Salário Renan" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="entrada-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Salário Isabel" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="entrada-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Vó" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="entrada-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Extra" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="entrada-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Assinaturas -->
        <div class="section">
            <div class="section-header">
                <h2 class="section-title">
                    <span class="section-title-icon">📱</span>
                    Assinaturas & Serviços
                </h2>
                <button class="btn btn-warning" onclick="addLinha('tabela-assinaturas', 'assinatura-item-valor')">
                    ➕ Nova Assinatura
                </button>
            </div>
            <div class="table-container">
                <table id="tabela-assinaturas">
                    <thead>
                        <tr>
                            <th>Serviço</th>
                            <th style="width: 200px;">Valor Mensal</th>
                            <th style="width: 80px; text-align: center;">Ação</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><input type="text" value="Apple iCloud (Isabel)" placeholder="Nome do serviço"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="assinatura-item-valor with-prefix" value="19,90" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Apple iCloud (Renan)" placeholder="Nome do serviço"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="assinatura-item-valor with-prefix" value="19,90" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="YouTube Premium" placeholder="Nome do serviço"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="assinatura-item-valor with-prefix" value="53,90" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="iFood Club" placeholder="Nome do serviço"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="assinatura-item-valor with-prefix" value="5,95" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Loovi Seguradora" placeholder="Nome do serviço"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="assinatura-item-valor with-prefix" value="112,57" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td style="text-align: center;">
                                <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Despesas -->
        <div class="section">
            <div class="section-header">
                <h2 class="section-title">
                    <span class="section-title-icon">💳</span>
                    Despesas & Contas
                </h2>
                <button class="btn btn-primary" onclick="addLinhaGasto()">
                    ➕ Nova Conta
                </button>
            </div>
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Descrição</th>
                            <th style="width: 200px;">Valor</th>
                            <th style="width: 100px; text-align: center;">Pago?</th>
                        </tr>
                    </thead>
                    <tbody id="tabela-gastos">
                        <tr class="highlight">
                            <td style="font-weight: 600;">📱 ASSINATURAS (Total)</td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" id="valor-total-assinaturas" class="with-prefix" readonly style="background: #fffbeb; font-weight: 600;">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="MRV" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>                        <tr>
                            <td><input type="text" value="Apartamento" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>                        <tr>
                            <td><input type="text" value="Escolinha Crescer" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>                        
						<tr>
                            <td><input type="text" value="Aluguel" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
						<tr>
                            <td><input type="text" value="Financiamento Carro" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Copel" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Sanepar" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Internet" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td><input type="text" value="Faculdade" placeholder="Descrição"></td>
                            <td>
                                <div class="input-wrapper">
                                    <span class="input-prefix">R$</span>
                                    <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                                </div>
                            </td>
                            <td>
                                <div class="checkbox-wrapper">
                                    <input type="checkbox" onchange="calcular()">
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Distribution -->
        <div class="distribution-panel">
            <h3 class="distribution-title">
                🎯 Planejamento de Sobras
            </h3>
            <div class="distribution-grid">
                <div class="distribution-item">
                    <div class="distribution-item-label">🏦 Fundo Reserva (25%)</div>
                    <div class="distribution-item-value" id="reserva">R$ 0,00</div>
                </div>
                <div class="distribution-item">
                    <div class="distribution-item-label">✈️ Fundo Viagem (10%)</div>
                    <div class="distribution-item-value" id="viagem">R$ 0,00</div>
                </div>
                <div class="distribution-item">
                    <div class="distribution-item-label">🛒 Fundo Compras (10%)</div>
                    <div class="distribution-item-value" id="compras">R$ 0,00</div>
                </div>
                <div class="distribution-item personal">
                    <div class="distribution-item-label">👩 Isabel (33%)</div>
                    <div class="distribution-item-value" id="sobra-isabel">R$ 0,00</div>
                </div>
                <div class="distribution-item personal">
                    <div class="distribution-item-label">👨 Renan (22%)</div>
                    <div class="distribution-item-value" id="sobra-renan">R$ 0,00</div>
                </div>
            </div>
        </div>

        <!-- Action Buttons -->
        <div class="section">
            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="gerarRelatorio()">
                    📋 Copiar para Planilha (CSV)
                </button>
                <button class="btn btn-primary" onclick="salvarNoHistorico()">
                    💾 Finalizar e Salvar Mês
                </button>
            </div>
        </div>

        <!-- Dashboard -->
        <div class="dashboard">
            <div class="dashboard-header">
                <h2 class="dashboard-title">
                    🚀 Dashboard Acumulado
                </h2>
                <button class="btn btn-outline" onclick="limparHistorico()">
                    🗑️ Limpar Histórico
                </button>
            </div>
            
            <div class="dashboard-stats">
                <div class="dashboard-stat">
                    <div class="dashboard-stat-label">💰 Total Fundo Reserva</div>
                    <div class="dashboard-stat-value" id="dash-reserva">R$ 0,00</div>
                </div>
                <div class="dashboard-stat">
                    <div class="dashboard-stat-label">✈️ Total Fundo Viagem</div>
                    <div class="dashboard-stat-value" id="dash-viagem">R$ 0,00</div>
                </div>
                <div class="dashboard-stat">
                    <div class="dashboard-stat-label">🛒 Total Fundo Compras</div>
                    <div class="dashboard-stat-value" id="dash-compras">R$ 0,00</div>
                </div>
            </div>
            
            <h3 class="dashboard-history-title">📅 Histórico de Meses Salvos</h3>
            <div class="table-container">
                <table id="tabela-historico">
                    <thead>
                        <tr>
                            <th>Mês/Ano</th>
                            <th>Entrada</th>
                            <th>Sobra</th>
                            <th>Reserva</th>
                            <th>Viagem</th>
                            <th>Compras</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td colspan="6">
                                <div class="empty-state">
                                    <div class="empty-state-icon">📊</div>
                                    <p>Nenhum mês salvo ainda. Finalize o mês atual para começar.</p>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>

    <script>
        // Utility Functions
        function parseMoeda(valor) {
            if (!valor) return 0;
            let limpo = valor.toString().replace(/\./g, '').replace(',', '.').replace(/[^0-9.]/g, '');
            return parseFloat(limpo) || 0;
        }

        function formatarMoeda(input) {
            let valor = parseMoeda(input.value);
            input.value = valor > 0 ? valor.toLocaleString('pt-BR', { 
                minimumFractionDigits: 2, 
                maximumFractionDigits: 2 
            }) : "";
        }

        function formatarMoedaBRL(valor) {
            return valor.toLocaleString('pt-BR', { 
                style: 'currency', 
                currency: 'BRL' 
            });
        }

        // Toast Notifications
        function showToast(message, type = 'success') {
            const toast = document.createElement('div');
            toast.className = `toast ${type}`;
            toast.innerHTML = `
                <span style="font-size: 20px;">${type === 'success' ? '✅' : '❌'}</span>
                <span style="font-weight: 600;">${message}</span>
            `;
            document.body.appendChild(toast);
            
            setTimeout(() => {
                toast.style.animation = 'slideInRight 0.3s ease-out reverse';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // Table Management
        function addLinha(idTabela, classe) {
            const tbody = document.querySelector(`#${idTabela} tbody`);
            const novaLinha = tbody.insertRow();
            novaLinha.innerHTML = `
                <td><input type="text" placeholder="Descrição"></td>
                <td>
                    <div class="input-wrapper">
                        <span class="input-prefix">R$</span>
                        <input type="text" class="${classe} with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                    </div>
                </td>
                <td style="text-align: center;">
                    <button class="btn btn-danger" onclick="removerLinha(this)">🗑️</button>
                </td>
            `;
        }

        function addLinhaGasto() {
            const tbody = document.getElementById('tabela-gastos');
            const novaLinha = tbody.insertRow();
            novaLinha.innerHTML = `
                <td><input type="text" placeholder="Nova conta"></td>
                <td>
                    <div class="input-wrapper">
                        <span class="input-prefix">R$</span>
                        <input type="text" class="gasto-valor with-prefix" placeholder="0,00" onblur="formatarMoeda(this)" oninput="calcular()">
                    </div>
                </td>
                <td>
                    <div class="checkbox-wrapper">
                        <input type="checkbox" onchange="calcular()">
                    </div>
                </td>
            `;
        }

        function removerLinha(botao) {
            botao.closest('tr').remove();
            calcular();
        }

        // Calculations
        function calcular() {
            // Calcular entradas
            let totalEntradas = 0;
            document.querySelectorAll('.entrada-valor').forEach(input => {
                totalEntradas += parseMoeda(input.value);
            });
            document.getElementById('total-receita').innerText = formatarMoedaBRL(totalEntradas);

            // Calcular assinaturas
            let totalAssinaturas = 0;
            document.querySelectorAll('.assinatura-item-valor').forEach(input => {
                totalAssinaturas += parseMoeda(input.value);
            });
            document.getElementById('valor-total-assinaturas').value = totalAssinaturas > 0 
                ? totalAssinaturas.toLocaleString('pt-BR', { minimumFractionDigits: 2, maximumFractionDigits: 2 })
                : "";

            // Calcular gastos
            let totalPago = 0;
            let totalPendente = 0;
            let totalDespesas = 0;
            
            document.querySelectorAll('#tabela-gastos tr').forEach(linha => {
                // Buscar todos os inputs de texto (tanto com classe gasto-valor quanto o readonly das assinaturas)
                const inputs = linha.querySelectorAll('input[type="text"]');
                const checkbox = linha.querySelector('input[type="checkbox"]');
                
                let valor = 0;
                
                // Verificar cada input na linha
                inputs.forEach(input => {
                    const inputValor = parseMoeda(input.value);
                    if (inputValor > 0) {
                        valor = inputValor;
                    }
                });
                
                // Se tem valor e checkbox, calcular
                if (valor > 0 && checkbox) {
                    totalDespesas += valor;
                    if (checkbox.checked) {
                        totalPago += valor;
                    } else {
                        totalPendente += valor;
                    }
                }
            });

            document.getElementById('total-pago').innerText = formatarMoedaBRL(totalPago);
            document.getElementById('total-a-pagar').innerText = formatarMoedaBRL(totalPendente);

            // Calcular sobra
            const sobra = totalEntradas - totalDespesas;
            document.getElementById('sobra-total').innerText = formatarMoedaBRL(sobra);

            // Calcular distribuição
            if (sobra > 0) {
                const reserva = sobra * 0.25;
                const viagem = sobra * 0.10;
                const compras = sobra * 0.10;
                const casal = sobra * 0.55;
                
                document.getElementById('reserva').innerText = formatarMoedaBRL(reserva);
                document.getElementById('viagem').innerText = formatarMoedaBRL(viagem);
                document.getElementById('compras').innerText = formatarMoedaBRL(compras);
                document.getElementById('sobra-isabel').innerText = formatarMoedaBRL(casal * 0.60);
                document.getElementById('sobra-renan').innerText = formatarMoedaBRL(casal * 0.40);
            } else {
                document.getElementById('reserva').innerText = 'R$ 0,00';
                document.getElementById('viagem').innerText = 'R$ 0,00';
                document.getElementById('compras').innerText = 'R$ 0,00';
                document.getElementById('sobra-isabel').innerText = 'R$ 0,00';
                document.getElementById('sobra-renan').innerText = 'R$ 0,00';
            }
        }

        // History Management
        function salvarNoHistorico() {
            const entrada = document.getElementById('total-receita').innerText;
            const sobra = document.getElementById('sobra-total').innerText;
            
            if (parseMoeda(entrada) === 0) {
                showToast('Preencha os valores antes de salvar!', 'error');
                return;
            }

            const dados = {
                data: new Date().toLocaleDateString('pt-BR', { month: '2-digit', year: 'numeric' }),
                entrada: entrada,
                sobra: sobra,
                reserva: document.getElementById('reserva').innerText,
                viagem: document.getElementById('viagem').innerText,
                compras: document.getElementById('compras').innerText
            };

            let historico = JSON.parse(localStorage.getItem('financas_historico') || "[]");
            historico.push(dados);
            localStorage.setItem('financas_historico', JSON.stringify(historico));
            
            showToast('Mês salvo com sucesso! 🎉', 'success');
            carregarDashboard();
        }

        function carregarDashboard() {
            let historico = JSON.parse(localStorage.getItem('financas_historico') || "[]");
            let totalReserva = 0;
            let totalViagem = 0;
            let totalCompras = 0;
            
            const tbody = document.querySelector('#tabela-historico tbody');
            tbody.innerHTML = "";

            if (historico.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="6">
                            <div class="empty-state">
                                <div class="empty-state-icon">📊</div>
                                <p>Nenhum mês salvo ainda. Finalize o mês atual para começar.</p>
                            </div>
                        </td>
                    </tr>
                `;
            } else {
                historico.forEach(mes => {
                    totalReserva += parseMoeda(mes.reserva);
                    totalViagem += parseMoeda(mes.viagem);
                    totalCompras += parseMoeda(mes.compras || 'R$ 0,00');
                    
                    const novaLinha = tbody.insertRow();
                    novaLinha.innerHTML = `
                        <td>${mes.data}</td>
                        <td>${mes.entrada}</td>
                        <td>${mes.sobra}</td>
                        <td>${mes.reserva}</td>
                        <td>${mes.viagem}</td>
                        <td>${mes.compras || 'R$ 0,00'}</td>
                    `;
                });
            }

            document.getElementById('dash-reserva').innerText = formatarMoedaBRL(totalReserva);
            document.getElementById('dash-viagem').innerText = formatarMoedaBRL(totalViagem);
            document.getElementById('dash-compras').innerText = formatarMoedaBRL(totalCompras);
        }

        function gerarRelatorio() {
            const data = new Date().toLocaleDateString('pt-BR', { month: '2-digit', year: 'numeric' });
            const valores = [
                data,
                document.getElementById('total-receita').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('total-pago').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('total-a-pagar').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('sobra-total').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('reserva').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('viagem').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('compras').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('sobra-isabel').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", "."),
                document.getElementById('sobra-renan').innerText.replace("R$\u00a0", "").replace(".", "").replace(",", ".")
            ];
            
            navigator.clipboard.writeText(valores.join(';'));
            showToast('Dados copiados! Cole no Google Sheets 📊', 'success');
        }

        function limparHistorico() {
            if (confirm('⚠️ Tem certeza que deseja apagar todo o histórico? Esta ação não pode ser desfeita.')) {
                localStorage.removeItem('financas_historico');
                carregarDashboard();
                showToast('Histórico limpo com sucesso!', 'success');
            }
        }

        // Initialize
        window.onload = () => {
            // Set current date
            const now = new Date();
            const mesAno = now.toLocaleDateString('pt-BR', { month: 'long', year: 'numeric' });
            document.getElementById('current-date').innerText = mesAno.charAt(0).toUpperCase() + mesAno.slice(1);
            
            calcular();
            carregarDashboard();
        };
    </script>
</body>
</html>
