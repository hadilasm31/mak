<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MKJ SERVICE - Gestion du Personnel</title>
    <style>
        :root {
            --admin-color: #2c7be5;
            --chef-color: #ff8c00;
            --employe-color: #28a745;
            --dark-bg: #0f172a;
            --card-bg: rgba(255, 255, 255, 0.95);
            --text-dark: #1e293b;
            --text-light: #64748b;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --border: #e2e8f0;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background: none;
            min-height: 100vh;
            color: #000;
            position: relative;
            overflow-x: hidden;
            width: 100%;
        }

        .bg-slider {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        .bg-slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0;
            animation: fade 20s infinite;
        }

        .bg-slide:nth-child(1) { 
            background-image: url('https://lespalmistes.ci/wp-content/uploads/2023/06/476300445258001666880096-1.jpg'); 
            animation-delay: 0s; 
        }
        .bg-slide:nth-child(2) { 
            background-image: url('https://www.makanisi.org/wp-content/uploads/2020/03/GTC_Palmier_Huile_en_Savane@DR.jpg'); 
            animation-delay: 5s; 
        }
        .bg-slide:nth-child(3) { 
            background-image: url('https://fr.infosgabon.com/wp-content/uploads/2018/01/Olam-Palm-Gabon.jpg'); 
            animation-delay: 10s; 
        }
        .bg-slide:nth-child(4) { 
            background-image: url('https://i.ytimg.com/vi/Dwl7T7PAC_g/maxresdefault.jpg'); 
            animation-delay: 15s; 
        }

        @keyframes fade {
            0% { opacity: 0; }
            10% { opacity: 1; }
            25% { opacity: 1; }
            35% { opacity: 0; }
            100% { opacity: 0; }
        }

        .app-container {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            width: 100%;
            overflow-x: hidden;
        }

        /* Header fixe */
        .header {
            background: var(--card-bg);
            backdrop-filter: blur(10px);
            padding: 1rem;
            box-shadow: var(--shadow);
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 1rem;
            width: 100%;
            position: fixed;
            top: 0;
            left: 0;
            z-index: 1000;
        }

        .main-content {
            flex: 1;
            padding: 1rem;
            max-width: 1200px;
            margin: 80px auto 0;
            width: 100%;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            flex-shrink: 0;
            min-width: 0;
        }

        .logo-icon {
            font-size: 1.8rem;
            color: var(--admin-color);
        }

        .logo h1 {
            font-size: 1.3rem;
            font-weight: 700;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            max-width: 150px;
        }

        .nav {
            display: flex;
            gap: 0.5rem;
            align-items: center;
            flex-wrap: wrap;
            justify-content: center;
        }

        .nav a {
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 500;
            padding: 0.5rem 0.8rem;
            border-radius: 8px;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .nav a:hover {
            background: var(--border);
        }

        /* Cards */
        .card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--admin-color);
            transition: all 0.3s ease;
        }

        .card:hover {
            box-shadow: var(--shadow-lg);
            transform: translateY(-2px);
        }

        /* Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.75rem 1.2rem;
            background: var(--admin-color);
            color: white;
            border: none;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
            white-space: nowrap;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
            opacity: 0.9;
        }

        .btn-chef { 
            background: var(--chef-color); 
            color: white;
        }
        .btn-employe { 
            background: var(--employe-color); 
            color: white;
        }
        .btn-danger { 
            background: var(--danger); 
            color: white;
        }
        .btn-success { 
            background: var(--success); 
            color: white;
        }
        .btn-warning { 
            background: var(--warning); 
            color: white;
        }
        .btn-whatsapp { 
            background: #25D366; 
            color: white;
        }
        .btn-email { 
            background: #EA4335; 
            color: white;
        }
        .btn-outline {
            background: transparent;
            border: 2px solid var(--admin-color);
            color: var(--admin-color);
        }
        .btn-outline:hover {
            background: var(--admin-color);
            color: white;
        }

        .btn-small {
            padding: 0.5rem 0.8rem;
            font-size: 0.8rem;
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        /* Role Cards */
        .roles-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .role-card {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 12px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            border-top: 4px solid var(--admin-color);
        }

        .role-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
        }

        .role-card.chef { border-color: var(--chef-color); }
        .role-card.employe { border-color: var(--employe-color); }

        .role-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        /* Forms */
        .form-group {
            margin-bottom: 1.2rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--text-dark);
            font-size: 0.9rem;
        }

        input, select, textarea {
            width: 100%;
            padding: 0.75rem;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--admin-color);
            box-shadow: 0 0 0 3px rgba(44, 123, 229, 0.1);
        }

        .form-row {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .form-row .form-group {
            flex: 1;
            min-width: 200px;
        }

        /* Tables */
        .table-container {
            overflow-x: auto;
            margin-top: 1rem;
            -webkit-overflow-scrolling: touch;
            width: 100%;
            border: 1px solid var(--border);
            border-radius: 8px;
            background: white;
            position: relative;
        }

        .table-container::-webkit-scrollbar {
            height: 8px;
        }

        .table-container::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 4px;
        }

        .table-container::-webkit-scrollbar-thumb {
            background: var(--admin-color);
            border-radius: 4px;
        }

        .table-container::-webkit-scrollbar-thumb:hover {
            background: #1a56db;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: var(--shadow);
            min-width: 800px;
        }

        th, td {
            padding: 0.8rem;
            text-align: left;
            border-bottom: 1px solid var(--border);
            font-size: 0.85rem;
            white-space: nowrap;
        }

        th {
            background: var(--admin-color);
            color: white;
            font-weight: 600;
            position: sticky;
            top: 0;
        }

        tr:hover {
            background: #f8fafc;
        }

        /* Alerts */
        .alert {
            padding: 1rem;
            border-radius: 8px;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.75rem;
            font-size: 0.9rem;
        }

        .alert.success {
            background: #d1fae5;
            color: #065f46;
            border-left: 4px solid var(--success);
        }

        .alert.error {
            background: #fee2e2;
            color: #991b1b;
            border-left: 4px solid var(--danger);
        }

        .alert.info {
            background: #dbeafe;
            color: #1e40af;
            border-left: 4px solid var(--admin-color);
        }

        .alert.warning {
            background: #fef3c7;
            color: #92400e;
            border-left: 4px solid var(--warning);
        }

        /* Dashboard Grid */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .dashboard-card {
            background: var(--card-bg);
            padding: 1.2rem;
            border-radius: 12px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            border-top: 4px solid var(--admin-color);
            cursor: pointer;
        }

        .dashboard-card:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-lg);
        }

        /* Login */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 70vh;
        }

        .login-card {
            width: 100%;
            max-width: 400px;
            padding: 1.5rem;
        }

        /* Presence Management */
        .presence-section {
            background: #f8fafc;
            padding: 1.2rem;
            border-radius: 8px;
            margin-bottom: 1.2rem;
        }

        .employee-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .employee-card {
            background: white;
            padding: 1rem;
            border-radius: 8px;
            border: 2px solid var(--border);
            transition: all 0.3s ease;
        }

        .employee-card.present {
            border-color: var(--success);
            background: #f0fdf4;
        }

        .employee-card.absent {
            border-color: var(--danger);
            background: #fef2f2;
        }

        .presence-toggle {
            display: flex;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }

        .toggle-btn {
            flex: 1;
            padding: 0.5rem;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            font-size: 0.8rem;
        }

        .toggle-present {
            background: var(--success);
            color: white;
        }

        .toggle-absent {
            background: var(--danger);
            color: white;
        }

        /* Image Section */
        .image-section {
            margin: 1.5rem 0;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--shadow-lg);
            position: relative;
            height: 250px;
        }

        .background-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .image-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.3);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            text-align: center;
            padding: 1.5rem;
        }

        .image-title {
            font-size: 2rem;
            font-weight: bold;
            margin-bottom: 0.8rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .image-subtitle {
            font-size: 1rem;
            margin-bottom: 1.5rem;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
            max-width: 600px;
        }

        /* Day Navigation */
        .day-navigation {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.2rem;
            padding: 1rem;
            background: #f8fafc;
            border-radius: 8px;
            gap: 1rem;
        }

        .day-selector {
            display: flex;
            gap: 0.5rem;
            align-items: center;
            flex-wrap: wrap;
        }

        .day-btn {
            padding: 0.5rem 0.8rem;
            border: 1px solid var(--border);
            background: white;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.8rem;
            min-width: 60px;
        }

        .day-btn.active {
            background: var(--admin-color);
            color: white;
            border-color: var(--admin-color);
        }

        .day-btn:hover:not(.active) {
            background: var(--border);
        }

        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 2rem;
            color: var(--text-light);
        }

        .empty-state-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            opacity: 0.5;
        }

        /* Notification buttons */
        .notification-buttons {
            display: flex;
            gap: 1rem;
            margin: 1rem 0;
            flex-wrap: wrap;
        }

        .notification-section {
            background: #f8fafc;
            padding: 1.2rem;
            border-radius: 8px;
            margin: 1.2rem 0;
            border-left: 4px solid var(--warning);
        }

        .sending-status {
            margin-top: 1rem;
            padding: 1rem;
            background: white;
            border-radius: 8px;
            border: 1px solid var(--border);
        }

        .status-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--border);
            font-size: 0.85rem;
        }

        .status-item:last-child {
            border-bottom: none;
        }

        .status-indicator {
            display: inline-block;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            margin-right: 0.5rem;
        }

        .status-pending { background: var(--warning); }
        .status-success { background: var(--success); }
        .status-error { background: var(--danger); }

        /* Styles pour le bulletin de paie professionnel */
        .bulletin-container {
            width: 100%;
            max-width: 210mm;
            height: auto;
            margin: 0 auto;
            background-color: white;
            box-shadow: var(--shadow-lg);
            position: relative;
            overflow: hidden;
            border-radius: 4px;
        }

        .bulletin-content {
            padding: 15px;
            height: 100%;
            display: flex;
            flex-direction: column;
        }

        /* Header */
        .bulletin-header {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--accent-color);
            gap: 1rem;
        }

        .company-info {
            flex: 1;
            min-width: 200px;
        }

        .company-logo {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
        }

        .logo-icon {
            font-size: 24px;
            margin-right: 8px;
            color: var(--accent-color);
        }

        .company-name {
            font-size: 18px;
            font-weight: 700;
            color: var(--primary-color);
        }

        .company-details {
            font-size: 9px;
            line-height: 1.3;
            color: #555;
        }

        .document-title {
            text-align: center;
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            margin-right: 0;
        }

        .title-main {
            font-size: 18px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 3px;
        }

        .title-sub {
            font-size: 11px;
            color: #666;
            font-weight: 500;
        }

        .employee-header-section {
            width: 120px;
            text-align: right;
        }

        .employee-photo {
            width: 70px;
            height: 70px;
            border: 2px solid var(--border-color);
            border-radius: 6px;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-left: auto;
            margin-bottom: 8px;
            overflow: hidden;
        }

        .photo-placeholder {
            color: #7f8c8d;
            font-size: 10px;
            text-align: center;
            padding: 3px;
        }

        .employee-details-compact {
            font-size: 9px;
        }

        .employee-details-compact .info-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 2px;
        }

        .employee-details-compact .info-label {
            font-weight: 600;
            text-align: left;
        }

        .employee-details-compact .info-value {
            text-align: right;
            margin-left: 5px;
        }

        /* Main Content */
        .bulletin-main {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .period-info {
            background-color: var(--header-bg);
            padding: 8px 12px;
            border-radius: 4px;
            margin-bottom: 12px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            font-size: 9px;
            gap: 0.5rem;
        }

        .period-dates {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }

        .period-item {
            display: flex;
            align-items: center;
        }

        .period-label {
            font-weight: 600;
            margin-right: 3px;
        }

        /* Main Table */
        .table-container-bulletin {
            flex: 1;
            overflow-x: auto;
            margin-bottom: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
        }

        .table-container-bulletin::-webkit-scrollbar {
            height: 6px;
        }

        .table-container-bulletin::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 3px;
        }

        .table-container-bulletin::-webkit-scrollbar-thumb {
            background: var(--accent-color);
            border-radius: 3px;
        }

        .main-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 8px;
            min-width: 600px;
        }

        .main-table th {
            background-color: var(--header-bg);
            border: 1px solid var(--border-color);
            padding: 6px 3px;
            text-align: center;
            font-weight: 600;
            color: var(--primary-color);
            position: sticky;
            top: 0;
        }

        .main-table td {
            border: 1px solid var(--border-color);
            padding: 5px 3px;
        }

        .main-table .designation {
            text-align: left;
            width: 35%;
        }

        .main-table .number, .main-table .base, .main-table .rate, 
        .main-table .gains, .main-table .deductions, .main-table .net {
            text-align: right;
            width: 11%;
        }

        .main-table .subtotal {
            font-weight: 600;
            background-color: var(--header-bg);
        }

        .main-table .total {
            font-weight: 700;
            background-color: var(--primary-color);
            color: white;
        }

        .main-table .activity-row {
            border-left: 2px solid var(--accent-color);
        }

        /* Summary */
        .summary-section {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            margin-bottom: 15px;
            gap: 1rem;
        }

        .summary-left, .summary-right {
            width: 100%;
            min-width: 200px;
        }

        .summary-title {
            font-size: 10px;
            font-weight: 600;
            margin-bottom: 5px;
            color: var(--primary-color);
            padding-bottom: 3px;
            border-bottom: 1px solid var(--border-color);
        }

        .summary-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 8px;
        }

        .summary-table td {
            border: 1px solid var(--border-color);
            padding: 5px;
        }

        .summary-table .label {
            font-weight: 600;
            width: 60%;
        }

        .summary-table .value {
            text-align: right;
            width: 40%;
        }

        .summary-table .total-row {
            font-weight: 700;
            background-color: var(--header-bg);
        }

        /* Footer */
        .bulletin-footer {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            margin-top: auto;
            padding-top: 10px;
            border-top: 1px solid var(--border-color);
            gap: 1rem;
        }

        .legal-mentions {
            width: 100%;
            font-size: 7px;
            color: #7f8c8d;
            line-height: 1.3;
        }

        .signature-section {
            text-align: center;
            width: 100%;
        }

        .signature-stamp {
            width: 80px;
            height: 80px;
            border: 2px solid var(--accent-color);
            border-radius: 50%;
            margin: 0 auto 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--accent-color);
            font-weight: 600;
            font-size: 8px;
            text-align: center;
            line-height: 1.1;
            background: white;
        }

        .signature-line {
            border-top: 1px solid var(--border-color);
            width: 120px;
            margin: 0 auto;
            padding-top: 3px;
            font-size: 8px;
        }

        /* Print styles */
        @media print {
            body {
                background: white;
                padding: 0;
                margin: 0;
            }
            
            .bulletin-container {
                box-shadow: none;
                margin: 0;
                width: 100%;
                height: 100%;
                border-radius: 0;
                page-break-after: avoid;
                page-break-inside: avoid;
            }
            
            .bulletin-content {
                padding: 10mm;
            }
            
            .no-print {
                display: none;
            }
        }

        /* Controls */
        .controls {
            text-align: center;
            margin: 15px auto;
            max-width: 210mm;
        }

        /* Additional variables for bulletin */
        .bulletin-container {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #2980b9;
            --border-color: #e0e0e0;
            --text-color: #2c3e50;
            --light-bg: #f8f9fa;
            --success-color: #27ae60;
            --header-bg: #f5f7fa;
        }

        /* Color indicator */
        .color-indicator {
            display: inline-block;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            margin-right: 0.5rem;
            border: 2px solid white;
            box-shadow: 0 0 0 1px var(--border);
        }

        /* Activity badges */
        .activity-badge {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            background: var(--admin-color);
            color: white;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
            margin-left: 0.5rem;
        }

        /* Action buttons */
        .action-buttons {
            display: flex;
            gap: 1rem;
            margin: 1.5rem 0;
            flex-wrap: wrap;
        }

        .action-btn {
            flex: 1;
            min-width: 200px;
            padding: 1.2rem;
            font-size: 1rem;
            text-align: center;
        }

        .chef-info {
            background: #e8f2ff;
            padding: 1rem;
            border-radius: 8px;
            margin-bottom: 1.2rem;
            font-size: 0.9rem;
        }

        /* Photo upload */
        .photo-upload-container {
            text-align: center;
            margin-bottom: 1.2rem;
        }

        .photo-preview {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--border);
            margin: 0 auto 1rem;
            display: block;
            background: #f8fafc;
        }

        .photo-placeholder {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: #f8fafc;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1rem;
            border: 3px dashed var(--border);
            color: var(--text-light);
            font-size: 1.8rem;
        }

        .file-input {
            display: none;
        }

        .file-input-label {
            display: inline-block;
            padding: 0.5rem 1rem;
            background: var(--admin-color);
            color: white;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .file-input-label:hover {
            background: #1a56db;
        }

        .user-photo {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            object-fit: cover;
            margin-right: 0.5rem;
            border: 2px solid var(--border);
        }

        .user-photo-table {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            object-fit: cover;
            margin-right: 0.5rem;
            border: 2px solid var(--border);
        }

        /* Avatar avec initiales */
        .avatar {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 14px;
            margin-right: 0.5rem;
        }

        .avatar-table {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 10px;
            margin-right: 0.5rem;
        }

        .avatar-admin { background: var(--admin-color); }
        .avatar-chef { background: var(--chef-color); }
        .avatar-employe { background: var(--employe-color); }

        /* Filtres */
        .filters {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.2rem;
            flex-wrap: wrap;
            align-items: center;
        }

        .filter-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            min-width: 150px;
        }

        .filter-group label {
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 0;
        }

        /* Stats cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin-bottom: 1.2rem;
        }

        .stat-card {
            background: white;
            padding: 1.2rem;
            border-radius: 8px;
            text-align: center;
            box-shadow: var(--shadow);
            border-top: 4px solid var(--admin-color);
        }

        .stat-number {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--admin-color);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 0.8rem;
        }

        /* Fiche de pointage */
        .fiche-header {
            background: #f8fafc;
            padding: 1.2rem;
            border-radius: 8px;
            margin-bottom: 1.2rem;
            border-left: 4px solid var(--admin-color);
        }

        .fiche-date {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--admin-color);
            margin-bottom: 0.5rem;
        }

        .fiche-activity {
            font-size: 1rem;
            color: var(--text-light);
            font-weight: 500;
        }

        .fiche-stats {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
            flex-wrap: wrap;
        }

        .fiche-stat {
            background: white;
            padding: 0.75rem 1rem;
            border-radius: 6px;
            border: 1px solid var(--border);
            text-align: center;
            min-width: 100px;
        }

        .fiche-stat-number {
            font-size: 1.1rem;
            font-weight: bold;
            color: var(--admin-color);
        }

        .fiche-stat-label {
            font-size: 0.75rem;
            color: var(--text-light);
        }

        /* Archives */
        .archive-section {
            background: #f8fafc;
            padding: 1.2rem;
            border-radius: 8px;
            margin-bottom: 1.2rem;
            border-left: 4px solid var(--warning);
        }

        .archive-actions {
            display: flex;
            gap: 1rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .archive-folder {
            background: white;
            border: 2px solid var(--border);
            border-radius: 8px;
            padding: 1rem;
            margin-bottom: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .archive-folder:hover {
            border-color: var(--admin-color);
            transform: translateY(-2px);
        }

        .folder-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.5rem;
        }

        .folder-title {
            font-weight: bold;
            color: var(--admin-color);
        }

        .folder-count {
            background: var(--admin-color);
            color: white;
            padding: 0.25rem 0.5rem;
            border-radius: 12px;
            font-size: 0.8rem;
        }

        .folder-details {
            font-size: 0.85rem;
            color: var(--text-light);
        }

        .search-box {
            display: flex;
            gap: 0.5rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .search-input {
            flex: 1;
            min-width: 200px;
        }

        .search-results {
            background: white;
            border-radius: 8px;
            padding: 1rem;
            margin-top: 1rem;
            box-shadow: var(--shadow);
        }

        /* Checkbox pour sélection multiple */
        .select-all-container {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 1rem;
            padding: 1rem;
            background: #f8fafc;
            border-radius: 8px;
            flex-wrap: wrap;
        }

        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem;
            margin: 0.25rem 0;
        }

        .selected-count {
            background: var(--admin-color);
            color: white;
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        /* Modal d'archivage */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 1rem;
        }

        .modal-content {
            background: white;
            padding: 1.5rem;
            border-radius: 12px;
            box-shadow: var(--shadow-lg);
            max-width: 500px;
            width: 100%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.2rem;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-light);
        }

        .archive-options {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            margin: 1rem 0;
        }

        .archive-option {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            border: 2px solid var(--border);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .archive-option:hover {
            border-color: var(--admin-color);
            background: #f0f7ff;
        }

        .archive-option.selected {
            border-color: var(--admin-color);
            background: #e8f2ff;
        }

        .option-icon {
            font-size: 1.8rem;
        }

        .option-content {
            flex: 1;
        }

        .option-title {
            font-weight: 600;
            margin-bottom: 0.25rem;
        }

        .option-description {
            font-size: 0.85rem;
            color: var(--text-light);
        }

        /* Sous-quantités */
        .sub-quantities-container {
            background: #f8fafc;
            padding: 1rem;
            border-radius: 8px;
            margin-bottom: 1rem;
        }

        .sub-quantity-row {
            display: flex;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
            align-items: center;
        }

        .sub-quantity-input {
            flex: 1;
        }

        .sub-quantity-total {
            font-weight: bold;
            margin-top: 0.5rem;
            padding: 0.5rem;
            background: white;
            border-radius: 4px;
            text-align: center;
        }

        /* Hidden sections */
        .section {
            display: none;
        }

        .section.active {
            display: block;
        }

        /* ============================================= */
        /* NOUVEAUX STYLES POUR LES TABLEAUX PAR SEMAINE */
        /* ============================================= */

        .week-container {
            margin-bottom: 2rem;
            border: 1px solid var(--border);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: var(--shadow);
        }

        .week-header {
            background: var(--admin-color);
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .week-header:hover {
            background: #1a56db;
        }

        .week-title {
            font-size: 1.1rem;
            font-weight: 600;
        }

        .week-dates {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        .week-stats {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .week-stat {
            background: rgba(255, 255, 255, 0.2);
            padding: 0.3rem 0.7rem;
            border-radius: 20px;
            font-size: 0.8rem;
        }

        .week-content {
            display: none;
            background: white;
        }

        .week-content.expanded {
            display: block;
        }

        .week-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.85rem;
        }

        .week-table th {
            background: #f8fafc;
            color: var(--text-dark);
            font-weight: 600;
            padding: 0.8rem;
            border-bottom: 1px solid var(--border);
            text-align: left;
        }

        .week-table td {
            padding: 0.8rem;
            border-bottom: 1px solid var(--border);
        }

        .week-table tr:last-child td {
            border-bottom: none;
        }

        .week-table tr:hover {
            background: #f8fafc;
        }

        .week-total {
            background: #f0f7ff;
            font-weight: 600;
        }

        .week-total td {
            border-top: 2px solid var(--admin-color);
        }

        /* ============================================= */
        /* NOUVEAUX STYLES POUR L'EXPORT */
        /* ============================================= */

        .export-section {
            background: #f8fafc;
            padding: 1.5rem;
            border-radius: 8px;
            margin: 1.5rem 0;
            border-left: 4px solid var(--chef-color);
        }

        .export-buttons {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .export-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 1.5rem;
            background: white;
            border: 2px solid var(--border);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }

        .export-btn:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-lg);
            border-color: var(--chef-color);
        }

        .export-icon {
            font-size: 2.5rem;
            margin-bottom: 0.8rem;
        }

        .export-title {
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-dark);
        }

        .export-description {
            font-size: 0.85rem;
            color: var(--text-light);
            line-height: 1.4;
        }

        .whatsapp-input-section {
            margin-top: 1rem;
            padding: 1rem;
            background: white;
            border-radius: 6px;
            border: 1px solid var(--border);
        }

        .whatsapp-input-group {
            display: flex;
            gap: 0.5rem;
            align-items: center;
        }

        .whatsapp-input {
            flex: 1;
            padding: 0.75rem;
            border: 1px solid var(--border);
            border-radius: 6px;
            font-size: 0.9rem;
        }

        .whatsapp-input:focus {
            outline: none;
            border-color: var(--chef-color);
            box-shadow: 0 0 0 3px rgba(255, 140, 0, 0.1);
        }

        .whatsapp-example {
            font-size: 0.8rem;
            color: var(--text-light);
            margin-top: 0.5rem;
        }

        .export-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.85rem;
        }

        .export-table th {
            background: var(--chef-color);
            color: white;
            padding: 0.8rem;
            text-align: left;
            font-weight: 600;
        }

        .export-table td {
            padding: 0.8rem;
            border-bottom: 1px solid var(--border);
        }

        .export-table tfoot {
            background: #f8fafc;
            font-weight: 600;
        }

        .export-table tfoot td {
            border-top: 2px solid var(--chef-color);
        }

        /* ============================================= */
        /* MEDIA QUERIES POUR LA RESPONSIVE */
        /* ============================================= */

        /* Tablettes */
        @media (max-width: 1024px) {
            .header {
                padding: 1rem;
            }
            
            .logo h1 {
                font-size: 1.2rem;
                max-width: 140px;
            }
            
            .nav a {
                padding: 0.4rem 0.7rem;
                font-size: 0.85rem;
            }
            
            .main-content {
                padding: 1rem;
            }
            
            .card {
                padding: 1.2rem;
            }
            
            .roles-grid {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            }
            
            .dashboard-grid {
                grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            }
            
            .action-btn {
                min-width: 180px;
                padding: 1rem;
            }
            
            .image-section {
                height: 200px;
            }
            
            .image-title {
                font-size: 1.8rem;
            }
            
            .image-subtitle {
                font-size: 0.9rem;
            }
        }

        /* Mobiles */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                gap: 1rem;
                padding: 1rem;
            }

            .nav {
                width: 100%;
                justify-content: center;
            }

            .main-content {
                padding: 0.8rem;
            }
            
            .card {
                padding: 1rem;
                margin-bottom: 1rem;
            }
            
            .form-row {
                flex-direction: column;
            }
            
            .form-row .form-group {
                min-width: 100%;
            }

            .roles-grid, .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .employee-list {
                grid-template-columns: 1fr;
            }
            
            .filters {
                flex-direction: column;
                align-items: stretch;
            }
            
            .filter-group {
                min-width: 100%;
            }
            
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .action-buttons {
                flex-direction: column;
            }
            
            .action-btn {
                min-width: 100%;
            }
            
            .notification-buttons {
                flex-direction: column;
            }
            
            .day-navigation {
                flex-direction: column;
                align-items: stretch;
            }
            
            .day-selector {
                justify-content: center;
            }
            
            .image-section {
                height: 180px;
            }
            
            .image-title {
                font-size: 1.5rem;
            }
            
            .image-subtitle {
                font-size: 0.8rem;
                margin-bottom: 1rem;
            }
            
            .bulletin-header {
                flex-direction: column;
                text-align: center;
            }
            
            .employee-header-section {
                width: 100%;
                text-align: center;
                margin-top: 15px;
            }
            
            .employee-photo {
                margin: 0 auto 8px;
            }
            
            .summary-section {
                flex-direction: column;
            }
            
            .summary-left, .summary-right {
                width: 100%;
                margin-bottom: 15px;
            }
            
            .bulletin-footer {
                flex-direction: column;
            }
            
            .legal-mentions, .signature-section {
                width: 100%;
            }
            
            .archive-actions {
                flex-direction: column;
            }
            
            .select-all-container {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .search-box {
                flex-direction: column;
            }
            
            .search-input {
                min-width: 100%;
            }
            
            .modal-content {
                padding: 1rem;
            }
            
            .archive-option {
                flex-direction: column;
                text-align: center;
            }
            
            .option-icon {
                font-size: 2rem;
            }
            
            .export-buttons {
                grid-template-columns: 1fr;
            }
            
            .whatsapp-input-group {
                flex-direction: column;
            }
            
            .whatsapp-input {
                width: 100%;
            }
            
            /* Responsive pour les tableaux par semaine */
            .week-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 0.5rem;
            }
            
            .week-stats {
                width: 100%;
                justify-content: space-between;
            }
            
            .week-table {
                font-size: 0.75rem;
            }
            
            .week-table th, .week-table td {
                padding: 0.5rem;
            }
        }

        /* Petits mobiles */
        @media (max-width: 480px) {
            .header {
                padding: 0.8rem 0.5rem;
            }
            
            .logo h1 {
                font-size: 1rem;
                max-width: 120px;
            }
            
            .logo-icon {
                font-size: 1.5rem;
            }
            
            .nav a {
                padding: 0.3rem 0.5rem;
                font-size: 0.75rem;
            }
            
            .main-content {
                padding: 0.5rem;
            }
            
            .card {
                padding: 0.8rem;
            }
            
            .btn {
                padding: 0.6rem 1rem;
                font-size: 0.85rem;
            }
            
            .btn-small {
                padding: 0.4rem 0.7rem;
                font-size: 0.75rem;
            }
            
            .roles-grid {
                gap: 0.8rem;
            }
            
            .role-card {
                padding: 1rem;
            }
            
            .role-icon {
                font-size: 2rem;
            }
            
            .dashboard-grid {
                gap: 0.8rem;
            }
            
            .dashboard-card {
                padding: 1rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
                gap: 0.8rem;
            }
            
            .stat-card {
                padding: 1rem;
            }
            
            .stat-number {
                font-size: 1.3rem;
            }
            
            .image-section {
                height: 150px;
            }
            
            .image-title {
                font-size: 1.3rem;
            }
            
            .image-subtitle {
                font-size: 0.75rem;
            }
            
            .fiche-header {
                padding: 1rem;
            }
            
            .fiche-date {
                font-size: 1.1rem;
            }
            
            .fiche-activity {
                font-size: 0.9rem;
            }
            
            .fiche-stats {
                gap: 0.5rem;
            }
            
            .fiche-stat {
                padding: 0.5rem 0.8rem;
                min-width: 80px;
            }
            
            .fiche-stat-number {
                font-size: 1rem;
            }
            
            .fiche-stat-label {
                font-size: 0.7rem;
            }
            
            th, td {
                padding: 0.6rem;
                font-size: 0.75rem;
            }
            
            .alert {
                padding: 0.8rem;
                font-size: 0.85rem;
            }
            
            .presence-section {
                padding: 1rem;
            }
            
            .employee-card {
                padding: 0.8rem;
            }
            
            .toggle-btn {
                font-size: 0.75rem;
            }
            
            .notification-section {
                padding: 1rem;
            }
            
            .sending-status {
                padding: 0.8rem;
            }
            
            .status-item {
                font-size: 0.8rem;
            }
            
            .day-btn {
                padding: 0.4rem 0.6rem;
                font-size: 0.75rem;
                min-width: 50px;
            }
            
            .empty-state {
                padding: 1.5rem;
            }
            
            .empty-state-icon {
                font-size: 2.5rem;
            }
            
            .photo-preview, .photo-placeholder {
                width: 80px;
                height: 80px;
            }
            
            .photo-placeholder {
                font-size: 1.5rem;
            }
            
            .user-photo {
                width: 30px;
                height: 30px;
            }
            
            .user-photo-table {
                width: 20px;
                height: 20px;
            }
            
            .avatar {
                width: 30px;
                height: 30px;
                font-size: 12px;
            }
            
            .avatar-table {
                width: 20px;
                height: 20px;
                font-size: 9px;
            }
            
            .color-indicator {
                width: 16px;
                height: 16px;
            }
            
            .activity-badge {
                padding: 0.2rem 0.6rem;
                font-size: 0.75rem;
            }
            
            .chef-info {
                padding: 0.8rem;
                font-size: 0.85rem;
            }
            
            table {
                min-width: 800px;
            }
            
            /* Responsive pour les tableaux par semaine */
            .week-table {
                min-width: 800px;
            }
            
            .week-stat {
                font-size: 0.7rem;
                padding: 0.2rem 0.5rem;
            }
        }

        /* Très petits écrans */
        @media (max-width: 360px) {
            .logo h1 {
                font-size: 0.9rem;
                max-width: 100px;
            }
            
            .nav a {
                padding: 0.25rem 0.4rem;
                font-size: 0.7rem;
            }
            
            .main-content {
                padding: 0.3rem;
            }
            
            .card {
                padding: 0.7rem;
            }
            
            .btn {
                padding: 0.5rem 0.8rem;
                font-size: 0.8rem;
            }
            
            .roles-grid {
                grid-template-columns: 1fr;
            }
            
            .role-card {
                padding: 0.8rem;
            }
            
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .dashboard-card {
                padding: 0.8rem;
            }
            
            .image-section {
                height: 120px;
            }
            
            .image-title {
                font-size: 1.1rem;
            }
            
            .image-subtitle {
                font-size: 0.7rem;
            }
            
            .fiche-header {
                padding: 0.8rem;
            }
            
            .fiche-date {
                font-size: 1rem;
            }
            
            .fiche-activity {
                font-size: 0.8rem;
            }
            
            .fiche-stats {
                gap: 0.3rem;
            }
            
            .fiche-stat {
                padding: 0.4rem 0.6rem;
                min-width: 70px;
            }
            
            .fiche-stat-number {
                font-size: 0.9rem;
            }
            
            .fiche-stat-label {
                font-size: 0.65rem;
            }
            
            table {
                min-width: 800px;
            }
            
            /* Responsive pour les tableaux par semaine */
            .week-table {
                min-width: 800px;
            }
        }

        /* Orientation paysage sur mobiles */
        @media (max-height: 500px) and (orientation: landscape) {
            .header {
                padding: 0.5rem;
                flex-wrap: nowrap;
            }
            
            .nav {
                flex-wrap: nowrap;
            }
            
            .main-content {
                padding: 0.5rem;
            }
            
            .card {
                padding: 1rem;
                margin-bottom: 0.8rem;
            }
            
            .login-container {
                min-height: 60vh;
            }
            
            .image-section {
                height: 120px;
                margin: 1rem 0;
            }
            
            .roles-grid {
                grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
                gap: 0.8rem;
                margin-top: 1rem;
            }
            
            .dashboard-grid {
                grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
                gap: 0.8rem;
                margin-top: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="bg-slider">
        <div class="bg-slide"></div>
        <div class="bg-slide"></div>
        <div class="bg-slide"></div>
        <div class="bg-slide"></div>
    </div>

    <div class="app-container">
        <!-- Header fixe -->
        <header class="header" id="appHeader">
            <div class="logo">
                <div class="logo-icon">🌴</div>
                <h1>MKJ SERVICE</h1>
            </div>
            <nav class="nav" id="appNav">
                <a href="#" onclick="showSection('home')">Accueil</a>
                <a href="#" onclick="showSection('dashboard')" id="navDashboard" style="display: none;">Dashboard</a>
                <a href="#" onclick="showSection('profile')" id="navProfile" style="display: none;">Profil</a>
                <a href="#" onclick="showSection('adminArchives')" id="navArchives" style="display: none;">Archives</a>
                <a href="#" onclick="logout()" id="navLogout" style="display: none;">Déconnexion</a>
            </nav>
        </header>

        <!-- Main Content -->
        <main class="main-content">
            <!-- Alerts Container -->
            <div id="alertsContainer"></div>

            <!-- Home Section -->
            <section id="home" class="section active">
                <!-- Image Section -->
                <div class="image-section">
                    <img src="https://static.vecteezy.com/ti/vecteur-libre/p1/132008-illustration-de-l-huile-de-palme-vectoriel.jpg" alt="Plantation de palmiers" class="background-image">
                    <div class="image-overlay">
                        <h2 class="image-title">MKJ SERVICE</h2>
                        <p class="image-subtitle">Expert en plantation de palmiers à huile - Gestion optimisée de votre personnel</p>
                    </div>
                </div>

                <div class="card">
                    <h2>Bienvenue sur MKJ SERVICE</h2>
                    <p>Système de gestion du personnel pour plantation de palmiers à huile</p>
                    
                    <div class="roles-grid">
                        <div class="role-card">
                            <div class="role-icon">👑</div>
                            <h3>ADMINISTRATEUR</h3>
                            <p>Accès complet à la gestion des utilisateurs et données</p>
                            <button class="btn" onclick="showLogin('ADMINISTRATEUR')">Se connecter</button>
                        </div>
                        
                        <div class="role-card chef">
                            <div class="role-icon">👨‍💼</div>
                            <h3>CHEF D'ÉQUIPE</h3>
                            <p>Gestion des pointages et suivi des équipes</p>
                            <button class="btn btn-chef" onclick="showLogin('CHEF')">Se connecter</button>
                        </div>
                        
                        <div class="role-card employe">
                            <div class="role-icon">👷</div>
                            <h3>EMPLOYÉ</h3>
                            <p>Consultation des pointages et activités</p>
                            <button class="btn btn-employe" onclick="showLogin('EMPLOYE')">Se connecter</button>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Login Section -->
            <section id="login" class="section">
                <div class="login-container">
                    <div class="card login-card">
                        <h2 id="loginTitle">Connexion</h2>
                        <form id="loginForm" onsubmit="handleLogin(event)">
                            <div class="form-group">
                                <label for="username">Identifiant</label>
                                <input type="text" id="username" required placeholder="Votre identifiant">
                            </div>
                            
                            <div class="form-group">
                                <label for="password">Mot de passe</label>
                                <input type="password" id="password" required placeholder="Votre mot de passe">
                            </div>
                            
                            <button type="submit" class="btn" style="width: 100%;">
                                <span>🔐</span> Se connecter
                            </button>
                        </form>
                        
                        <div style="text-align: center; margin-top: 1rem;">
                            <button class="btn btn-outline" onclick="showSection('home')">← Retour à l'accueil</button>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Dashboard Section -->
            <section id="dashboard" class="section">
                <div class="card">
                    <h2 id="dashboardTitle">Tableau de bord</h2>
                    <p id="dashboardWelcome">Bienvenue !</p>
                    
                    <div class="dashboard-grid" id="dashboardGrid">
                        <!-- Content populated by JavaScript -->
                    </div>
                </div>
            </section>

            <!-- Profile Section -->
            <section id="profile" class="section">
                <div class="card">
                    <h3>Profil utilisateur</h3>
                    <div id="profileContent">
                        <!-- Content populated by JavaScript -->
                    </div>
                </div>
            </section>

            <!-- Admin Users Section -->
            <section id="adminUsers" class="section">
                <div class="card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                        <h3>Gestion des utilisateurs</h3>
                        <button class="btn" onclick="showSection('adminCreateUser')">➕ Créer utilisateur</button>
                    </div>

                    <!-- Filtres -->
                    <div class="filters">
                        <div class="filter-group">
                            <label for="filterDepartement">Filtrer par département:</label>
                            <select id="filterDepartement" onchange="filterUsersTable()">
                                <option value="">Tous les départements</option>
                                <!-- Options will be populated by JavaScript -->
                            </select>
                        </div>
                        <div class="filter-group">
                            <label for="filterRole">Filtrer par rôle:</label>
                            <select id="filterRole" onchange="filterUsersTable()">
                                <option value="">Tous les rôles</option>
                                <option value="CHEF">CHEF</option>
                                <option value="EMPLOYE">EMPLOYE</option>
                            </select>
                        </div>
                    </div>

                    <div class="table-container">
                        <table id="usersTable">
                            <thead>
                                <tr>
                                    <th>Photo</th><th>ID</th><th>Identifiant</th><th>Nom</th><th>Prénom</th><th>Role</th><th>Activité</th><th>Département</th><th>Couleur</th><th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="usersTableBody">
                                <!-- Populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- Admin Pointages Section -->
            <section id="adminPointages" class="section">
                <div class="card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                        <h3>Gestion des fiches de pointage</h3>
                        <div>
                            <button class="btn" onclick="showSection('dashboard')">📊 Retour au dashboard</button>
                            <button class="btn btn-warning" onclick="showArchiveModal('pointages')" style="margin-left: 0.5rem;">📦 Archiver sélection</button>
                        </div>
                    </div>

                    <!-- Sélection multiple -->
                    <div class="select-all-container">
                        <input type="checkbox" id="selectAllPointages" onchange="toggleSelectAllPointages()">
                        <label for="selectAllPointages">Tout sélectionner</label>
                        <span class="selected-count" id="selectedPointagesCount">0 sélectionné(s)</span>
                        <button class="btn btn-small btn-outline" onclick="clearPointagesSelection()" style="margin-left: auto;">❌ Effacer</button>
                    </div>

                    <!-- Recherche avancée -->
                    <div class="search-box">
                        <input type="text" id="searchPointage" class="search-input" placeholder="Rechercher par nom d'employé, chef, activité..." onkeyup="searchPointages()">
                        <button class="btn btn-small" onclick="searchPointages()">🔍 Rechercher</button>
                        <button class="btn btn-small btn-outline" onclick="clearPointageSearch()">❌ Effacer</button>
                    </div>

                    <!-- Statistiques -->
                    <div class="stats-grid" id="pointageStats">
                        <!-- Populated by JavaScript -->
                    </div>

                    <!-- Filtres -->
                    <div class="filters">
                        <div class="filter-group">
                            <label for="filterPointageActivity">Filtrer par activité:</label>
                            <select id="filterPointageActivity" onchange="filterPointagesTable()">
                                <option value="">Toutes les activités</option>
                                <!-- Options will be populated by JavaScript -->
                            </select>
                        </div>
                        <div class="filter-group">
                            <label for="filterPointageDate">Filtrer par date:</label>
                            <input type="date" id="filterPointageDate" onchange="filterPointagesTable()">
                        </div>
                        <div class="filter-group">
                            <label for="filterPointageChef">Filtrer par chef:</label>
                            <select id="filterPointageChef" onchange="filterPointagesTable()">
                                <option value="">Tous les chefs</option>
                                <!-- Options will be populated by JavaScript -->
                            </select>
                        </div>
                        <div class="filter-group">
                            <label for="filterPointageArchived">Statut:</label>
                            <select id="filterPointageArchived" onchange="filterPointagesTable()">
                                <option value="non-archived">Non archivés</option>
                                <option value="archived">Archivés</option>
                                <option value="all">Tous</option>
                            </select>
                        </div>
                    </div>

                    <!-- Conteneur pour les pointages groupés par semaine -->
                    <div id="pointagesByWeekContainer">
                        <!-- Les pointages groupés par semaine seront affichés ici -->
                    </div>
                </div>
            </section>

            <!-- Admin Create User Section -->
            <section id="adminCreateUser" class="section">
                <div class="card">
                    <h3>Créer un utilisateur</h3>
                    <form id="createUserForm" onsubmit="handleCreateUser(event)">
                        <!-- Photo Upload -->
                        <div class="photo-upload-container">
                            <div id="photoPreview" class="photo-placeholder">
                                👤
                            </div>
                            <input type="file" id="photoInput" class="file-input" accept="image/*" onchange="previewPhoto(event)">
                            <label for="photoInput" class="file-input-label">📷 Choisir une photo</label>
                            <div style="font-size: 0.8rem; color: var(--text-light); margin-top: 0.5rem;">
                                Si aucune photo n'est choisie, un avatar avec les initiales sera généré
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Role *</label>
                                <select id="userRole" required onchange="toggleActivityField()">
                                    <option value="">Sélectionner un rôle</option>
                                    <option value="CHEF">CHEF</option>
                                    <option value="EMPLOYE">EMPLOYE</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Identifiant *</label>
                                <input type="text" id="newUsername" required placeholder="identifiant">
                            </div>
                            <div class="form-group">
                                <label>Mot de passe *</label>
                                <input type="password" id="newPassword" required placeholder="mot de passe">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label>Nom *</label>
                                <input type="text" id="newNom" required placeholder="Nom">
                            </div>
                            <div class="form-group">
                                <label>Prénom *</label>
                                <input type="text" id="newPrenom" required placeholder="Prénom">
                            </div>
                            <div class="form-group">
                                <label>Département *</label>
                                <select id="newDepartement" required>
                                    <option value="">Sélectionner un département</option>
                                    <option value="ZoneA">Zone A</option>
                                    <option value="ZoneB">Zone B</option>
                                    <option value="ZoneC">Zone C</option>
                                    <option value="ZoneD">Zone D</option>
                                    <option value="ZoneE">Zone E</option>
                                    <option value="ZoneF">Zone F</option>
                                    <option value="ZoneG">Zone G</option>
                                    <option value="ZoneH">Zone H</option>
                                    <option value="ZoneI">Zone I</option>
                                    <option value="ZoneJ">Zone J</option>
                                </select>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Numéro de téléphone</label>
                                <input type="tel" id="newTelephone" placeholder="Numéro de téléphone">
                            </div>
                            <div class="form-group">
                                <label>Email</label>
                                <input type="email" id="newEmail" placeholder="Adresse email">
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group" id="activityField" style="display: none;">
                                <label>Activité du Chef *</label>
                                <select id="newActivity">
                                    <option value="recolte">Récolte</option>
                                    <option value="rabattage">Rabattage</option>
                                    <option value="élagage">Élagage</option>
                                    <option value="ronds">Ronds</option>
                                    <option value="spring">Spring</option>
                                    <option value="engrais">Engrais</option>
                                </select>
                            </div>
                            <div class="form-group" id="employeeActivityField">
                                <label>Activité de l'Employé *</label>
                                <select id="newEmployeeActivity" required>
                                    <option value="">Sélectionner une activité</option>
                                    <option value="recolte">Récolte</option>
                                    <option value="rabattage">Rabattage</option>
                                    <option value="élagage">Élagage</option>
                                    <option value="ronds">Ronds</option>
                                    <option value="spring">Spring</option>
                                    <option value="engrais">Engrais</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Couleur (hex)</label>
                                <input type="color" id="newColor" value="#ff8c00">
                            </div>
                        </div>
                        
                        <div style="margin-top: 1.5rem;">
                            <button type="submit" class="btn">Créer l'utilisateur</button>
                            <button type="button" class="btn btn-outline" onclick="showSection('adminUsers')" style="margin-left: 0.5rem;">Annuler</button>
                        </div>
                    </form>
                </div>
            </section>

            <!-- Admin Edit User Section -->
            <section id="adminEditUser" class="section">
                <div class="card">
                    <h3>Modifier l'utilisateur</h3>
                    <form id="editUserForm" onsubmit="handleEditUser(event)">
                        <input type="hidden" id="editUserId">
                        
                        <!-- Photo Upload -->
                        <div class="photo-upload-container">
                            <div id="editPhotoPreview" class="photo-placeholder">
                                👤
                            </div>
                            <input type="file" id="editPhotoInput" class="file-input" accept="image/*" onchange="previewEditPhoto(event)">
                            <label for="editPhotoInput" class="file-input-label">📷 Changer la photo</label>
                            <div style="font-size: 0.8rem; color: var(--text-light); margin-top: 0.5rem;">
                                Si aucune photo n'est choisie, un avatar avec les initiales sera généré
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Role *</label>
                                <select id="editUserRole" required onchange="toggleEditActivityField()">
                                    <option value="">Sélectionner un rôle</option>
                                    <option value="CHEF">CHEF</option>
                                    <option value="EMPLOYE">EMPLOYE</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Identifiant *</label>
                                <input type="text" id="editUsername" required placeholder="identifiant">
                            </div>
                            <div class="form-group">
                                <label>Mot de passe</label>
                                <input type="password" id="editPassword" placeholder="Laisser vide pour ne pas changer">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label>Nom *</label>
                                <input type="text" id="editNom" required placeholder="Nom">
                            </div>
                            <div class="form-group">
                                <label>Prénom *</label>
                                <input type="text" id="editPrenom" required placeholder="Prénom">
                            </div>
                            <div class="form-group">
                                <label>Département *</label>
                                <select id="editDepartement" required>
                                    <option value="">Sélectionner un département</option>
                                    <option value="ZoneA">Zone A</option>
                                    <option value="ZoneB">Zone B</option>
                                    <option value="ZoneC">Zone C</option>
                                    <option value="ZoneD">Zone D</option>
                                    <option value="ZoneE">Zone E</option>
                                    <option value="ZoneF">Zone F</option>
                                    <option value="ZoneG">Zone G</option>
                                    <option value="ZoneH">Zone H</option>
                                    <option value="ZoneI">Zone I</option>
                                    <option value="ZoneJ">Zone J</option>
                                </select>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Numéro de téléphone</label>
                                <input type="tel" id="editTelephone" placeholder="Numéro de téléphone">
                            </div>
                            <div class="form-group">
                                <label>Email</label>
                                <input type="email" id="editEmail" placeholder="Adresse email">
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group" id="editActivityField" style="display: none;">
                                <label>Activité du Chef *</label>
                                <select id="editActivity">
                                    <option value="recolte">Récolte</option>
                                    <option value="rabattage">Rabattage</option>
                                    <option value="élagage">Élagage</option>
                                    <option value="ronds">Ronds</option>
                                    <option value="spring">Spring</option>
                                    <option value="engrais">Engrais</option>
                                </select>
                            </div>
                            <div class="form-group" id="editEmployeeActivityField">
                                <label>Activité de l'Employé *</label>
                                <select id="editEmployeeActivity" required>
                                    <option value="">Sélectionner une activité</option>
                                    <option value="recolte">Récolte</option>
                                    <option value="rabattage">Rabattage</option>
                                    <option value="élagage">Élagage</option>
                                    <option value="ronds">Ronds</option>
                                    <option value="spring">Spring</option>
                                    <option value="engrais">Engrais</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Couleur (hex)</label>
                                <input type="color" id="editColor" value="#ff8c00">
                            </div>
                        </div>
                        
                        <div style="margin-top: 1.5rem;">
                            <button type="submit" class="btn">💾 Modifier l'utilisateur</button>
                            <button type="button" class="btn btn-outline" onclick="showSection('adminUsers')" style="margin-left: 0.5rem;">Annuler</button>
                        </div>
                    </form>
                </div>
            </section>

            <!-- Chef Actions Section -->
            <section id="chefActions" class="section">
                <div class="card">
                    <h3>Actions Chef d'Équipe</h3>
                    <div id="chefInfo" class="chef-info">
                        <!-- Chef information will be populated here -->
                    </div>
                    <p>Choisissez l'action que vous souhaitez effectuer :</p>
                    
                    <div class="action-buttons">
                        <button class="btn action-btn" onclick="showSection('chefPresence')">
                            <div style="font-size: 2rem; margin-bottom: 0.5rem;">📋</div>
                            <div><strong>Gestion des Présences</strong></div>
                            <div style="font-size: 0.9rem; opacity: 0.8; margin-top: 0.5rem;">Marquer les présences et absences</div>
                        </button>
                        
                        <button class="btn btn-chef action-btn" onclick="showSection('chefPointage')">
                            <div style="font-size: 2rem; margin-bottom: 0.5rem;">📝</div>
                            <div><strong>Pointage des Activités</strong></div>
                            <div style="font-size: 0.9rem; opacity: 0.8; margin-top: 0.5rem;">Renseigner les activités des présents</div>
                        </button>
                    </div>
                    
                    <div style="margin-top: 1.5rem;">
                        <button class="btn btn-outline" onclick="showSection('chefPointages')">📋 Voir mes pointages</button>
                    </div>
                </div>
            </section>

            <!-- Chef Presence Section -->
            <section id="chefPresence" class="section">
                <div class="card">
                    <h3>📋 Gestion des Présences - <span id="chefActivityBadge"></span></h3>
                    <p>Marquez les employés présents de votre activité. Les absents seront automatiquement enregistrés.</p>
                    
                    <div class="presence-section">
                        <div class="form-group">
                            <label>Date du pointage *</label>
                            <input type="date" id="presenceDate" required>
                        </div>
                        
                        <div class="employee-list" id="employeePresenceList">
                            <!-- Employees will be populated here -->
                        </div>
                        
                        <div style="margin-top: 1rem; text-align: center;">
                            <button class="btn" onclick="savePresences()">💾 Enregistrer les Présences</button>
                            <button class="btn btn-outline" onclick="showSection('chefActions')" style="margin-left: 0.5rem;">← Retour</button>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Chef Pointage Section -->
            <section id="chefPointage" class="section">
                <div class="card">
                    <h3>📝 Pointage des Activités - <span id="pointageActivityBadge"></span></h3>
                    <p>Renseignez les activités des employés marqués comme présents dans votre activité.</p>
                    
                    <div class="form-group">
                        <label>Date du pointage *</label>
                        <input type="date" id="pointageDate" required>
                    </div>
                    
                    <div id="pointageFormsContainer">
                        <!-- Pointage forms will be populated here -->
                    </div>

                    <!-- Section de notification -->
                    <div class="notification-section">
                        <h4>📤 Envoi des pointages</h4>
                        <p>Après enregistrement, vous pouvez envoyer les pointages aux employés concernés :</p>
                        
                        <div class="notification-buttons">
                            <button class="btn btn-email" onclick="sendPointagesByEmail()" id="emailBtn" disabled>
                                📧 Envoyer par Email
                            </button>
                            <button class="btn btn-whatsapp" onclick="sendPointagesByWhatsApp()" id="whatsappBtn" disabled>
                                💬 Envoyer par WhatsApp
                            </button>
                        </div>

                        <div id="sendingStatus" class="sending-status" style="display: none;">
                            <h5>Statut d'envoi :</h5>
                            <div id="statusList"></div>
                        </div>
                    </div>
                    
                    <div style="margin-top: 1.5rem;">
                        <button class="btn" onclick="saveAllPointages()">💾 Enregistrer Tous les Pointages</button>
                        <button class="btn btn-outline" onclick="showSection('chefActions')" style="margin-left: 0.5rem;">← Retour</button>
                    </div>
                </div>
            </section>

            <!-- Chef Pointages List Section -->
            <section id="chefPointages" class="section">
                <div class="card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                        <h3>Mes pointages - <span id="pointagesActivityBadge"></span></h3>
                        <div>
                            <button class="btn" onclick="showSection('chefActions')">📊 Retour aux actions</button>
                            <button class="btn btn-outline" onclick="searchChefPointages()" style="margin-left: 0.5rem;">🔍 Rechercher</button>
                        </div>
                    </div>

                    <!-- NOUVELLE SECTION D'EXPORT -->
                    <div class="export-section">
                        <h4>📤 Export des Pointages du Jour</h4>
                        <p>Exportez vos pointages d'aujourd'hui dans différents formats :</p>
                        
                        <div class="export-buttons">
                            <div class="export-btn" onclick="exportPointagesPDF()">
                                <div class="export-icon">📄</div>
                                <div class="export-title">PDF Professionnel</div>
                                <div class="export-description">Document formaté avec en-tête et totaux, idéal pour l'archivage</div>
                            </div>
                            
                            <div class="export-btn" onclick="exportPointagesExcel()">
                                <div class="export-icon">📊</div>
                                <div class="export-title">Excel Structuré</div>
                                <div class="export-description">Fichier tableur avec mise en forme pour analyse des données</div>
                            </div>
                            
                            <div class="export-btn" onclick="exportPointagesPNG()">
                                <div class="export-icon">🖼️</div>
                                <div class="export-title">Image PNG</div>
                                <div class="export-description">Capture d'écran haute qualité pour partage rapide</div>
                            </div>
                        </div>

                        <!-- Section WhatsApp -->
                        <div style="margin-top: 1.5rem;">
                            <h5>💬 Envoi par WhatsApp</h5>
                            <div class="whatsapp-input-section">
                                <div class="whatsapp-input-group">
                                    <input type="tel" id="whatsappNumber" class="whatsapp-input" 
                                           placeholder="Numéro WhatsApp (format international: +22501234567)" 
                                           pattern="^\+[0-9]{10,15}$">
                                    <button class="btn btn-whatsapp" onclick="sendPointagesViaWhatsApp()">
                                        💬 Envoyer
                                    </button>
                                </div>
                                <div class="whatsapp-example">
                                    Format requis: +22501234567 (indicatif pays + numéro)
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Pointages groupés par semaine -->
                    <div id="weeklyPointagesContainer">
                        <!-- Contenu généré dynamiquement -->
                    </div>
                </div>
            </section>

            <!-- Employee Pointages Section -->
            <section id="employeePointages" class="section">
                <div class="card">
                    <h3>Mes pointages</h3>
                    
                    <!-- Pointages groupés par semaine -->
                    <div id="employeeWeeklyPointagesContainer">
                        <!-- Contenu généré dynamiquement -->
                    </div>
                </div>
            </section>

            <!-- Employee Bulletins Section -->
            <section id="employeeBulletins" class="section">
                <div class="card">
                    <h3>Mes bulletins de paie</h3>
                    
                    <!-- Bulletins de paie -->
                    <div id="employeeBulletinsContainer">
                        <!-- Contenu généré dynamiquement -->
                    </div>
                </div>
            </section>

            <!-- Admin Paie Section -->
            <section id="adminPaie" class="section">
                <div class="card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                        <h3>💰 Gestion de la Paie</h3>
                        <div>
                            <button class="btn" onclick="genererBulletinsMensuels()">💰 Générer tous les bulletins</button>
                            <button class="btn btn-warning" onclick="showArchiveModal('bulletins')" style="margin-left: 0.5rem;">📦 Archiver sélection</button>
                        </div>
                    </div>

                    <!-- Sélection multiple -->
                    <div class="select-all-container">
                        <input type="checkbox" id="selectAllBulletins" onchange="toggleSelectAllBulletins()">
                        <label for="selectAllBulletins">Tout sélectionner</label>
                        <span class="selected-count" id="selectedBulletinsCount">0 sélectionné(s)</span>
                        <button class="btn btn-small btn-outline" onclick="clearBulletinsSelection()" style="margin-left: auto;">❌ Effacer</button>
                    </div>

                    <!-- Recherche avancée -->
                    <div class="search-box">
                        <input type="text" id="searchBulletin" class="search-input" placeholder="Rechercher par nom d'employé, période..." onkeyup="searchBulletins()">
                        <button class="btn btn-small" onclick="searchBulletins()">🔍 Rechercher</button>
                        <button class="btn btn-small btn-outline" onclick="clearBulletinSearch()">❌ Effacer</button>
                    </div>

                    <!-- Statistiques -->
                    <div class="stats-grid" id="paieStats">
                        <!-- Populated by JavaScript -->
                    </div>

                    <!-- Filtres -->
                    <div class="filters">
                        <div class="filter-group">
                            <label for="filterPaieMois">Mois :</label>
                            <select id="filterPaieMois" onchange="filterBulletins()">
                                <option value="">Tous les mois</option>
                                <!-- Options will be populated by JavaScript -->
                            </select>
                        </div>
                        <div class="filter-group">
                            <label for="filterPaieAnnee">Année :</label>
                            <select id="filterPaieAnnee" onchange="filterBulletins()">
                                <option value="">Toutes les années</option>
                                <!-- Options will be populated by JavaScript -->
                            </select>
                        </div>
                        <div class="filter-group">
                            <label for="filterPaieEmploye">Employé :</label>
                            <select id="filterPaieEmploye" onchange="filterBulletins()">
                                <option value="">Tous les employés</option>
                                <!-- Options will be populated by JavaScript -->
                            </select>
                        </div>
                        <div class="filter-group">
                            <label for="filterPaieArchived">Statut:</label>
                            <select id="filterPaieArchived" onchange="filterBulletins()">
                                <option value="non-archived">Non archivés</option>
                                <option value="archived">Archivés</option>
                                <option value="all">Tous</option>
                            </select>
                        </div>
                    </div>

                    <div class="table-container">
                        <table id="bulletinsTable">
                            <thead>
                                <tr>
                                    <th width="30px">
                                        <input type="checkbox" id="selectAllBulletinsHeader" onchange="toggleSelectAllBulletins()">
                                    </th>
                                    <th>ID</th>
                                    <th>Employé</th>
                                    <th>Période</th>
                                    <th>Salaire Brut</th>
                                    <th>Net à Payer</th>
                                    <th>Statut</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="bulletinsTableBody">
                                <!-- Populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- Bulletin Detail Section -->
            <section id="bulletinDetail" class="section">
                <div class="card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                        <h3>Détail du Bulletin de Paie</h3>
                        <div>
                            <button class="btn" onclick="imprimerBulletin()">🖨️ Imprimer</button>
                            <button class="btn btn-outline" onclick="goBackToPaie()" style="margin-left: 0.5rem;">← Retour</button>
                        </div>
                    </div>
                    
                    <div id="bulletinContent" class="bulletin-container">
                        <!-- Bulletin content will be populated here -->
                    </div>
                </div>
            </section>

            <!-- Admin Archives Section -->
            <section id="adminArchives" class="section">
                <div class="card">
                    <h3>📦 Archives</h3>
                    <p>Gestion des archives des bulletins de paie et fiches de pointage</p>
                    
                    <div class="archive-actions">
                        <button class="btn" onclick="showArchives('bulletins')">📋 Archives des Bulletins</button>
                        <button class="btn" onclick="showArchives('pointages')">📊 Archives des Pointages</button>
                        <button class="btn btn-warning" onclick="archiverDonneesAnciennes()">🔄 Archiver données anciennes</button>
                    </div>

                    <div id="archivesContent">
                        <!-- Content will be populated by JavaScript -->
                    </div>
                </div>
            </section>
        </main>
    </div>

    <!-- Modal d'archivage -->
    <div id="archiveModal" class="modal-overlay" style="display: none;">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modalTitle">Archiver des documents</h3>
                <button class="modal-close" onclick="closeArchiveModal()">×</button>
            </div>
            
            <div id="modalContent">
                <!-- Content populated by JavaScript -->
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.28/jspdf.plugin.autotable.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script>
        // Configuration Supabase
        const SUPABASE_URL = 'https://nvnxcwffhkhmrophvhbh.supabase.co';
        const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im52bnhjd2ZmaGtobXJvcGh2aGJoIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTk2OTQ5MDMsImV4cCI6MjA3NTI3MDkwM30.uXFtEd81k80VE6eEcBVvntmG1ymNycg6Nhuhv2K48YY';

        // Initialisation du client Supabase
        const supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

        // Configuration de la paie professionnelle en FCFA
        const CONFIG_PAIE_PRO = {
            // Salaire de base en FCFA
            salaireBase: 1100000, // 1,100,000 FCFA
            
            // Cotisations salariales (taux en %)
            cotisations: {
                csg: 9.20,
                crds: 0.50,
                secu: 13.10,
                retraite: 6.85,
                assedic: 3.45,
                transport: 2.40
            },
            
            // Cotisations patronales (taux en %)
            cotisationsPatronales: {
                secu: 16.65,
                accident: 2.50,
                retraite: 9.45,
                assedic: 4.45,
                formation: 1.60,
                transport: 5.00
            },
            
            // Plafonds en FCFA
            plafondSecu: 2000000,
            plafondTransport: 1100000
        };

        // Activities configuration
        const ACTIVITIES = {
            'recolte': 'Récolte',
            'rabattage': 'Rabattage',
            'élagage': 'Élagage',
            'ronds': 'Ronds',
            'spring': 'Spring',
            'engrais': 'Engrais'
        };

        // Départements configuration
        const DEPARTEMENTS = [
            'ZoneA', 'ZoneB', 'ZoneC', 'ZoneD', 'ZoneE', 
            'ZoneF', 'ZoneG', 'ZoneH', 'ZoneI', 'ZoneJ'
        ];

        // Variables globales pour la navigation par semaine
        let currentWeekOffset = 0;
        let currentEmployeeWeekOffset = 0;
        let selectedDate = new Date().toISOString().split('T')[0];
        let lastSavedPointages = [];

        // Variables pour la sélection multiple
        let selectedPointages = new Set();
        let selectedBulletins = new Set();

        // Variables pour les filtres et recherche
        let currentPointages = [];
        let currentBulletins = [];

        // =============================================
        // FONCTIONS SUPABASE CORRIGÉES
        // =============================================

        // Fonctions pour gérer les utilisateurs
        async function getUsers() {
            try {
                const { data, error } = await supabase
                    .from('users')
                    .select('*')
                    .order('id', { ascending: true });
                
                if (error) {
                    console.error('Erreur lors de la récupération des utilisateurs:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la récupération des utilisateurs:', error);
                throw error;
            }
        }

        async function createUser(userData) {
            try {
                const { data, error } = await supabase
                    .from('users')
                    .insert([userData])
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la création de l\'utilisateur:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data ? data[0] : null;
            } catch (error) {
                console.error('Erreur critique lors de la création de l\'utilisateur:', error);
                throw error;
            }
        }

        async function updateUser(userId, userData) {
            try {
                const { data, error } = await supabase
                    .from('users')
                    .update(userData)
                    .eq('id', userId)
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la modification de l\'utilisateur:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data ? data[0] : null;
            } catch (error) {
                console.error('Erreur critique lors de la modification de l\'utilisateur:', error);
                throw error;
            }
        }

        async function deleteUser(userId) {
            try {
                const { error } = await supabase
                    .from('users')
                    .delete()
                    .eq('id', userId);
                
                if (error) {
                    console.error('Erreur lors de la suppression de l\'utilisateur:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return true;
            } catch (error) {
                console.error('Erreur critique lors de la suppression de l\'utilisateur:', error);
                throw error;
            }
        }

        // Fonctions pour gérer les pointages
        async function getPointages() {
            try {
                const { data, error } = await supabase
                    .from('pointages')
                    .select('*')
                    .order('created_at', { ascending: false });
                
                if (error) {
                    console.error('Erreur lors de la récupération des pointages:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la récupération des pointages:', error);
                throw error;
            }
        }

        async function getArchivedPointages() {
            try {
                const { data, error } = await supabase
                    .from('pointages')
                    .select('*')
                    .eq('archived', true)
                    .order('created_at', { ascending: false });
                
                if (error) {
                    console.error('Erreur lors de la récupération des pointages archivés:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la récupération des pointages archivés:', error);
                throw error;
            }
        }

        async function createPointage(pointageData) {
            try {
                const { data, error } = await supabase
                    .from('pointages')
                    .insert([pointageData])
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la création du pointage:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data ? data[0] : null;
            } catch (error) {
                console.error('Erreur critique lors de la création du pointage:', error);
                throw error;
            }
        }

        async function createMultiplePointages(pointagesData) {
            try {
                const { data, error } = await supabase
                    .from('pointages')
                    .insert(pointagesData)
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la création des pointages:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la création des pointages:', error);
                throw error;
            }
        }

        async function updatePointage(pointageId, updates) {
            try {
                const { data, error } = await supabase
                    .from('pointages')
                    .update(updates)
                    .eq('id', pointageId)
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la mise à jour du pointage:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data ? data[0] : null;
            } catch (error) {
                console.error('Erreur critique lors de la mise à jour du pointage:', error);
                throw error;
            }
        }

        // Fonctions pour gérer les bulletins de paie
        async function getBulletins() {
            try {
                const { data, error } = await supabase
                    .from('bulletins')
                    .select('*')
                    .order('date_generation', { ascending: false });
                
                if (error) {
                    console.error('Erreur lors de la récupération des bulletins:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la récupération des bulletins:', error);
                throw error;
            }
        }

        async function getBulletinsByEmployee(employeeId) {
            try {
                const { data, error } = await supabase
                    .from('bulletins')
                    .select('*')
                    .eq('employee_id', employeeId)
                    .order('date_generation', { ascending: false });
                
                if (error) {
                    console.error('Erreur lors de la récupération des bulletins employé:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la récupération des bulletins employé:', error);
                throw error;
            }
        }

        async function getArchivedBulletins() {
            try {
                const { data, error } = await supabase
                    .from('bulletins')
                    .select('*')
                    .eq('archived', true)
                    .order('date_generation', { ascending: false });
                
                if (error) {
                    console.error('Erreur lors de la récupération des bulletins archivés:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data || [];
            } catch (error) {
                console.error('Erreur critique lors de la récupération des bulletins archivés:', error);
                throw error;
            }
        }

        async function createBulletin(bulletinData) {
            try {
                const { data, error } = await supabase
                    .from('bulletins')
                    .insert([bulletinData])
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la création du bulletin:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data ? data[0] : null;
            } catch (error) {
                console.error('Erreur critique lors de la création du bulletin:', error);
                throw error;
            }
        }

        async function updateBulletin(bulletinId, updates) {
            try {
                const { data, error } = await supabase
                    .from('bulletins')
                    .update(updates)
                    .eq('id', bulletinId)
                    .select();
                
                if (error) {
                    console.error('Erreur lors de la mise à jour du bulletin:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                return data ? data[0] : null;
            } catch (error) {
                console.error('Erreur critique lors de la mise à jour du bulletin:', error);
                throw error;
            }
        }

        // Fonctions pour gérer les présences
        async function getPresences(date) {
            try {
                const { data, error } = await supabase
                    .from('presences')
                    .select('*')
                    .eq('date', date);
                
                if (error) {
                    console.error('Erreur lors de la récupération des présences:', error);
                    throw new Error(`Erreur Supabase: ${error.message}`);
                }
                
                const presencesMap = {};
                if (data) {
                    data.forEach(p => {
                        presencesMap[p.employee_id] = p.status;
                    });
                }
                return presencesMap;
            } catch (error) {
                console.error('Erreur critique lors de la récupération des présences:', error);
                throw error;
            }
        }

        async function savePresencesForDate(date, presencesMap) {
            try {
                // Supprimer les anciennes présences pour cette date
                const { error: deleteError } = await supabase
                    .from('presences')
                    .delete()
                    .eq('date', date);
                
                if (deleteError) {
                    console.error('Erreur lors de la suppression des anciennes présences:', deleteError);
                    throw new Error(`Erreur Supabase: ${deleteError.message}`);
                }
                
                // Insérer les nouvelles présences
                const presencesData = Object.keys(presencesMap).map(employeeId => ({
                    date: date,
                    employee_id: parseInt(employeeId),
                    status: presencesMap[employeeId]
                }));
                
                if (presencesData.length > 0) {
                    const { data, error } = await supabase
                        .from('presences')
                        .insert(presencesData)
                        .select();
                    
                    if (error) {
                        console.error('Erreur lors de l\'enregistrement des présences:', error);
                        throw new Error(`Erreur Supabase: ${error.message}`);
                    }
                }
                return true;
            } catch (error) {
                console.error('Erreur critique lors de l\'enregistrement des présences:', error);
                throw error;
            }
        }

        // =============================================
        // FONCTIONS D'EXPORT DES POINTAGES (CHEF)
        // =============================================

        // Fonction pour obtenir les pointages du jour
        async function getTodayPointages() {
            try {
                const user = getCurrentUser();
                if (!user || user.role !== 'CHEF') {
                    throw new Error('Accès réservé aux chefs');
                }

                const today = new Date().toISOString().split('T')[0];
                
                const pointages = await getPointages();
                
                // Filtrer les pointages du chef pour aujourd'hui
                const todayPointages = pointages.filter(p => 
                    p.chef_id === user.id && 
                    p.date === today
                );

                // Enrichir avec les noms des employés
                const users = await getUsers();
                const enrichedPointages = todayPointages.map(pointage => {
                    const employee = users.find(u => u.id === pointage.employee_id);
                    return {
                        ...pointage,
                        employee_name: employee ? `${employee.prenom} ${employee.nom}` : 'N/A'
                    };
                });

                return enrichedPointages;
            } catch (error) {
                console.error('Erreur lors de la récupération des pointages du jour:', error);
                throw error;
            }
        }

        // Fonction pour générer le tableau des pointages du jour
        function generateTodayPointagesTable(pointages) {
            if (!pointages || pointages.length === 0) {
                return '<p style="text-align: center; padding: 2rem; color: var(--text-light);">Aucun pointage trouvé pour aujourd\'hui</p>';
            }

            const user = getCurrentUser();
            const today = new Date().toLocaleDateString('fr-FR');
            
            let html = `
                <div style="text-align: center; margin-bottom: 1rem; padding: 1rem; background: #f8fafc; border-radius: 8px;">
                    <h3 style="color: var(--chef-color); margin-bottom: 0.5rem;">Pointages du ${today}</h3>
                    <div style="display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap;">
                        <div><strong>Chef:</strong> ${user.prenom} ${user.nom}</div>
                        <div><strong>Activité:</strong> ${getActivityName(user.activity)}</div>
                        <div><strong>Total:</strong> ${pointages.length} pointage(s)</div>
                    </div>
                </div>
                <div class="table-container">
                    <table class="export-table">
                        <thead>
                            <tr>
                                <th>Employé</th>
                                <th>Activité</th>
                                <th>Bloc</th>
                                <th>Sous-quantités</th>
                                <th>Quantité Totale</th>
                                <th>Prix Unitaire</th>
                                <th>Prix Total</th>
                            </tr>
                        </thead>
                        <tbody>
            `;

            let totalGeneral = 0;
            
            pointages.forEach(pointage => {
                const sousQuantites = pointage.sub_quantities && pointage.sub_quantities.length > 0 
                    ? pointage.sub_quantities.join(' + ') 
                    : '-';
                
                const prixTotal = pointage.total_price || 0;
                totalGeneral += prixTotal;

                html += `
                    <tr>
                        <td>${pointage.employee_name}</td>
                        <td>${getActivityName(pointage.activity)}</td>
                        <td>${pointage.bloc || '-'}</td>
                        <td>${sousQuantites}</td>
                        <td>${pointage.qty_total || 0}</td>
                        <td>${formatFCFA(pointage.unit_price || 0)}</td>
                        <td style="font-weight: bold;">${formatFCFA(prixTotal)}</td>
                    </tr>
                `;
            });

            html += `
                        </tbody>
                        <tfoot>
                            <tr style="background: var(--chef-color); color: white; font-weight: bold;">
                                <td colspan="6" style="text-align: right;">Total Général:</td>
                                <td>${formatFCFA(totalGeneral)}</td>
                            </tr>
                        </tfoot>
                    </table>
                </div>
            `;

            return html;
        }

        // 📄 EXPORT PDF - Format professionnel avec en-tête et totaux
        async function exportPointagesPDF() {
            try {
                showAlert('Génération du PDF en cours...', 'info');
                
                const pointages = await getTodayPointages();
                if (pointages.length === 0) {
                    showAlert('Aucun pointage trouvé pour aujourd\'hui', 'warning');
                    return;
                }

                const { jsPDF } = window.jspdf;
                const doc = new jsPDF();

                // En-tête professionnel
                const user = getCurrentUser();
                const today = new Date().toLocaleDateString('fr-FR');
                
                // Logo et titre
                doc.setFontSize(16);
                doc.setTextColor(44, 123, 229);
                doc.text('MKJ SERVICE - Pointages du Jour', 105, 15, { align: 'center' });
                
                // Informations détaillées
                doc.setFontSize(10);
                doc.setTextColor(100, 100, 100);
                doc.text(`Date: ${today} | Chef: ${user.prenom} ${user.nom}`, 105, 22, { align: 'center' });
                doc.text(`Activité: ${getActivityName(user.activity)} | Total: ${pointages.length} pointage(s)`, 105, 27, { align: 'center' });

                // Préparer les données du tableau
                const tableData = pointages.map(pointage => {
                    const sousQuantites = pointage.sub_quantities && pointage.sub_quantities.length > 0 
                        ? pointage.sub_quantities.join(' + ') 
                        : '-';
                    
                    return [
                        pointage.employee_name,
                        getActivityName(pointage.activity),
                        pointage.bloc || '-',
                        sousQuantites,
                        pointage.qty_total || 0,
                        formatFCFA(pointage.unit_price || 0),
                        formatFCFA(pointage.total_price || 0)
                    ];
                });

                // Calcul du total général
                const totalGeneral = pointages.reduce((sum, p) => sum + (p.total_price || 0), 0);

                // Générer le tableau avec style professionnel
                doc.autoTable({
                    startY: 35,
                    head: [['Employé', 'Activité', 'Bloc', 'Sous-quantités', 'Quantité', 'Prix Unitaire', 'Prix Total']],
                    body: tableData,
                    theme: 'grid',
                    headStyles: {
                        fillColor: [255, 140, 0], // Orange chef
                        textColor: [255, 255, 255],
                        fontStyle: 'bold',
                        fontSize: 9
                    },
                    alternateRowStyles: {
                        fillColor: [245, 245, 245]
                    },
                    styles: {
                        fontSize: 8,
                        cellPadding: 2,
                        lineColor: [200, 200, 200],
                        lineWidth: 0.1
                    },
                    margin: { top: 35 },
                    didDrawPage: function (data) {
                        // Ajouter le total général en bas de la dernière page
                        if (data.pageNumber === data.pageCount) {
                            const finalY = data.cursor.y + 10;
                            doc.setFontSize(10);
                            doc.setTextColor(255, 140, 0);
                            doc.setFont(undefined, 'bold');
                            doc.text('TOTAL GÉNÉRAL:', 140, finalY);
                            doc.text(formatFCFA(totalGeneral), 190, finalY, { align: 'right' });
                        }
                    }
                });

                // Pied de page professionnel
                const pageCount = doc.internal.getNumberOfPages();
                for (let i = 1; i <= pageCount; i++) {
                    doc.setPage(i);
                    doc.setFontSize(8);
                    doc.setTextColor(150, 150, 150);
                    doc.text(`Page ${i} / ${pageCount} - Généré le ${new Date().toLocaleString('fr-FR')} - MKJ SERVICE`, 105, doc.internal.pageSize.height - 10, { align: 'center' });
                }

                // Télécharger le PDF avec nom de fichier professionnel
                const fileName = `Pointages_${today.replace(/\//g, '-')}_${user.prenom}_${user.nom}.pdf`;
                doc.save(fileName);
                
                showAlert('PDF généré avec succès', 'success');
                
            } catch (error) {
                console.error('Erreur lors de l\'export PDF:', error);
                showAlert('Erreur lors de la génération du PDF: ' + error.message, 'error');
            }
        }

        // 📊 EXPORT EXCEL - Fichier structuré avec mise en forme
        async function exportPointagesExcel() {
            try {
                showAlert('Génération du fichier Excel en cours...', 'info');
                
                const pointages = await getTodayPointages();
                if (pointages.length === 0) {
                    showAlert('Aucun pointage trouvé pour aujourd\'hui', 'warning');
                    return;
                }

                const user = getCurrentUser();
                const today = new Date().toLocaleDateString('fr-FR');

                // Préparer les données avec structure professionnelle
                const data = [
                    // En-tête principal
                    ['MKJ SERVICE - POINTAGES DU JOUR'],
                    [`Date: ${today} | Chef: ${user.prenom} ${user.nom}`],
                    [`Activité: ${getActivityName(user.activity)} | Total pointages: ${pointages.length}`],
                    [], // Ligne vide
                    // En-tête du tableau
                    ['Employé', 'Activité', 'Bloc', 'Sous-quantités', 'Quantité Totale', 'Prix Unitaire', 'Prix Total']
                ];

                let totalGeneral = 0;
                
                // Données des pointages
                pointages.forEach(pointage => {
                    const sousQuantites = pointage.sub_quantities && pointage.sub_quantities.length > 0 
                        ? pointage.sub_quantities.join(' + ') 
                        : '-';
                    
                    const prixTotal = pointage.total_price || 0;
                    totalGeneral += prixTotal;

                    data.push([
                        pointage.employee_name,
                        getActivityName(pointage.activity),
                        pointage.bloc || '-',
                        sousQuantites,
                        pointage.qty_total || 0,
                        pointage.unit_price || 0,
                        prixTotal
                    ]);
                });

                // Ligne de total général
                data.push([]); // Ligne vide
                data.push(['TOTAL GÉNÉRAL', '', '', '', '', '', totalGeneral]);

                // Créer le workbook
                const ws = XLSX.utils.aoa_to_sheet(data);
                const wb = XLSX.utils.book_new();
                XLSX.utils.book_append_sheet(wb, ws, 'Pointages');

                // Appliquer les styles professionnels
                if (ws['!ref']) {
                    const range = XLSX.utils.decode_range(ws['!ref']);
                    
                    // Fusionner les cellules du titre
                    if (!ws['!merges']) ws['!merges'] = [];
                    ws['!merges'].push({ s: { r: 0, c: 0 }, e: { r: 0, c: 6 } });
                    ws['!merges'].push({ s: { r: 1, c: 0 }, e: { r: 1, c: 6 } });
                    ws['!merges'].push({ s: { r: 2, c: 0 }, e: { r: 2, c: 6 } });

                    // Style de l'en-tête principal
                    for (let C = range.s.c; C <= range.e.c; ++C) {
                        const cell_address = { c: C, r: 0 };
                        const cell_ref = XLSX.utils.encode_cell(cell_address);
                        if (!ws[cell_ref]) continue;
                        ws[cell_ref].s = {
                            font: { sz: 14, bold: true, color: { rgb: "2C7BE5" } },
                            alignment: { horizontal: "center" },
                            fill: { fgColor: { rgb: "F8FAFC" } }
                        };
                    }

                    // Style des sous-titres
                    for (let R = 1; R <= 2; R++) {
                        for (let C = range.s.c; C <= range.e.c; ++C) {
                            const cell_address = { c: C, r: R };
                            const cell_ref = XLSX.utils.encode_cell(cell_address);
                            if (!ws[cell_ref]) continue;
                            ws[cell_ref].s = {
                                font: { sz: 10, color: { rgb: "666666" } },
                                alignment: { horizontal: "center" }
                            };
                        }
                    }

                    // Style de l'en-tête du tableau
                    for (let C = range.s.c; C <= range.e.c; ++C) {
                        const cell_address = { c: C, r: 4 };
                        const cell_ref = XLSX.utils.encode_cell(cell_address);
                        if (!ws[cell_ref]) continue;
                        ws[cell_ref].s = {
                            fill: { fgColor: { rgb: "FF8C00" } },
                            font: { bold: true, color: { rgb: "FFFFFF" } },
                            border: {
                                top: { style: "thin", color: { rgb: "000000" } },
                                left: { style: "thin", color: { rgb: "000000" } },
                                bottom: { style: "thin", color: { rgb: "000000" } },
                                right: { style: "thin", color: { rgb: "000000" } }
                            }
                        };
                    }

                    // Style des données du tableau
                    for (let R = 5; R <= range.e.r - 2; R++) {
                        for (let C = range.s.c; C <= range.e.c; ++C) {
                            const cell_address = { c: C, r: R };
                            const cell_ref = XLSX.utils.encode_cell(cell_address);
                            if (!ws[cell_ref]) continue;
                            ws[cell_ref].s = {
                                border: {
                                    top: { style: "thin", color: { rgb: "E2E8F0" } },
                                    left: { style: "thin", color: { rgb: "E2E8F0" } },
                                    bottom: { style: "thin", color: { rgb: "E2E8F0" } },
                                    right: { style: "thin", color: { rgb: "E2E8F0" } }
                                }
                            };
                        }
                    }

                    // Style du total général
                    const lastRow = range.e.r;
                    for (let C = range.s.c; C <= range.e.c; ++C) {
                        const cell_address = { c: C, r: lastRow };
                        const cell_ref = XLSX.utils.encode_cell(cell_address);
                        if (!ws[cell_ref]) continue;
                        ws[cell_ref].s = {
                            fill: { fgColor: { rgb: "FF8C00" } },
                            font: { bold: true, color: { rgb: "FFFFFF" } },
                            border: {
                                top: { style: "medium", color: { rgb: "000000" } },
                                bottom: { style: "medium", color: { rgb: "000000" } }
                            }
                        };
                    }

                    // Ajuster la largeur des colonnes automatiquement
                    ws['!cols'] = [
                        { wch: 25 }, // Employé
                        { wch: 15 }, // Activité
                        { wch: 12 }, // Bloc
                        { wch: 20 }, // Sous-quantités
                        { wch: 15 }, // Quantité
                        { wch: 15 }, // Prix Unitaire
                        { wch: 15 }  // Prix Total
                    ];
                }

                // Générer et télécharger le fichier
                const fileName = `Pointages_${today.replace(/\//g, '-')}_${user.prenom}_${user.nom}.xlsx`;
                XLSX.writeFile(wb, fileName);
                
                showAlert('Fichier Excel généré avec succès', 'success');
                
            } catch (error) {
                console.error('Erreur lors de l\'export Excel:', error);
                showAlert('Erreur lors de la génération du fichier Excel: ' + error.message, 'error');
            }
        }

        // 🖼️ EXPORT PNG - Capture d'écran du tableau
        async function exportPointagesPNG() {
            try {
                showAlert('Génération de l\'image en cours...', 'info');
                
                const pointages = await getTodayPointages();
                if (pointages.length === 0) {
                    showAlert('Aucun pointage trouvé pour aujourd\'hui', 'warning');
                    return;
                }

                // Créer un élément temporaire pour le rendu haute qualité
                const tempDiv = document.createElement('div');
                tempDiv.style.cssText = `
                    position: fixed;
                    left: -10000px;
                    top: -10000px;
                    width: 900px;
                    background: white;
                    padding: 25px;
                    border: 3px solid #2c7be5;
                    border-radius: 12px;
                    font-family: 'Segoe UI', Arial, sans-serif;
                    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
                `;

                const tableHTML = generateTodayPointagesTable(pointages);
                tempDiv.innerHTML = tableHTML;
                document.body.appendChild(tempDiv);

                // Convertir en image haute résolution
                const canvas = await html2canvas(tempDiv, {
                    scale: 3, // Haute résolution
                    useCORS: true,
                    allowTaint: true,
                    backgroundColor: '#ffffff',
                    logging: false,
                    quality: 1
                });

                // Nettoyer
                document.body.removeChild(tempDiv);

                // Convertir en blob et télécharger
                canvas.toBlob(function(blob) {
                    const link = document.createElement('a');
                    const user = getCurrentUser();
                    const today = new Date().toLocaleDateString('fr-FR').replace(/\//g, '-');
                    
                    link.download = `Pointages_${today}_${user.prenom}_${user.nom}.png`;
                    link.href = URL.createObjectURL(blob);
                    link.click();
                    URL.revokeObjectURL(link.href);
                }, 'image/png', 1.0);

                showAlert('Image PNG générée avec succès', 'success');
                
            } catch (error) {
                console.error('Erreur lors de l\'export PNG:', error);
                showAlert('Erreur lors de la génération de l\'image: ' + error.message, 'error');
            }
        }

        // 💬 WHATSAPP - Envoi direct avec message formaté
        async function sendPointagesViaWhatsApp() {
            try {
                const phoneNumber = document.getElementById('whatsappNumber').value.trim();
                
                if (!phoneNumber) {
                    showAlert('Veuillez entrer un numéro WhatsApp', 'error');
                    return;
                }

                // Validation du format international
                const phoneRegex = /^\+[0-9]{10,15}$/;
                if (!phoneRegex.test(phoneNumber)) {
                    showAlert('Format de numéro invalide. Utilisez le format international: +22501234567', 'error');
                    return;
                }

                showAlert('Préparation de l\'envoi WhatsApp...', 'info');

                const pointages = await getTodayPointages();
                if (pointages.length === 0) {
                    showAlert('Aucun pointage trouvé pour aujourd\'hui', 'warning');
                    return;
                }

                const user = getCurrentUser();
                const today = new Date().toLocaleDateString('fr-FR');
                
                // Créer le message WhatsApp formaté professionnellement
                let message = `*🌴 MKJ SERVICE - POINTAGES DU JOUR*\\n\\n`;
                
                // En-tête informatif
                message += `*📅 Date :* ${today}\\n`;
                message += `*👨‍💼 Chef :* ${user.prenom} ${user.nom}\\n`;
                message += `*🔧 Activité :* ${getActivityName(user.activity)}\\n`;
                message += `*📊 Total pointages :* ${pointages.length}\\n\\n`;
                
                message += `*📋 DÉTAIL DES POINTAGES :*\\n\\n`;

                let totalGeneral = 0;
                let index = 1;
                
                // Détail de chaque pointage
                pointages.forEach(pointage => {
                    const sousQuantites = pointage.sub_quantities && pointage.sub_quantities.length > 0 
                        ? pointage.sub_quantities.join(' + ') 
                        : '-';
                    
                    const prixTotal = pointage.total_price || 0;
                    totalGeneral += prixTotal;

                    message += `*${index}. ${pointage.employee_name}*\\n`;
                    message += `   🎯 Activité : ${getActivityName(pointage.activity)}\\n`;
                    message += `   📍 Bloc : ${pointage.bloc || '-'}\\n`;
                    message += `   📦 Sous-quantités : ${sousQuantites}\\n`;
                    message += `   ⚖️ Quantité : ${pointage.qty_total || 0}\\n`;
                    message += `   💰 Prix unitaire : ${formatFCFA(pointage.unit_price || 0)}\\n`;
                    message += `   🏷️ Prix total : ${formatFCFA(prixTotal)}\\n\\n`;
                    
                    index++;
                });

                // Résumé général
                message += `*💰 RÉSUMÉ GÉNÉRAL*\\n`;
                message += `━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\\n`;
                message += `*Nombre d'employés :* ${pointages.length}\\n`;
                message += `*Total général :* ${formatFCFA(totalGeneral)}\\n\\n`;
                
                message += `_📱 Généré automatiquement par MKJ SERVICE_\\n`;
                message += `_🕐 ${new Date().toLocaleString('fr-FR')}_`;

                // Encoder le message pour URL (échapper les caractères spéciaux)
                const encodedMessage = encodeURIComponent(message);
                const whatsappUrl = `https://wa.me/${phoneNumber.replace('+', '')}?text=${encodedMessage}`;

                // Ouvrir WhatsApp dans un nouvel onglet
                window.open(whatsappUrl, '_blank');
                
                showAlert('WhatsApp ouvert avec le message pré-rempli', 'success');
                
            } catch (error) {
                console.error('Erreur lors de l\'envoi WhatsApp:', error);
                showAlert('Erreur lors de l\'envoi WhatsApp: ' + error.message, 'error');
            }
        }

        // =============================================
        // FONCTIONS PRINCIPALES DE L'APPLICATION
        // =============================================

        // Fonctions d'authentification
        async function login(username, password) {
            try {
                const users = await getUsers();
                const user = users.find(u => u.username === username && u.password === password);
                
                if (user) {
                    localStorage.setItem('mkj_current_user', JSON.stringify(user));
                    updateUIForUser(user);
                    showSection('dashboard');
                    showAlert('Connexion réussie!', 'success');
                    return true;
                }
                return false;
            } catch (error) {
                console.error('Erreur de connexion:', error);
                showAlert('Erreur de connexion: ' + error.message, 'error');
                return false;
            }
        }

        function logout() {
            localStorage.removeItem('mkj_current_user');
            updateUIForUser(null);
            showSection('home');
            showAlert('Déconnexion réussie', 'success');
        }

        function getCurrentUser() {
            const userStr = localStorage.getItem('mkj_current_user');
            return userStr ? JSON.parse(userStr) : null;
        }

        // Fonctions pour les sous-quantités
        function addSubQuantity(employeeId) {
            const container = document.getElementById(`subQuantities-${employeeId}`);
            const rowCount = container.querySelectorAll('.sub-quantity-row').length;
            
            const row = document.createElement('div');
            row.className = 'sub-quantity-row';
            row.innerHTML = `
                <input type="number" class="sub-quantity-input" placeholder="Quantité" min="0" step="0.01" 
                       oninput="updateSubQuantityTotal(${employeeId})">
                <button type="button" class="btn btn-small btn-danger" onclick="this.parentElement.remove(); updateSubQuantityTotal(${employeeId})">❌</button>
            `;
            
            container.appendChild(row);
        }

        function updateSubQuantityTotal(employeeId) {
            const container = document.getElementById(`subQuantities-${employeeId}`);
            const inputs = container.querySelectorAll('.sub-quantity-input');
            const totalElement = document.getElementById(`subQuantityTotal-${employeeId}`);
            const qtyTotalInput = document.getElementById(`qty-${employeeId}`);
            
            let total = 0;
            inputs.forEach(input => {
                total += parseFloat(input.value) || 0;
            });
            
            totalElement.textContent = `Total: ${total}`;
            qtyTotalInput.value = total;
            
            // Mettre à jour le prix total
            const unitPriceInput = document.getElementById(`unitPrice-${employeeId}`);
            const totalPriceInput = document.getElementById(`totalPrice-${employeeId}`);
            const unitPrice = parseFloat(unitPriceInput.value) || 0;
            totalPriceInput.value = (total * unitPrice).toFixed(2);
        }

        function getSubQuantities(employeeId) {
            const container = document.getElementById(`subQuantities-${employeeId}`);
            const inputs = container.querySelectorAll('.sub-quantity-input');
            const quantities = [];
            
            inputs.forEach(input => {
                if (input.value && parseFloat(input.value) > 0) {
                    quantities.push(parseFloat(input.value));
                }
            });
            
            return quantities;
        }

        function formatSubQuantities(quantities) {
            if (!quantities || quantities.length === 0) return '';
            return quantities.join('+');
        }

        // Fonctions utilitaires
        function showSection(sectionId) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            
            const targetSection = document.getElementById(sectionId);
            if (targetSection) {
                targetSection.classList.add('active');
                
                switch(sectionId) {
                    case 'dashboard':
                        loadDashboard();
                        break;
                    case 'profile':
                        loadProfile();
                        break;
                    case 'adminUsers':
                        loadUsersTable();
                        break;
                    case 'adminPointages':
                        loadAdminPointages();
                        break;
                    case 'adminPaie':
                        loadBulletinsTable();
                        break;
                    case 'chefActions':
                        loadChefActions();
                        break;
                    case 'chefPresence':
                        loadPresenceManagement();
                        break;
                    case 'chefPointage':
                        loadPointageManagement();
                        break;
                    case 'chefPointages':
                        loadChefPointages();
                        break;
                    case 'employeePointages':
                        loadEmployeePointages();
                        break;
                    case 'employeeBulletins':
                        loadEmployeeBulletins();
                        break;
                    case 'adminArchives':
                        showArchives('bulletins');
                        break;
                }
            }
        }

        function showLogin(role) {
            document.getElementById('loginTitle').textContent = `Connexion - ${role}`;
            showSection('login');
        }

        function updateUIForUser(user) {
            const navDashboard = document.getElementById('navDashboard');
            const navProfile = document.getElementById('navProfile');
            const navArchives = document.getElementById('navArchives');
            const navLogout = document.getElementById('navLogout');
            const header = document.getElementById('appHeader');

            if (user) {
                navDashboard.style.display = 'block';
                navProfile.style.display = 'block';
                navLogout.style.display = 'block';
                
                if (user.role === 'ADMINISTRATEUR') {
                    navArchives.style.display = 'block';
                } else {
                    navArchives.style.display = 'none';
                }
                
                header.style.background = user.color;
            } else {
                navDashboard.style.display = 'none';
                navProfile.style.display = 'none';
                navArchives.style.display = 'none';
                navLogout.style.display = 'none';
                header.style.background = '';
            }
        }

        function showAlert(message, type = 'success') {
            const alertsContainer = document.getElementById('alertsContainer');
            const alert = document.createElement('div');
            alert.className = `alert ${type}`;
            alert.innerHTML = `
                <span>${type === 'success' ? '✓' : type === 'error' ? '⚠' : 'ℹ'}</span>
                ${message}
            `;
            
            alertsContainer.appendChild(alert);
            
            setTimeout(() => {
                alert.remove();
            }, 5000);
        }

        // Activity functions
        function getActivityName(activityKey) {
            return ACTIVITIES[activityKey] || activityKey;
        }

        function createActivityBadge(activity) {
            return `<span class="activity-badge">${getActivityName(activity)}</span>`;
        }

        // Form functions
        function toggleActivityField() {
            const role = document.getElementById('userRole').value;
            const activityField = document.getElementById('activityField');
            const employeeActivityField = document.getElementById('employeeActivityField');
            
            if (role === 'CHEF') {
                activityField.style.display = 'block';
                employeeActivityField.style.display = 'none';
                document.getElementById('newActivity').required = true;
                document.getElementById('newEmployeeActivity').required = false;
            } else if (role === 'EMPLOYE') {
                activityField.style.display = 'none';
                employeeActivityField.style.display = 'block';
                document.getElementById('newActivity').required = false;
                document.getElementById('newEmployeeActivity').required = true;
            } else {
                activityField.style.display = 'none';
                employeeActivityField.style.display = 'none';
                document.getElementById('newActivity').required = false;
                document.getElementById('newEmployeeActivity').required = false;
            }
        }

        // Event Handlers
        function handleLogin(event) {
            event.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (login(username, password)) {
                document.getElementById('username').value = '';
                document.getElementById('password').value = '';
            } else {
                showAlert('Identifiant ou mot de passe incorrect', 'error');
            }
        }

        async function handleCreateUser(event) {
            event.preventDefault();
            
            try {
                const photoData = await getPhotoData();
                const role = document.getElementById('userRole').value;
                
                const newUser = {
                    username: document.getElementById('newUsername').value,
                    password: document.getElementById('newPassword').value,
                    role: role,
                    color: document.getElementById('newColor').value,
                    nom: document.getElementById('newNom').value,
                    prenom: document.getElementById('newPrenom').value,
                    departement: document.getElementById('newDepartement').value,
                    telephone: document.getElementById('newTelephone').value,
                    email: document.getElementById('newEmail').value,
                    activity: role === 'CHEF' ? document.getElementById('newActivity').value : 
                             role === 'EMPLOYE' ? document.getElementById('newEmployeeActivity').value : null,
                    photo: photoData
                };

                const users = await getUsers();
                
                if (users.find(u => u.username === newUser.username)) {
                    showAlert('Cet identifiant est déjà utilisé', 'error');
                    return;
                }

                const createdUser = await createUser(newUser);
                
                if (createdUser) {
                    document.getElementById('createUserForm').reset();
                    document.getElementById('photoPreview').innerHTML = '👤';
                    document.getElementById('photoPreview').className = 'photo-placeholder';
                    
                    showAlert('Utilisateur créé avec succès', 'success');
                    showSection('adminUsers');
                }
            } catch (error) {
                console.error('Erreur lors de la création de l\'utilisateur:', error);
                showAlert('Erreur lors de la création de l\'utilisateur: ' + error.message, 'error');
            }
        }

        // Photo handling functions
        function previewPhoto(event) {
            const input = event.target;
            const preview = document.getElementById('photoPreview');
            
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    preview.innerHTML = '';
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.className = 'photo-preview';
                    preview.appendChild(img);
                }
                
                reader.readAsDataURL(input.files[0]);
            }
        }

        function getPhotoData() {
            const input = document.getElementById('photoInput');
            if (input.files && input.files[0]) {
                return new Promise((resolve) => {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        resolve(e.target.result);
                    };
                    reader.readAsDataURL(input.files[0]);
                });
            }
            return Promise.resolve(null);
        }

        function createAvatar(user) {
            if (user.photo) {
                return `<img src="${user.photo}" alt="${user.prenom} ${user.nom}" class="user-photo-table">`;
            }
            
            const roleLetter = user.role.charAt(0);
            const nomLetter = user.nom ? user.nom.charAt(0).toUpperCase() : 'U';
            const initiales = roleLetter + nomLetter;
            
            const avatarClass = `avatar-table ${
                user.role === 'ADMINISTRATEUR' ? 'avatar-admin' : 
                user.role === 'CHEF' ? 'avatar-chef' : 'avatar-employe'
            }`;
            
            return `<div class="${avatarClass}">${initiales}</div>`;
        }

        function createLargeAvatar(user) {
            if (user.photo) {
                return `<img src="${user.photo}" alt="${user.prenom} ${user.nom}" class="photo-preview">`;
            }
            
            const roleLetter = user.role.charAt(0);
            const nomLetter = user.nom ? user.nom.charAt(0).toUpperCase() : 'U';
            const initiales = roleLetter + nomLetter;
            
            const avatarClass = `avatar ${
                user.role === 'ADMINISTRATEUR' ? 'avatar-admin' : 
                user.role === 'CHEF' ? 'avatar-chef' : 'avatar-employe'
            }`;
            
            return `<div class="${avatarClass}" style="width: 120px; height: 120px; font-size: 2rem; margin: 0 auto 1rem;">${initiales}</div>`;
        }

        function createMediumAvatar(user) {
            if (user.photo) {
                return `<img src="${user.photo}" alt="${user.prenom} ${user.nom}" class="user-photo">`;
            }
            
            const roleLetter = user.role.charAt(0);
            const nomLetter = user.nom ? user.nom.charAt(0).toUpperCase() : 'U';
            const initiales = roleLetter + nomLetter;
            
            const avatarClass = `avatar ${
                user.role === 'ADMINISTRATEUR' ? 'avatar-admin' : 
                user.role === 'CHEF' ? 'avatar-chef' : 'avatar-employe'
            }`;
            
            return `<div class="${avatarClass}">${initiales}</div>`;
        }

        // Chef Actions
        function loadChefActions() {
            const user = getCurrentUser();
            if (!user || user.role !== 'CHEF') return;

            const chefInfo = document.getElementById('chefInfo');
            chefInfo.innerHTML = `
                <strong>Chef d'équipe :</strong> ${user.prenom} ${user.nom}
                ${user.activity ? createActivityBadge(user.activity) : ''}
                <br><strong>Département :</strong> ${user.departement}
                <br><strong>Activité assignée :</strong> ${getActivityName(user.activity)}
            `;
        }

        // Presence Management
        let currentPresences = {};

        async function loadPresenceManagement() {
            const user = getCurrentUser();
            if (!user || user.role !== 'CHEF') return;

            document.getElementById('chefActivityBadge').innerHTML = createActivityBadge(user.activity);

            const today = new Date().toISOString().split('T')[0];
            document.getElementById('presenceDate').value = today;

            try {
                const users = await getUsers();
                const employees = users.filter(u => u.role === 'EMPLOYE' && u.departement === user.departement && u.activity === user.activity);

                const container = document.getElementById('employeePresenceList');
                
                if (employees.length === 0) {
                    container.innerHTML = `
                        <div style="text-align: center; padding: 2rem; color: var(--text-light);">
                            <div style="font-size: 3rem; margin-bottom: 1rem;">👥</div>
                            <h4>Aucun employé dans votre activité</h4>
                            <p>Les employés de l'activité "${getActivityName(user.activity)}" apparaîtront ici</p>
                        </div>
                    `;
                    return;
                }

                // Charger les présences existantes pour aujourd'hui
                const existingPresences = await getPresences(today);
                currentPresences = { ...existingPresences };

                employees.forEach(emp => {
                    if (!currentPresences[emp.id]) {
                        currentPresences[emp.id] = 'absent';
                    }
                });

                container.innerHTML = employees.map(emp => {
                    const avatar = createMediumAvatar(emp);
                    const status = currentPresences[emp.id] || 'absent';
                    return `
                        <div class="employee-card ${status}" id="employee-${emp.id}">
                            <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                                ${avatar}
                                <div>
                                    <strong>${emp.prenom} ${emp.nom}</strong>
                                    <div>${emp.username} - ${emp.departement}</div>
                                </div>
                            </div>
                            <div class="presence-toggle">
                                <button type="button" class="toggle-btn toggle-present ${status === 'present' ? 'active' : ''}" onclick="togglePresence(${emp.id}, 'present')">
                                    ✅ Présent
                                </button>
                                <button type="button" class="toggle-btn toggle-absent ${status === 'absent' ? 'active' : ''}" onclick="togglePresence(${emp.id}, 'absent')">
                                    ❌ Absent
                                </button>
                            </div>
                        </div>
                    `;
                }).join('');
            } catch (error) {
                console.error('Erreur lors du chargement de la gestion des présences:', error);
                showAlert('Erreur lors du chargement des employés: ' + error.message, 'error');
            }
        }

        function togglePresence(employeeId, status) {
            currentPresences[employeeId] = status;
            const card = document.getElementById(`employee-${employeeId}`);
            
            card.classList.remove('present', 'absent');
            card.classList.add(status);
        }

        async function savePresences() {
            const date = document.getElementById('presenceDate').value;
            if (!date) {
                showAlert('Veuillez sélectionner une date', 'error');
                return;
            }

            try {
                const success = await savePresencesForDate(date, currentPresences);
                
                if (success) {
                    const user = getCurrentUser();
                    const presentCount = Object.values(currentPresences).filter(p => p === 'present').length;
                    const absentCount = Object.values(currentPresences).filter(p => p === 'absent').length;
                    
                    showAlert(`Présences enregistrées : ${presentCount} présent(s), ${absentCount} absent(s)`, 'success');
                    showSection('chefActions');
                }
            } catch (error) {
                console.error('Erreur lors de l\'enregistrement des présences:', error);
                showAlert('Erreur lors de l\'enregistrement des présences: ' + error.message, 'error');
            }
        }

        // Pointage Management avec sous-quantités
        async function loadPointageManagement() {
            const user = getCurrentUser();
            if (!user || user.role !== 'CHEF') return;

            document.getElementById('pointageActivityBadge').innerHTML = createActivityBadge(user.activity);

            const today = new Date().toISOString().split('T')[0];
            document.getElementById('pointageDate').value = today;

            try {
                const todayPresences = await getPresences(today);

                if (!todayPresences || Object.keys(todayPresences).length === 0) {
                    showAlert('Aucune présence enregistrée pour aujourd\'hui. Veuillez d\'abord gérer les présences.', 'error');
                    showSection('chefPresence');
                    return;
                }

                const users = await getUsers();
                const employees = users.filter(u => u.role === 'EMPLOYE' && u.departement === user.departement && u.activity === user.activity);

                const presentEmployees = employees.filter(emp => todayPresences[emp.id] === 'present');
                
                if (presentEmployees.length === 0) {
                    showAlert('Aucun employé présent aujourd\'hui dans votre activité.', 'error');
                    showSection('chefPresence');
                    return;
                }

                const container = document.getElementById('pointageFormsContainer');
                container.innerHTML = presentEmployees.map(emp => {
                    const avatar = createMediumAvatar(emp);
                    return `
                        <div class="form-group" style="background: #f0fdf4; padding: 1.5rem; border-radius: 8px; margin-bottom: 1.5rem;">
                            <div style="display: flex; align-items: center; margin-bottom: 1rem;">
                                ${avatar}
                                <h4>📝 ${emp.prenom} ${emp.nom}</h4>
                                ${emp.email ? `<div style="font-size: 0.8rem; color: var(--text-light);">📧 ${emp.email}</div>` : ''}
                                ${emp.telephone ? `<div style="font-size: 0.8rem; color: var(--text-light);">📞 ${emp.telephone}</div>` : ''}
                            </div>
                            <div class="form-row">
                                <div class="form-group">
                                    <label>Activité *</label>
                                    <select id="activity-${emp.id}" required>
                                        <option value="${user.activity}">${getActivityName(user.activity)}</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label>Bloc</label>
                                    <input type="text" id="bloc-${emp.id}" placeholder="Bloc...">
                                </div>
                            </div>
                            
                            <!-- Sous-quantités -->
                            <div class="sub-quantities-container">
                                <h5>Sous-quantités</h5>
                                <div id="subQuantities-${emp.id}">
                                    <div class="sub-quantity-row">
                                        <input type="number" class="sub-quantity-input" placeholder="Quantité" min="0" step="0.01" oninput="updateSubQuantityTotal(${emp.id})">
                                        <button type="button" class="btn btn-small btn-danger" onclick="this.parentElement.remove(); updateSubQuantityTotal(${emp.id})">❌</button>
                                    </div>
                                </div>
                                <button type="button" class="btn btn-small" onclick="addSubQuantity(${emp.id})">➕ Ajouter une sous-quantité</button>
                                <div id="subQuantityTotal-${emp.id}" class="sub-quantity-total">Total: 0</div>
                            </div>
                            
                            <div class="form-row">
                                <div class="form-group">
                                    <label>Quantité totale *</label>
                                    <input type="number" id="qty-${emp.id}" required placeholder="0" step="0.01" min="0" readonly>
                                </div>
                                <div class="form-group">
                                    <label>Prix unitaire</label>
                                    <input type="number" id="unitPrice-${emp.id}" placeholder="0" step="0.01" min="0" oninput="updateSubQuantityTotal(${emp.id})">
                                </div>
                                <div class="form-group">
                                    <label>Prix total</label>
                                    <input type="number" id="totalPrice-${emp.id}" readonly>
                                </div>
                            </div>
                        </div>
                    `;
                }).join('');

                document.getElementById('emailBtn').disabled = true;
                document.getElementById('whatsappBtn').disabled = true;
                document.getElementById('sendingStatus').style.display = 'none';
            } catch (error) {
                console.error('Erreur lors du chargement de la gestion des pointages:', error);
                showAlert('Erreur lors du chargement des données: ' + error.message, 'error');
            }
        }

        async function saveAllPointages() {
            const user = getCurrentUser();
            const date = document.getElementById('pointageDate').value;
            
            try {
                const todayPresences = await getPresences(date);

                if (!todayPresences) {
                    showAlert('Aucune présence trouvée pour cette date', 'error');
                    return;
                }

                const users = await getUsers();
                const employees = users.filter(u => u.role === 'EMPLOYE' && u.departement === user.departement && u.activity === user.activity);

                const presentEmployees = employees.filter(emp => todayPresences[emp.id] === 'present');
                let savedCount = 0;

                lastSavedPointages = [];
                const pointagesData = [];

                for (const emp of presentEmployees) {
                    const subQuantities = getSubQuantities(emp.id);
                    const qtyTotal = parseFloat(document.getElementById(`qty-${emp.id}`).value) || 0;
                    
                    const pointageData = {
                        chef_id: user.id,
                        employee_id: emp.id,
                        date: date,
                        presence: 'Présent',
                        activity: user.activity,
                        bloc: document.getElementById(`bloc-${emp.id}`).value,
                        sub_quantities: subQuantities,
                        qty_total: qtyTotal,
                        unit_price: parseFloat(document.getElementById(`unitPrice-${emp.id}`).value) || 0,
                        total_price: parseFloat(document.getElementById(`totalPrice-${emp.id}`).value) || 0,
                        archived: false
                    };

                    pointagesData.push(pointageData);
                    lastSavedPointages.push(pointageData);
                    savedCount++;
                }

                const createdPointages = await createMultiplePointages(pointagesData);
                
                if (createdPointages.length > 0) {
                    document.getElementById('emailBtn').disabled = false;
                    document.getElementById('whatsappBtn').disabled = false;
                    
                    showAlert(`${savedCount} pointage(s) enregistré(s) avec succès. Vous pouvez maintenant les envoyer aux employés.`, 'success');
                }
            } catch (error) {
                console.error('Erreur lors de l\'enregistrement des pointages:', error);
                showAlert('Erreur lors de l\'enregistrement des pointages: ' + error.message, 'error');
            }
        }

        // Fonctions d'envoi des pointages
        function sendPointagesByEmail() {
            if (lastSavedPointages.length === 0) {
                showAlert('Aucun pointage à envoyer', 'error');
                return;
            }

            // Implémentation basique de l'envoi d'email
            const statusList = document.getElementById('statusList');
            const sendingStatus = document.getElementById('sendingStatus');
            
            sendingStatus.style.display = 'block';
            statusList.innerHTML = '';

            lastSavedPointages.forEach(pointage => {
                const statusItem = document.createElement('div');
                statusItem.className = 'status-item';
                statusItem.innerHTML = `
                    <span>
                        <span class="status-indicator status-success"></span>
                        Pointage ${pointage.id || ''}
                    </span>
                    <span style="color: var(--success);">Email préparé</span>
                `;
                statusList.appendChild(statusItem);
            });

            showAlert(`Préparation de ${lastSavedPointages.length} email(s) terminée`, 'info');
        }

        function sendPointagesByWhatsApp() {
            if (lastSavedPointages.length === 0) {
                showAlert('Aucun pointage à envoyer', 'error');
                return;
            }

            // Implémentation basique de l'envoi WhatsApp
            const statusList = document.getElementById('statusList');
            const sendingStatus = document.getElementById('sendingStatus');
            
            sendingStatus.style.display = 'block';
            statusList.innerHTML = '';

            lastSavedPointages.forEach(pointage => {
                const statusItem = document.createElement('div');
                statusItem.className = 'status-item';
                statusItem.innerHTML = `
                    <span>
                        <span class="status-indicator status-success"></span>
                        Pointage ${pointage.id || ''}
                    </span>
                    <span style="color: var(--success);">WhatsApp préparé</span>
                `;
                statusList.appendChild(statusItem);
            });

            showAlert(`Préparation de ${lastSavedPointages.length} message(s) WhatsApp terminée`, 'info');
        }

        // Data Loading Functions
        async function loadDashboard() {
            const user = getCurrentUser();
            if (!user) return;

            const dashboardTitle = document.getElementById('dashboardTitle');
            const dashboardWelcome = document.getElementById('dashboardWelcome');
            const dashboardGrid = document.getElementById('dashboardGrid');

            dashboardTitle.textContent = `Tableau de bord — ${user.role}`;
            dashboardWelcome.textContent = `Bienvenue ${user.prenom} ${user.nom} !`;
            let extraInfo = `<br><small>Rôle: ${user.role} | Département: ${user.departement}`;
            if (user.activity) {
                extraInfo += ` | Activité: ${getActivityName(user.activity)}`;
            }
            extraInfo += '</small>';
            dashboardWelcome.innerHTML += extraInfo;

            let dashboardHTML = '';

            if (user.role === 'ADMINISTRATEUR') {
                dashboardHTML = `
                    <div class="dashboard-card" onclick="showSection('adminUsers')">
                        <h3>👥 Gestion Utilisateurs</h3>
                        <p>Gérer les chefs et employés</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('adminCreateUser')">
                        <h3>➕ Créer Utilisateur</h3>
                        <p>Ajouter un nouveau utilisateur</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('adminPointages')">
                        <h3>📋 Fiches de Pointage</h3>
                        <p>Voir toutes les fiches de pointage</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('adminPaie')">
                        <h3>💰 Gestion Paie</h3>
                        <p>Générer et imprimer les bulletins</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('adminArchives')">
                        <h3>📦 Archives</h3>
                        <p>Gérer les archives</p>
                    </div>
                `;
            } else if (user.role === 'CHEF') {
                dashboardHTML = `
                    <div class="dashboard-card" onclick="showSection('chefActions')">
                        <h3>📊 Actions Chef</h3>
                        <p>Gérer présences et pointages</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('chefPointages')">
                        <h3>📋 Mes Pointages</h3>
                        <p>Voir l'historique</p>
                    </div>
                `;
            } else if (user.role === 'EMPLOYE') {
                dashboardHTML = `
                    <div class="dashboard-card" onclick="showSection('employeePointages')">
                        <h3>📋 Mes Pointages</h3>
                        <p>Consulter mes activités</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('employeeBulletins')">
                        <h3>💰 Mes Bulletins</h3>
                        <p>Consulter mes bulletins de paie</p>
                    </div>
                    <div class="dashboard-card" onclick="showSection('profile')">
                        <h3>👤 Mon Profil</h3>
                        <p>Informations personnelles</p>
                    </div>
                `;
            }

            dashboardGrid.innerHTML = dashboardHTML;
        }

        function loadProfile() {
            const user = getCurrentUser();
            if (!user) return;

            const profileContent = document.getElementById('profileContent');
            const avatar = createLargeAvatar(user);
            
            let activityHTML = '';
            if (user.activity) {
                activityHTML = `
                    <div>
                        <strong>Activité :</strong><br>
                        <span>${getActivityName(user.activity)}</span>
                    </div>
                `;
            }

            let contactHTML = '';
            if (user.telephone || user.email) {
                contactHTML = `
                    <div>
                        <strong>Contact :</strong><br>
                        ${user.telephone ? `<span>📞 ${user.telephone}</span><br>` : ''}
                        ${user.email ? `<span>📧 ${user.email}</span>` : ''}
                    </div>
                `;
            }

            profileContent.innerHTML = `
                <div style="text-align: center; margin-bottom: 2rem;">
                    ${avatar}
                </div>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1rem;">
                    <div>
                        <strong>Identifiant :</strong><br>
                        <span>${user.username}</span>
                    </div>
                    <div>
                        <strong>Nom :</strong><br>
                        <span>${user.nom}</span>
                    </div>
                    <div>
                        <strong>Prénom :</strong><br>
                        <span>${user.prenom}</span>
                    </div>
                    <div>
                        <strong>Rôle :</strong><br>
                        <span>${user.role}</span>
                    </div>
                    <div>
                        <strong>Département :</strong><br>
                        <span>${user.departement}</span>
                    </div>
                    ${activityHTML}
                    ${contactHTML}
                    <div>
                        <strong>Couleur :</strong><br>
                        <span style="display: inline-flex; align-items: center; gap: 0.5rem;">
                            <span class="color-indicator" style="background: ${user.color};"></span>
                            ${user.color}
                        </span>
                    </div>
                </div>
            `;
        }

        async function loadUsersTable() {
            try {
                const users = await getUsers();
                const tbody = document.getElementById('usersTableBody');
                
                const filteredUsers = users.filter(user => user.role !== 'ADMINISTRATEUR');
                
                updateDepartementFilters(filteredUsers);
                
                tbody.innerHTML = filteredUsers.map(user => {
                    const avatar = createAvatar(user);
                    return `
                        <tr>
                            <td>${avatar}</td>
                            <td>${user.id}</td>
                            <td>${user.username}</td>
                            <td>${user.nom}</td>
                            <td>${user.prenom}</td>
                            <td>${user.role}</td>
                            <td>${user.activity ? getActivityName(user.activity) : '-'}</td>
                            <td>${user.departement}</td>
                            <td>
                                <span class="color-indicator" style="background: ${user.color};"></span>
                                ${user.color}
                            </td>
                            <td>
                                <button class="btn btn-small" onclick="editUser(${user.id})" style="margin-right: 0.5rem;">✏️ Modifier</button>
                                <button class="btn btn-danger btn-small" onclick="deleteUserHandler(${user.id})" ${user.id === getCurrentUser()?.id ? 'disabled' : ''}>🗑️ Supprimer</button>
                            </td>
                        </tr>
                    `;
                }).join('');
            } catch (error) {
                console.error('Erreur lors du chargement des utilisateurs:', error);
                showAlert('Erreur lors du chargement des utilisateurs: ' + error.message, 'error');
            }
        }

        async function deleteUserHandler(userId) {
            if (confirm('Êtes-vous sûr de vouloir supprimer cet utilisateur ?')) {
                try {
                    const success = await deleteUser(userId);
                    if (success) {
                        showAlert('Utilisateur supprimé', 'success');
                        loadUsersTable();
                    }
                } catch (error) {
                    console.error('Erreur lors de la suppression de l\'utilisateur:', error);
                    showAlert('Erreur lors de la suppression de l\'utilisateur: ' + error.message, 'error');
                }
            }
        }

        function updateDepartementFilters(users) {
            const departementFilter = document.getElementById('filterDepartement');
            const departements = [...new Set(users.map(user => user.departement))].sort();
            
            departementFilter.innerHTML = '<option value="">Tous les départements</option>';
            departements.forEach(dept => {
                departementFilter.innerHTML += `<option value="${dept}">${dept}</option>`;
            });
        }

        function filterUsersTable() {
            const departementFilter = document.getElementById('filterDepartement').value;
            const roleFilter = document.getElementById('filterRole').value;
            
            const rows = document.querySelectorAll('#usersTableBody tr');
            rows.forEach(row => {
                const cells = row.getElementsByTagName('td');
                const userDepartement = cells[7].textContent;
                const userRole = cells[5].textContent;
                
                const departementMatch = !departementFilter || userDepartement === departementFilter;
                const roleMatch = !roleFilter || userRole === roleFilter;
                
                row.style.display = departementMatch && roleMatch ? '' : 'none';
            });
        }

        // Formater les montants en FCFA
        function formatFCFA(montant) {
            if (typeof montant !== 'number') montant = parseFloat(montant) || 0;
            return new Intl.NumberFormat('fr-FR', {
                style: 'currency',
                currency: 'XOF',
                minimumFractionDigits: 0,
                maximumFractionDigits: 0
            }).format(montant);
        }

        // =============================================
        // FONCTIONS DE GESTION DES POINTAGES
        // =============================================

        // Admin Pointages Management - Version par semaine
        async function loadAdminPointages() {
            try {
                const pointages = await getPointages();
                const users = await getUsers();
                
                // Enrichir les pointages avec les noms des employés et chefs
                const enrichedPointages = pointages.map(pointage => {
                    const employee = users.find(u => u.id === pointage.employee_id);
                    const chef = users.find(u => u.id === pointage.chef_id);
                    
                    return {
                        ...pointage,
                        employee_name: employee ? `${employee.prenom} ${employee.nom}` : 'N/A',
                        chef_name: chef ? `${chef.prenom} ${chef.nom}` : 'N/A'
                    };
                });
                
                currentPointages = enrichedPointages;
                
                const container = document.getElementById('pointagesByWeekContainer');
                
                if (enrichedPointages.length === 0) {
                    container.innerHTML = `
                        <div class="empty-state">
                            <div class="empty-state-icon">📋</div>
                            <h3>Aucune fiche de pointage trouvée</h3>
                            <p>Les fiches de pointage créées par les chefs apparaîtront ici</p>
                        </div>
                    `;
                    return;
                }

                updatePointageStats(enrichedPointages);
                updatePointageFilters(enrichedPointages);
                
                // Filtrer les pointages selon les critères actuels
                const filteredPointages = filterPointages(enrichedPointages);
                
                // Grouper les pointages par semaine
                const weeks = groupPointagesByWeek(filteredPointages);
                
                // Générer l'affichage
                container.innerHTML = generateWeeklyPointagesDisplay(weeks, 'admin');
                
            } catch (error) {
                console.error('Erreur lors du chargement des pointages admin:', error);
                showAlert('Erreur lors du chargement des pointages: ' + error.message, 'error');
            }
        }

        function updatePointageStats(pointages) {
            const totalPointages = pointages.length;
            const totalPrix = pointages.reduce((sum, p) => sum + (p.total_price || 0), 0);
            const pointagesAujourdhui = pointages.filter(p => p.date === new Date().toISOString().split('T')[0]).length;
            const activitesUniques = [...new Set(pointages.map(p => p.activity))].length;

            document.getElementById('pointageStats').innerHTML = `
                <div class="stat-card">
                    <div class="stat-number">${totalPointages}</div>
                    <div class="stat-label">Total Pointages</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">${formatFCFA(totalPrix)}</div>
                    <div class="stat-label">Total Prix</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">${pointagesAujourdhui}</div>
                    <div class="stat-label">Aujourd'hui</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">${activitesUniques}</div>
                    <div class="stat-label">Activités</div>
                </div>
            `;
        }

        function updatePointageFilters(pointages) {
            // Mettre à jour le filtre d'activité
            const activityFilter = document.getElementById('filterPointageActivity');
            const activities = [...new Set(pointages.map(p => p.activity))].sort();
            
            activityFilter.innerHTML = '<option value="">Toutes les activités</option>';
            activities.forEach(activity => {
                activityFilter.innerHTML += `<option value="${activity}">${getActivityName(activity)}</option>`;
            });

            // Mettre à jour le filtre des chefs
            const chefFilter = document.getElementById('filterPointageChef');
            const chefs = [...new Set(pointages.map(p => p.chef_name))].filter(name => name !== 'N/A').sort();
            
            chefFilter.innerHTML = '<option value="">Tous les chefs</option>';
            chefs.forEach(chef => {
                chefFilter.innerHTML += `<option value="${chef}">${chef}</option>`;
            });
        }

        function filterPointages(pointages) {
            const activityFilter = document.getElementById('filterPointageActivity').value;
            const dateFilter = document.getElementById('filterPointageDate').value;
            const chefFilter = document.getElementById('filterPointageChef').value;
            const archivedFilter = document.getElementById('filterPointageArchived').value;
            const searchTerm = document.getElementById('searchPointage').value.toLowerCase();

            return pointages.filter(pointage => {
                // Filtre par activité
                if (activityFilter && pointage.activity !== activityFilter) {
                    return false;
                }
                
                // Filtre par date
                if (dateFilter && pointage.date !== dateFilter) {
                    return false;
                }
                
                // Filtre par chef
                if (chefFilter && pointage.chef_name !== chefFilter) {
                    return false;
                }
                
                // Filtre par statut d'archivage
                if (archivedFilter === 'non-archived' && pointage.archived) {
                    return false;
                }
                if (archivedFilter === 'archived' && !pointage.archived) {
                    return false;
                }
                
                // Recherche
                if (searchTerm) {
                    const searchFields = [
                        pointage.employee_name,
                        pointage.chef_name,
                        pointage.activity,
                        pointage.bloc
                    ].join(' ').toLowerCase();
                    
                    if (!searchFields.includes(searchTerm)) {
                        return false;
                    }
                }
                
                return true;
            });
        }

        function filterPointagesTable() {
            const filteredPointages = filterPointages(currentPointages);
            const weeks = groupPointagesByWeek(filteredPointages);
            const container = document.getElementById('pointagesByWeekContainer');
            
            if (filteredPointages.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-state-icon">📋</div>
                        <h3>Aucun pointage trouvé</h3>
                        <p>Aucun pointage ne correspond aux critères de recherche</p>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = generateWeeklyPointagesDisplay(weeks, 'admin');
        }

        function searchPointages() {
            filterPointagesTable();
        }

        function clearPointageSearch() {
            document.getElementById('searchPointage').value = '';
            document.getElementById('filterPointageActivity').value = '';
            document.getElementById('filterPointageDate').value = '';
            document.getElementById('filterPointageChef').value = '';
            document.getElementById('filterPointageArchived').value = 'non-archived';
            filterPointagesTable();
        }

        // Chef Pointages - Version par semaine
        async function loadChefPointages() {
            const user = getCurrentUser();
            if (!user || user.role !== 'CHEF') return;

            document.getElementById('pointagesActivityBadge').innerHTML = createActivityBadge(user.activity);

            try {
                const pointages = await getPointages();
                const users = await getUsers();

                // Filtrer les pointages du chef
                const chefPointages = pointages.filter(p => p.chef_id === user.id);
                
                // Enrichir les pointages avec les noms des employés
                const enrichedPointages = chefPointages.map(pointage => {
                    const employee = users.find(u => u.id === pointage.employee_id);
                    
                    return {
                        ...pointage,
                        employee_name: employee ? `${employee.prenom} ${employee.nom}` : 'N/A'
                    };
                });

                const container = document.getElementById('weeklyPointagesContainer');
                
                if (enrichedPointages.length === 0) {
                    container.innerHTML = `
                        <div class="empty-state">
                            <div class="empty-state-icon">📋</div>
                            <h3>Aucun pointage trouvé</h3>
                            <p>Vos pointages apparaîtront ici une fois créés</p>
                        </div>
                    `;
                    return;
                }

                // Grouper les pointages par semaine
                const weeks = groupPointagesByWeek(enrichedPointages);
                
                // Générer l'affichage
                container.innerHTML = generateWeeklyPointagesDisplay(weeks, 'chef');
                
            } catch (error) {
                console.error('Erreur lors du chargement des pointages du chef:', error);
                showAlert('Erreur lors du chargement des pointages: ' + error.message, 'error');
            }
        }

        // Employee Pointages - Version par semaine
        async function loadEmployeePointages() {
            const user = getCurrentUser();
            if (!user || user.role !== 'EMPLOYE') return;

            try {
                const pointages = await getPointages();
                const users = await getUsers();

                // Filtrer les pointages de l'employé
                const employeePointages = pointages.filter(p => p.employee_id === user.id);
                
                // Enrichir les pointages avec les noms des chefs
                const enrichedPointages = employeePointages.map(pointage => {
                    const chef = users.find(u => u.id === pointage.chef_id);
                    
                    return {
                        ...pointage,
                        chef_name: chef ? `${chef.prenom} ${chef.nom}` : 'N/A',
                        employee_name: `${user.prenom} ${user.nom}`
                    };
                });

                const container = document.getElementById('employeeWeeklyPointagesContainer');
                
                if (enrichedPointages.length === 0) {
                    container.innerHTML = `
                        <div class="empty-state">
                            <div class="empty-state-icon">📋</div>
                            <h3>Aucun pointage trouvé</h3>
                            <p>Vos pointages apparaîtront ici une fois créés par votre chef</p>
                        </div>
                    `;
                    return;
                }

                // Grouper les pointages par semaine
                const weeks = groupPointagesByWeek(enrichedPointages);
                
                // Générer l'affichage
                container.innerHTML = generateWeeklyPointagesDisplay(weeks, 'employe');
                
            } catch (error) {
                console.error('Erreur lors du chargement des pointages employé:', error);
                showAlert('Erreur lors du chargement des pointages: ' + error.message, 'error');
            }
        }

        // =============================================
        // FONCTIONS POUR LA GESTION DE LA PAIE (CORRIGÉES)
        // =============================================

        async function loadBulletinsTable() {
            try {
                const bulletins = await getBulletins();
                const users = await getUsers();
                
                currentBulletins = bulletins;
                
                const tbody = document.getElementById('bulletinsTableBody');
                
                if (bulletins.length === 0) {
                    tbody.innerHTML = `
                        <tr>
                            <td colspan="8" style="text-align: center; padding: 2rem;">
                                <div class="empty-state-icon">💰</div>
                                <h3>Aucun bulletin de paie</h3>
                                <p>Générez les bulletins pour les voir apparaître ici</p>
                            </td>
                        </tr>
                    `;
                    return;
                }

                updateBulletinsStats(bulletins);
                updateBulletinsFilters(bulletins, users);
                
                // Filtrer les bulletins selon les critères actuels
                const filteredBulletins = filterBulletins(bulletins, users);
                
                tbody.innerHTML = filteredBulletins.map(bulletin => {
                    const employee = users.find(u => u.id === bulletin.employee_id);
                    const employeeName = employee ? `${employee.prenom} ${employee.nom}` : 'N/A';
                    
                    return `
                        <tr>
                            <td>
                                <input type="checkbox" value="${bulletin.id}" onchange="toggleBulletinSelection(${bulletin.id})">
                            </td>
                            <td>${bulletin.id}</td>
                            <td>${employeeName}</td>
                            <td>${bulletin.periode}</td>
                            <td>${formatFCFA(bulletin.salaire_brut)}</td>
                            <td>${formatFCFA(bulletin.net_a_payer)}</td>
                            <td>
                                <span style="color: var(--success); font-weight: 500;">
                                    ${bulletin.statut}
                                </span>
                            </td>
                            <td>
                                <button class="btn btn-small" onclick="viewBulletin(${bulletin.id})">👁️ Voir</button>
                                <button class="btn btn-small btn-warning" onclick="archiverBulletin(${bulletin.id})">📦 Archiver</button>
                            </td>
                        </tr>
                    `;
                }).join('');

            } catch (error) {
                console.error('Erreur lors du chargement des bulletins:', error);
                showAlert('Erreur lors du chargement des bulletins: ' + error.message, 'error');
            }
        }

        function updateBulletinsStats(bulletins) {
            const totalBulletins = bulletins.length;
            const totalSalaireBrut = bulletins.reduce((sum, b) => sum + b.salaire_brut, 0);
            const totalNetAPayer = bulletins.reduce((sum, b) => sum + b.net_a_payer, 0);
            const employesPayes = new Set(bulletins.map(b => b.employee_id)).size;

            document.getElementById('paieStats').innerHTML = `
                <div class="stat-card">
                    <div class="stat-number">${totalBulletins}</div>
                    <div class="stat-label">Total Bulletins</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">${formatFCFA(totalSalaireBrut)}</div>
                    <div class="stat-label">Salaire Brut Total</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">${formatFCFA(totalNetAPayer)}</div>
                    <div class="stat-label">Net à Payer Total</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">${employesPayes}</div>
                    <div class="stat-label">Employés Payés</div>
                </div>
            `;
        }

        function updateBulletinsFilters(bulletins, users) {
            // Mettre à jour le filtre des mois
            const moisFilter = document.getElementById('filterPaieMois');
            const mois = [...new Set(bulletins.map(b => {
                const date = new Date(b.date_generation);
                return date.toLocaleDateString('fr-FR', { month: 'long', year: 'numeric' });
            }))].sort();
            
            moisFilter.innerHTML = '<option value="">Tous les mois</option>';
            mois.forEach(m => {
                moisFilter.innerHTML += `<option value="${m}">${m}</option>`;
            });

            // Mettre à jour le filtre des années
            const anneeFilter = document.getElementById('filterPaieAnnee');
            const annees = [...new Set(bulletins.map(b => new Date(b.date_generation).getFullYear()))].sort((a, b) => b - a);
            
            anneeFilter.innerHTML = '<option value="">Toutes les années</option>';
            annees.forEach(a => {
                anneeFilter.innerHTML += `<option value="${a}">${a}</option>`;
            });

            // Mettre à jour le filtre des employés
            const employeFilter = document.getElementById('filterPaieEmploye');
            const employes = [...new Set(bulletins.map(b => b.employee_id))].map(id => {
                const employee = users.find(u => u.id === id);
                return employee ? { id: id, name: `${employee.prenom} ${employee.nom}` } : null;
            }).filter(e => e !== null).sort((a, b) => a.name.localeCompare(b.name));
            
            employeFilter.innerHTML = '<option value="">Tous les employés</option>';
            employes.forEach(e => {
                employeFilter.innerHTML += `<option value="${e.id}">${e.name}</option>`;
            });
        }

        function filterBulletins(bulletins, users) {
            const moisFilter = document.getElementById('filterPaieMois').value;
            const anneeFilter = document.getElementById('filterPaieAnnee').value;
            const employeFilter = document.getElementById('filterPaieEmploye').value;
            const archivedFilter = document.getElementById('filterPaieArchived').value;
            const searchTerm = document.getElementById('searchBulletin').value.toLowerCase();

            return bulletins.filter(bulletin => {
                // Filtre par mois
                if (moisFilter) {
                    const bulletinMois = new Date(bulletin.date_generation).toLocaleDateString('fr-FR', { month: 'long', year: 'numeric' });
                    if (bulletinMois !== moisFilter) {
                        return false;
                    }
                }
                
                // Filtre par année
                if (anneeFilter) {
                    const bulletinAnnee = new Date(bulletin.date_generation).getFullYear().toString();
                    if (bulletinAnnee !== anneeFilter) {
                        return false;
                    }
                }
                
                // Filtre par employé
                if (employeFilter && bulletin.employee_id !== parseInt(employeFilter)) {
                    return false;
                }
                
                // Filtre par statut d'archivage
                if (archivedFilter === 'non-archived' && bulletin.archived) {
                    return false;
                }
                if (archivedFilter === 'archived' && !bulletin.archived) {
                    return false;
                }
                
                // Recherche
                if (searchTerm) {
                    const employee = users.find(u => u.id === bulletin.employee_id);
                    const employeeName = employee ? `${employee.prenom} ${employee.nom}` : '';
                    const searchFields = [
                        employeeName,
                        bulletin.periode,
                        bulletin.statut
                    ].join(' ').toLowerCase();
                    
                    if (!searchFields.includes(searchTerm)) {
                        return false;
                    }
                }
                
                return true;
            });
        }

        function searchBulletins() {
            loadBulletinsTable();
        }

        function clearBulletinSearch() {
            document.getElementById('searchBulletin').value = '';
            document.getElementById('filterPaieMois').value = '';
            document.getElementById('filterPaieAnnee').value = '';
            document.getElementById('filterPaieEmploye').value = '';
            document.getElementById('filterPaieArchived').value = 'non-archived';
            loadBulletinsTable();
        }

        async function genererBulletinsMensuels() {
            try {
                const users = await getUsers();
                const employees = users.filter(u => u.role === 'EMPLOYE');
                
                const aujourdhui = new Date();
                const mois = aujourdhui.toLocaleDateString('fr-FR', { month: 'long' });
                const annee = aujourdhui.getFullYear();
                const periode = `${mois} ${annee}`;
                
                let bulletinsCrees = 0;
                
                for (const employee of employees) {
                    // Vérifier si un bulletin existe déjà pour cet employé ce mois-ci
                    const bulletinsExistants = await getBulletinsByEmployee(employee.id);
                    const bulletinExistant = bulletinsExistants.find(b => b.periode === periode);
                    
                    if (bulletinExistant) {
                        // Mettre à jour le bulletin existant au lieu d'en créer un nouveau
                        const salaireBase = CONFIG_PAIE_PRO.salaireBase;
                        
                        // Ajuster selon l'activité
                        let salaireAjuste = salaireBase;
                        switch(employee.activity) {
                            case 'recolte':
                                salaireAjuste *= 1.1;
                                break;
                            case 'rabattage':
                                salaireAjuste *= 1.05;
                                break;
                            case 'élagage':
                                salaireAjuste *= 1.08;
                                break;
                            default:
                                salaireAjuste *= 1.0;
                        }
                        
                        // Calculer les cotisations (exemple simplifié)
                        const cotisations = salaireAjuste * 0.23; // 23% de cotisations
                        const netAPayer = salaireAjuste - cotisations;
                        
                        const updates = {
                            salaire_base: salaireAjuste,
                            salaire_brut: salaireAjuste,
                            total_retenues: cotisations,
                            net_a_payer: netAPayer,
                            date_generation: new Date().toISOString(),
                            // Mettre à jour les données supplémentaires
                            heures_supplementaires: Math.floor(Math.random() * 10),
                            prime_anciennete: salaireAjuste * 0.02,
                            prime_rendement: salaireAjuste * 0.05,
                            montant_cnps: salaireAjuste * 0.055,
                            montant_assurance: salaireAjuste * 0.035,
                            montant_irpp: Math.max(0, salaireAjuste - 50000) * 0.15,
                            total_charges_patronales: salaireAjuste * 0.45,
                            cout_total_employeur: salaireAjuste * 1.45
                        };
                        
                        await updateBulletin(bulletinExistant.id, updates);
                        bulletinsCrees++;
                    } else {
                        // Créer un nouveau bulletin
                        let salaireBase = CONFIG_PAIE_PRO.salaireBase;
                        
                        // Ajuster selon l'activité
                        switch(employee.activity) {
                            case 'recolte':
                                salaireBase *= 1.1;
                                break;
                            case 'rabattage':
                                salaireBase *= 1.05;
                                break;
                            case 'élagage':
                                salaireBase *= 1.08;
                                break;
                            default:
                                salaireBase *= 1.0;
                        }
                        
                        // Calculer les cotisations (exemple simplifié)
                        const cotisations = salaireBase * 0.23; // 23% de cotisations
                        const netAPayer = salaireBase - cotisations;
                        
                        const bulletinData = {
                            employee_id: employee.id,
                            employee_nom: employee.nom,
                            employee_prenom: employee.prenom,
                            employee_photo: employee.photo,
                            periode: periode,
                            date_generation: new Date().toISOString(),
                            salaire_base: salaireBase,
                            salaire_brut: salaireBase,
                            total_retenues: cotisations,
                            net_a_payer: netAPayer,
                            statut: 'Payé',
                            archived: false,
                            // Données supplémentaires pour le bulletin détaillé
                            heures_supplementaires: Math.floor(Math.random() * 10),
                            taux_horaire: 5000,
                            prime_anciennete: salaireBase * 0.02,
                            prime_rendement: salaireBase * 0.05,
                            base_cnps: salaireBase,
                            taux_cnps: 5.5,
                            base_assurance: salaireBase,
                            taux_assurance: 3.5,
                            base_irpp: Math.max(0, salaireBase - 50000),
                            taux_irpp: 15,
                            cnps_patronale: salaireBase * 0.085,
                            assurance_patronale: salaireBase * 0.05,
                            taxe_formation: salaireBase * 0.01,
                            cout_total_employeur: salaireBase * 1.45
                        };
                        
                        await createBulletin(bulletinData);
                        bulletinsCrees++;
                    }
                }
                
                showAlert(`${bulletinsCrees} bulletins de paie ${bulletinsCrees > 0 ? 'générés/mis à jour' : 'générés'} pour ${periode}`, 'success');
                loadBulletinsTable();
                
            } catch (error) {
                console.error('Erreur lors de la génération des bulletins:', error);
                showAlert('Erreur lors de la génération des bulletins: ' + error.message, 'error');
            }
        }

        async function viewBulletin(bulletinId) {
            try {
                const bulletins = await getBulletins();
                const bulletin = bulletins.find(b => b.id === bulletinId);
                
                if (!bulletin) {
                    showAlert('Bulletin non trouvé', 'error');
                    return;
                }

                document.getElementById('bulletinContent').innerHTML = genererBulletinHTML(bulletin);
                showSection('bulletinDetail');
            } catch (error) {
                console.error('Erreur lors de l\'affichage du bulletin:', error);
                showAlert('Erreur lors de l\'affichage du bulletin: ' + error.message, 'error');
            }
        }

        function imprimerBulletin() {
            window.print();
        }

        function goBackToPaie() {
            const user = getCurrentUser();
            if (user.role === 'ADMINISTRATEUR') {
                showSection('adminPaie');
            } else if (user.role === 'EMPLOYE') {
                showSection('employeeBulletins');
            }
        }

        // =============================================
        // FONCTIONS POUR LES ARCHIVES (CORRIGÉES)
        // =============================================

        async function showArchives(type) {
            try {
                const archivesContent = document.getElementById('archivesContent');
                
                if (type === 'bulletins') {
                    const bulletins = await getArchivedBulletins();
                    
                    if (bulletins.length === 0) {
                        archivesContent.innerHTML = `
                            <div class="empty-state">
                                <div class="empty-state-icon">📦</div>
                                <h3>Aucun bulletin archivé</h3>
                                <p>Les bulletins archivés apparaîtront ici</p>
                            </div>
                        `;
                        return;
                    }

                    archivesContent.innerHTML = `
                        <h4>📋 Archives des Bulletins de Paie</h4>
                        <div class="archive-section">
                            ${bulletins.map(bulletin => {
                                const dateGen = new Date(bulletin.date_generation);
                                return `
                                    <div class="archive-folder" onclick="viewBulletin(${bulletin.id})">
                                        <div class="folder-header">
                                            <div class="folder-title">${bulletin.employee_prenom} ${bulletin.employee_nom}</div>
                                            <div class="folder-count">${formatFCFA(bulletin.net_a_payer)}</div>
                                        </div>
                                        <div class="folder-details">
                                            <div><strong>Période:</strong> ${bulletin.periode}</div>
                                            <div><strong>Date d'archivage:</strong> ${dateGen.toLocaleDateString('fr-FR')}</div>
                                            <div><strong>Statut:</strong> ${bulletin.statut}</div>
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                    `;
                } else if (type === 'pointages') {
                    const pointages = await getArchivedPointages();
                    const users = await getUsers();
                    
                    // Enrichir les pointages avec les noms
                    const enrichedPointages = pointages.map(pointage => {
                        const employee = users.find(u => u.id === pointage.employee_id);
                        const chef = users.find(u => u.id === pointage.chef_id);
                        
                        return {
                            ...pointage,
                            employee_name: employee ? `${employee.prenom} ${employee.nom}` : 'N/A',
                            chef_name: chef ? `${chef.prenom} ${chef.nom}` : 'N/A'
                        };
                    });
                    
                    if (enrichedPointages.length === 0) {
                        archivesContent.innerHTML = `
                            <div class="empty-state">
                                <div class="empty-state-icon">📋</div>
                                <h3>Aucun pointage archivé</h3>
                                <p>Les pointages archivés apparaîtront ici</p>
                            </div>
                        `;
                        return;
                    }

                    // Grouper les pointages par semaine
                    const weeks = groupPointagesByWeek(enrichedPointages);
                    
                    archivesContent.innerHTML = `
                        <h4>📊 Archives des Pointages</h4>
                        <div class="archive-section">
                            ${Object.values(weeks).map(week => {
                                const weekStartFormatted = formatDateFr(week.startDate);
                                const weekEndFormatted = formatDateFr(week.endDate);
                                
                                return `
                                    <div class="archive-folder" onclick="toggleWeekContent('archive-${week.year}-${week.weekNumber}')">
                                        <div class="folder-header">
                                            <div class="folder-title">Semaine ${week.weekNumber} - ${week.year}</div>
                                            <div class="folder-count">${week.totalPointages} pointages</div>
                                        </div>
                                        <div class="folder-details">
                                            <div><strong>Période:</strong> ${weekStartFormatted} au ${weekEndFormatted}</div>
                                            <div><strong>Employés:</strong> ${week.employes.size}</div>
                                            <div><strong>Total:</strong> ${formatFCFA(week.totalPrix)}</div>
                                        </div>
                                        <div class="week-content" id="archive-${week.year}-${week.weekNumber}" style="display: none; margin-top: 1rem;">
                                            <div class="table-container">
                                                <table class="week-table">
                                                    <thead>
                                                        <tr>
                                                            <th>Date</th>
                                                            <th>Employé</th>
                                                            <th>Activité</th>
                                                            <th>Quantité</th>
                                                            <th>Prix total</th>
                                                            <th>Chef</th>
                                                        </tr>
                                                    </thead>
                                                    <tbody>
                                                        ${week.pointages.map(pointage => `
                                                            <tr>
                                                                <td>${pointage.date}</td>
                                                                <td>${pointage.employee_name}</td>
                                                                <td>${getActivityName(pointage.activity)}</td>
                                                                <td>${pointage.qty_total || 0}</td>
                                                                <td>${formatFCFA(pointage.total_price || 0)}</td>
                                                                <td>${pointage.chef_name}</td>
                                                            </tr>
                                                        `).join('')}
                                                    </tbody>
                                                </table>
                                            </div>
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                    `;
                }
                
            } catch (error) {
                console.error('Erreur lors du chargement des archives:', error);
                showAlert('Erreur lors du chargement des archives: ' + error.message, 'error');
            }
        }

        async function archiverBulletin(bulletinId) {
            if (confirm('Êtes-vous sûr de vouloir archiver ce bulletin ?')) {
                try {
                    const updates = { archived: true };
                    const result = await updateBulletin(bulletinId, updates);
                    
                    if (result) {
                        showAlert('Bulletin archivé avec succès', 'success');
                        loadBulletinsTable();
                    }
                } catch (error) {
                    console.error('Erreur lors de l\'archivage du bulletin:', error);
                    showAlert('Erreur lors de l\'archivage du bulletin: ' + error.message, 'error');
                }
            }
        }

        async function archiverPointage(pointageId) {
            if (confirm('Êtes-vous sûr de vouloir archiver ce pointage ?')) {
                try {
                    const updates = { archived: true };
                    const result = await updatePointage(pointageId, updates);
                    
                    if (result) {
                        showAlert('Pointage archivé avec succès', 'success');
                        loadAdminPointages();
                    }
                } catch (error) {
                    console.error('Erreur lors de l\'archivage du pointage:', error);
                    showAlert('Erreur lors de l\'archivage du pointage: ' + error.message, 'error');
                }
            }
        }

        async function archiverDonneesAnciennes() {
            if (confirm('Êtes-vous sûr de vouloir archiver les données de plus de 6 mois ? Cette action est irréversible.')) {
                try {
                    const sixMois = new Date();
                    sixMois.setMonth(sixMois.getMonth() - 6);
                    
                    // Archiver les bulletins anciens
                    const bulletins = await getBulletins();
                    let bulletinsArchives = 0;
                    
                    for (const bulletin of bulletins) {
                        const dateGen = new Date(bulletin.date_generation);
                        if (dateGen < sixMois && !bulletin.archived) {
                            await updateBulletin(bulletin.id, { archived: true });
                            bulletinsArchives++;
                        }
                    }
                    
                    // Archiver les pointages anciens
                    const pointages = await getPointages();
                    let pointagesArchives = 0;
                    
                    for (const pointage of pointages) {
                        const datePointage = new Date(pointage.date);
                        if (datePointage < sixMois && !pointage.archived) {
                            await updatePointage(pointage.id, { archived: true });
                            pointagesArchives++;
                        }
                    }
                    
                    showAlert(`${bulletinsArchives} bulletin(s) et ${pointagesArchives} pointage(s) archivés avec succès`, 'success');
                    loadBulletinsTable();
                    loadAdminPointages();
                    
                } catch (error) {
                    console.error('Erreur lors de l\'archivage des données anciennes:', error);
                    showAlert('Erreur lors de l\'archivage: ' + error.message, 'error');
                }
            }
        }

        // =============================================
        // FONCTIONS DE SÉLECTION MULTIPLE
        // =============================================

        function toggleSelectAllPointages() {
            const checkboxes = document.querySelectorAll('#pointagesTableBody input[type="checkbox"]');
            const selectAll = document.getElementById('selectAllPointages').checked;
            
            selectedPointages.clear();
            
            checkboxes.forEach(checkbox => {
                checkbox.checked = selectAll;
                if (selectAll) {
                    selectedPointages.add(checkbox.value);
                }
            });
            
            updateSelectedPointagesCount();
        }

        function togglePointageSelection(pointageId) {
            if (selectedPointages.has(pointageId)) {
                selectedPointages.delete(pointageId);
            } else {
                selectedPointages.add(pointageId);
            }
            
            updateSelectedPointagesCount();
            updateSelectAllPointagesCheckbox();
        }

        function updateSelectedPointagesCount() {
            const countElement = document.getElementById('selectedPointagesCount');
            countElement.textContent = `${selectedPointages.size} sélectionné(s)`;
        }

        function updateSelectAllPointagesCheckbox() {
            const checkboxes = document.querySelectorAll('#pointagesTableBody input[type="checkbox"]');
            const selectAll = document.getElementById('selectAllPointages');
            
            if (checkboxes.length === 0) {
                selectAll.checked = false;
                return;
            }
            
            const allChecked = Array.from(checkboxes).every(checkbox => checkbox.checked);
            selectAll.checked = allChecked;
        }

        function clearPointagesSelection() {
            selectedPointages.clear();
            const checkboxes = document.querySelectorAll('#pointagesTableBody input[type="checkbox"]');
            checkboxes.forEach(checkbox => checkbox.checked = false);
            updateSelectedPointagesCount();
            updateSelectAllPointagesCheckbox();
        }

        function toggleSelectAllBulletins() {
            const checkboxes = document.querySelectorAll('#bulletinsTableBody input[type="checkbox"]');
            const selectAll = document.getElementById('selectAllBulletins').checked;
            
            selectedBulletins.clear();
            
            checkboxes.forEach(checkbox => {
                checkbox.checked = selectAll;
                if (selectAll) {
                    selectedBulletins.add(checkbox.value);
                }
            });
            
            updateSelectedBulletinsCount();
        }

        function toggleBulletinSelection(bulletinId) {
            if (selectedBulletins.has(bulletinId)) {
                selectedBulletins.delete(bulletinId);
            } else {
                selectedBulletins.add(bulletinId);
            }
            
            updateSelectedBulletinsCount();
            updateSelectAllBulletinsCheckbox();
        }

        function updateSelectedBulletinsCount() {
            const countElement = document.getElementById('selectedBulletinsCount');
            countElement.textContent = `${selectedBulletins.size} sélectionné(s)`;
        }

        function updateSelectAllBulletinsCheckbox() {
            const checkboxes = document.querySelectorAll('#bulletinsTableBody input[type="checkbox"]');
            const selectAll = document.getElementById('selectAllBulletins');
            
            if (checkboxes.length === 0) {
                selectAll.checked = false;
                return;
            }
            
            const allChecked = Array.from(checkboxes).every(checkbox => checkbox.checked);
            selectAll.checked = allChecked;
        }

        function clearBulletinsSelection() {
            selectedBulletins.clear();
            const checkboxes = document.querySelectorAll('#bulletinsTableBody input[type="checkbox"]');
            checkboxes.forEach(checkbox => checkbox.checked = false);
            updateSelectedBulletinsCount();
            updateSelectAllBulletinsCheckbox();
        }

        // =============================================
        // FONCTIONS POUR LE MODAL D'ARCHIVAGE
        // =============================================

        function showArchiveModal(type) {
            const modal = document.getElementById('archiveModal');
            const modalTitle = document.getElementById('modalTitle');
            const modalContent = document.getElementById('modalContent');
            
            if (type === 'bulletins') {
                modalTitle.textContent = 'Archiver des bulletins de paie';
                modalContent.innerHTML = `
                    <p>Sélectionnez les bulletins à archiver :</p>
                    <div class="archive-options">
                        <div class="archive-option selected" onclick="selectArchiveOption(this, 'selected')">
                            <div class="option-icon">📋</div>
                            <div class="option-content">
                                <div class="option-title">Bulletins sélectionnés</div>
                                <div class="option-description">Archiver uniquement les bulletins actuellement sélectionnés</div>
                            </div>
                        </div>
                        <div class="archive-option" onclick="selectArchiveOption(this, 'all')">
                            <div class="option-icon">📦</div>
                            <div class="option-content">
                                <div class="option-title">Tous les bulletins</div>
                                <div class="option-description">Archiver tous les bulletins de paie</div>
                            </div>
                        </div>
                        <div class="archive-option" onclick="selectArchiveOption(this, 'old')">
                            <div class="option-icon">🕐</div>
                            <div class="option-content">
                                <div class="option-title">Bulletins anciens</div>
                                <div class="option-description">Archiver les bulletins de plus de 6 mois</div>
                            </div>
                        </div>
                    </div>
                    <div style="margin-top: 1.5rem; text-align: center;">
                        <button class="btn btn-warning" onclick="archiverBulletinsSelection()">📦 Archiver</button>
                        <button class="btn btn-outline" onclick="closeArchiveModal()" style="margin-left: 0.5rem;">Annuler</button>
                    </div>
                `;
            } else if (type === 'pointages') {
                modalTitle.textContent = 'Archiver des fiches de pointage';
                modalContent.innerHTML = `
                    <p>Sélectionnez les pointages à archiver :</p>
                    <div class="archive-options">
                        <div class="archive-option selected" onclick="selectArchiveOption(this, 'selected')">
                            <div class="option-icon">📋</div>
                            <div class="option-content">
                                <div class="option-title">Pointages sélectionnés</div>
                                <div class="option-description">Archiver uniquement les pointages actuellement sélectionnés</div>
                            </div>
                        </div>
                        <div class="archive-option" onclick="selectArchiveOption(this, 'all')">
                            <div class="option-icon">📦</div>
                            <div class="option-content">
                                <div class="option-title">Tous les pointages</div>
                                <div class="option-description">Archiver tous les pointages</div>
                            </div>
                        </div>
                        <div class="archive-option" onclick="selectArchiveOption(this, 'old')">
                            <div class="option-icon">🕐</div>
                            <div class="option-content">
                                <div class="option-title">Pointages anciens</div>
                                <div class="option-description">Archiver les pointages de plus de 3 mois</div>
                            </div>
                        </div>
                    </div>
                    <div style="margin-top: 1.5rem; text-align: center;">
                        <button class="btn btn-warning" onclick="archiverPointagesSelection()">📦 Archiver</button>
                        <button class="btn btn-outline" onclick="closeArchiveModal()" style="margin-left: 0.5rem;">Annuler</button>
                    </div>
                `;
            }
            
            modal.style.display = 'flex';
        }

        function closeArchiveModal() {
            const modal = document.getElementById('archiveModal');
            modal.style.display = 'none';
        }

        function selectArchiveOption(element, option) {
            // Retirer la classe selected de toutes les options
            document.querySelectorAll('.archive-option').forEach(opt => {
                opt.classList.remove('selected');
            });
            
            // Ajouter la classe selected à l'option cliquée
            element.classList.add('selected');
            
            // Stocker l'option sélectionnée
            element.dataset.option = option;
        }

        async function archiverBulletinsSelection() {
            const selectedOption = document.querySelector('.archive-option.selected');
            const optionType = selectedOption ? selectedOption.dataset.option : 'selected';
            
            try {
                let bulletinsAArchiver = [];
                
                if (optionType === 'selected') {
                    // Archiver les bulletins sélectionnés
                    if (selectedBulletins.size === 0) {
                        showAlert('Aucun bulletin sélectionné', 'error');
                        return;
                    }
                    
                    for (const bulletinId of selectedBulletins) {
                        const updates = { archived: true };
                        await updateBulletin(bulletinId, updates);
                        bulletinsAArchiver.push(bulletinId);
                    }
                } else if (optionType === 'all') {
                    // Archiver tous les bulletins
                    const bulletins = await getBulletins();
                    for (const bulletin of bulletins) {
                        if (!bulletin.archived) {
                            const updates = { archived: true };
                            await updateBulletin(bulletin.id, updates);
                            bulletinsAArchiver.push(bulletin.id);
                        }
                    }
                } else if (optionType === 'old') {
                    // Archiver les bulletins anciens (plus de 6 mois)
                    const bulletins = await getBulletins();
                    const sixMois = new Date();
                    sixMois.setMonth(sixMois.getMonth() - 6);
                    
                    for (const bulletin of bulletins) {
                        const dateGen = new Date(bulletin.date_generation);
                        if (dateGen < sixMois && !bulletin.archived) {
                            const updates = { archived: true };
                            await updateBulletin(bulletin.id, updates);
                            bulletinsAArchiver.push(bulletin.id);
                        }
                    }
                }
                
                closeArchiveModal();
                showAlert(`${bulletinsAArchiver.length} bulletin(s) archivé(s) avec succès`, 'success');
                loadBulletinsTable();
                clearBulletinsSelection();
                
            } catch (error) {
                console.error('Erreur lors de l\'archivage des bulletins:', error);
                showAlert('Erreur lors de l\'archivage des bulletins: ' + error.message, 'error');
            }
        }

        async function archiverPointagesSelection() {
            const selectedOption = document.querySelector('.archive-option.selected');
            const optionType = selectedOption ? selectedOption.dataset.option : 'selected';
            
            try {
                let pointagesAArchiver = [];
                
                if (optionType === 'selected') {
                    // Archiver les pointages sélectionnés
                    if (selectedPointages.size === 0) {
                        showAlert('Aucun pointage sélectionné', 'error');
                        return;
                    }
                    
                    for (const pointageId of selectedPointages) {
                        const updates = { archived: true };
                        await updatePointage(pointageId, updates);
                        pointagesAArchiver.push(pointageId);
                    }
                } else if (optionType === 'all') {
                    // Archiver tous les pointages
                    const pointages = await getPointages();
                    for (const pointage of pointages) {
                        if (!pointage.archived) {
                            const updates = { archived: true };
                            await updatePointage(pointage.id, updates);
                            pointagesAArchiver.push(pointage.id);
                        }
                    }
                } else if (optionType === 'old') {
                    // Archiver les pointages anciens (plus de 3 mois)
                    const pointages = await getPointages();
                    const troisMois = new Date();
                    troisMois.setMonth(troisMois.getMonth() - 3);
                    
                    for (const pointage of pointages) {
                        const datePointage = new Date(pointage.date);
                        if (datePointage < troisMois && !pointage.archived) {
                            const updates = { archived: true };
                            await updatePointage(pointage.id, updates);
                            pointagesAArchiver.push(pointage.id);
                        }
                    }
                }
                
                closeArchiveModal();
                showAlert(`${pointagesAArchiver.length} pointage(s) archivé(s) avec succès`, 'success');
                loadAdminPointages();
                clearPointagesSelection();
                
            } catch (error) {
                console.error('Erreur lors de l\'archivage des pointages:', error);
                showAlert('Erreur lors de l\'archivage des pointages: ' + error.message, 'error');
            }
        }

        // =============================================
        // FONCTIONS POUR LES BULLETINS EMPLOYÉ
        // =============================================

        async function loadEmployeeBulletins() {
            const user = getCurrentUser();
            if (!user || user.role !== 'EMPLOYE') return;

            try {
                const bulletins = await getBulletinsByEmployee(user.id);
                const container = document.getElementById('employeeBulletinsContainer');
                
                if (bulletins.length === 0) {
                    container.innerHTML = `
                        <div class="empty-state">
                            <div class="empty-state-icon">💰</div>
                            <h3>Aucun bulletin de paie disponible</h3>
                            <p>Vos bulletins de paie apparaîtront ici une fois générés par l'administrateur</p>
                        </div>
                    `;
                    return;
                }

                container.innerHTML = bulletins.map(bulletin => {
                    const dateGen = new Date(bulletin.date_generation);
                    const moisAnnee = dateGen.toLocaleDateString('fr-FR', { 
                        month: 'long', 
                        year: 'numeric' 
                    });
                    
                    return `
                        <div class="archive-folder" onclick="viewEmployeeBulletin(${bulletin.id})">
                            <div class="folder-header">
                                <div class="folder-title">Bulletin ${moisAnnee}</div>
                                <div class="folder-count">${formatFCFA(bulletin.net_a_payer)}</div>
                            </div>
                            <div class="folder-details">
                                <div><strong>Période:</strong> ${bulletin.periode}</div>
                                <div><strong>Salaire brut:</strong> ${formatFCFA(bulletin.salaire_brut)}</div>
                                <div><strong>Net à payer:</strong> ${formatFCFA(bulletin.net_a_payer)}</div>
                                <div><strong>Statut:</strong> ${bulletin.statut}</div>
                            </div>
                        </div>
                    `;
                }).join('');
            } catch (error) {
                console.error('Erreur lors du chargement des bulletins employé:', error);
                showAlert('Erreur lors du chargement des bulletins: ' + error.message, 'error');
            }
        }

        async function viewEmployeeBulletin(bulletinId) {
            try {
                const bulletins = await getBulletinsByEmployee(getCurrentUser().id);
                const bulletin = bulletins.find(b => b.id === bulletinId);
                
                if (!bulletin) {
                    showAlert('Bulletin non trouvé', 'error');
                    return;
                }

                document.getElementById('bulletinContent').innerHTML = genererBulletinHTML(bulletin);
                showSection('bulletinDetail');
            } catch (error) {
                console.error('Erreur lors de l\'affichage du bulletin:', error);
                showAlert('Erreur lors de l\'affichage du bulletin: ' + error.message, 'error');
            }
        }

        // =============================================
        // FONCTIONS POUR LA MODIFICATION DES UTILISATEURS
        // =============================================

        async function editUser(userId) {
            try {
                const users = await getUsers();
                const user = users.find(u => u.id === userId);
                
                if (!user) {
                    showAlert('Utilisateur non trouvé', 'error');
                    return;
                }

                // Remplir le formulaire de modification
                document.getElementById('editUserId').value = user.id;
                document.getElementById('editUserRole').value = user.role;
                document.getElementById('editUsername').value = user.username;
                document.getElementById('editNom').value = user.nom;
                document.getElementById('editPrenom').value = user.prenom;
                document.getElementById('editDepartement').value = user.departement;
                document.getElementById('editTelephone').value = user.telephone || '';
                document.getElementById('editEmail').value = user.email || '';
                document.getElementById('editColor').value = user.color;

                // Gérer l'affichage de la photo
                const photoPreview = document.getElementById('editPhotoPreview');
                if (user.photo) {
                    photoPreview.innerHTML = '';
                    const img = document.createElement('img');
                    img.src = user.photo;
                    img.className = 'photo-preview';
                    photoPreview.appendChild(img);
                } else {
                    photoPreview.innerHTML = '👤';
                    photoPreview.className = 'photo-placeholder';
                }

                // Gérer les champs d'activité
                toggleEditActivityField();
                if (user.role === 'CHEF') {
                    document.getElementById('editActivity').value = user.activity || 'recolte';
                } else if (user.role === 'EMPLOYE') {
                    document.getElementById('editEmployeeActivity').value = user.activity || 'recolte';
                }

                showSection('adminEditUser');
            } catch (error) {
                console.error('Erreur lors du chargement des données utilisateur:', error);
                showAlert('Erreur lors du chargement des données: ' + error.message, 'error');
            }
        }

        function toggleEditActivityField() {
            const role = document.getElementById('editUserRole').value;
            const activityField = document.getElementById('editActivityField');
            const employeeActivityField = document.getElementById('editEmployeeActivityField');
            
            if (role === 'CHEF') {
                activityField.style.display = 'block';
                employeeActivityField.style.display = 'none';
                document.getElementById('editActivity').required = true;
                document.getElementById('editEmployeeActivity').required = false;
            } else if (role === 'EMPLOYE') {
                activityField.style.display = 'none';
                employeeActivityField.style.display = 'block';
                document.getElementById('editActivity').required = false;
                document.getElementById('editEmployeeActivity').required = true;
            } else {
                activityField.style.display = 'none';
                employeeActivityField.style.display = 'none';
                document.getElementById('editActivity').required = false;
                document.getElementById('editEmployeeActivity').required = false;
            }
        }

        function previewEditPhoto(event) {
            const input = event.target;
            const preview = document.getElementById('editPhotoPreview');
            
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    preview.innerHTML = '';
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.className = 'photo-preview';
                    preview.appendChild(img);
                }
                
                reader.readAsDataURL(input.files[0]);
            }
        }

        async function handleEditUser(event) {
            event.preventDefault();
            
            try {
                const userId = document.getElementById('editUserId').value;
                const photoData = await getEditPhotoData();
                const role = document.getElementById('editUserRole').value;
                
                const updatedUser = {
                    username: document.getElementById('editUsername').value,
                    role: role,
                    color: document.getElementById('editColor').value,
                    nom: document.getElementById('editNom').value,
                    prenom: document.getElementById('editPrenom').value,
                    departement: document.getElementById('editDepartement').value,
                    telephone: document.getElementById('editTelephone').value,
                    email: document.getElementById('editEmail').value,
                    activity: role === 'CHEF' ? document.getElementById('editActivity').value : 
                             role === 'EMPLOYE' ? document.getElementById('editEmployeeActivity').value : null
                };

                // Ne mettre à jour le mot de passe que s'il est renseigné
                const password = document.getElementById('editPassword').value;
                if (password) {
                    updatedUser.password = password;
                }

                // Ne mettre à jour la photo que si une nouvelle est sélectionnée
                if (photoData) {
                    updatedUser.photo = photoData;
                }

                const users = await getUsers();
                const existingUser = users.find(u => u.username === updatedUser.username && u.id !== parseInt(userId));
                
                if (existingUser) {
                    showAlert('Cet identifiant est déjà utilisé par un autre utilisateur', 'error');
                    return;
                }

                const result = await updateUser(userId, updatedUser);
                
                if (result) {
                    showAlert('Utilisateur modifié avec succès', 'success');
                    showSection('adminUsers');
                    loadUsersTable();
                }
            } catch (error) {
                console.error('Erreur lors de la modification de l\'utilisateur:', error);
                showAlert('Erreur lors de la modification de l\'utilisateur: ' + error.message, 'error');
            }
        }

        function getEditPhotoData() {
            const input = document.getElementById('editPhotoInput');
            if (input.files && input.files[0]) {
                return new Promise((resolve) => {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        resolve(e.target.result);
                    };
                    reader.readAsDataURL(input.files[0]);
                });
            }
            return Promise.resolve(null);
        }

        // =============================================
        // FONCTIONS POUR LA GESTION DES POINTAGES PAR SEMAINE
        // =============================================

        // Fonction pour grouper les pointages par semaine
        function groupPointagesByWeek(pointages) {
            const weeks = {};
            
            pointages.forEach(pointage => {
                const date = new Date(pointage.date);
                const weekNumber = getWeekNumber(date);
                const year = date.getFullYear();
                const weekKey = `${year}-${weekNumber}`;
                
                if (!weeks[weekKey]) {
                    const weekStart = getStartOfWeek(date);
                    const weekEnd = getEndOfWeek(date);
                    
                    weeks[weekKey] = {
                        weekNumber: weekNumber,
                        year: year,
                        startDate: weekStart,
                        endDate: weekEnd,
                        pointages: [],
                        totalPointages: 0,
                        totalQuantite: 0,
                        totalPrix: 0,
                        employes: new Set()
                    };
                }
                
                weeks[weekKey].pointages.push(pointage);
                weeks[weekKey].totalPointages++;
                weeks[weekKey].totalQuantite += pointage.qty_total || 0;
                weeks[weekKey].totalPrix += pointage.total_price || 0;
                weeks[weekKey].employes.add(pointage.employee_id);
            });
            
            return weeks;
        }

        // Obtenir le numéro de semaine ISO
        function getWeekNumber(date) {
            const d = new Date(Date.UTC(date.getFullYear(), date.getMonth(), date.getDate()));
            const dayNum = d.getUTCDay() || 7;
            d.setUTCDate(d.getUTCDate() + 4 - dayNum);
            const yearStart = new Date(Date.UTC(d.getUTCFullYear(), 0, 1));
            return Math.ceil((((d - yearStart) / 86400000) + 1) / 7);
        }

        // Obtenir le début de la semaine (lundi)
        function getStartOfWeek(date) {
            const d = new Date(date);
            const day = d.getDay();
            const diff = d.getDate() - day + (day === 0 ? -6 : 1);
            return new Date(d.setDate(diff));
        }

        // Obtenir la fin de la semaine (dimanche)
        function getEndOfWeek(date) {
            const start = getStartOfWeek(date);
            const end = new Date(start);
            end.setDate(start.getDate() + 6);
            return end;
        }

        // Formater une date en français
        function formatDateFr(date) {
            return date.toLocaleDateString('fr-FR', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            });
        }

        // Générer l'affichage des pointages par semaine
        function generateWeeklyPointagesDisplay(weeks, userRole = 'admin') {
            let html = '';
            
            // Trier les semaines par date (plus récentes en premier)
            const sortedWeeks = Object.values(weeks).sort((a, b) => 
                new Date(b.startDate) - new Date(a.startDate)
            );
            
            if (sortedWeeks.length === 0) {
                return `
                    <div class="empty-state">
                        <div class="empty-state-icon">📋</div>
                        <h3>Aucun pointage trouvé</h3>
                        <p>Les pointages apparaîtront ici une fois créés</p>
                    </div>
                `;
            }
            
            sortedWeeks.forEach(week => {
                const weekStartFormatted = formatDateFr(week.startDate);
                const weekEndFormatted = formatDateFr(week.endDate);
                const uniqueEmployes = week.employes.size;
                
                html += `
                    <div class="week-container">
                        <div class="week-header" onclick="toggleWeekContent('${week.year}-${week.weekNumber}')">
                            <div>
                                <div class="week-title">Semaine ${week.weekNumber} - ${week.year}</div>
                                <div class="week-dates">${weekStartFormatted} au ${weekEndFormatted}</div>
                            </div>
                            <div class="week-stats">
                                <div class="week-stat">${week.totalPointages} pointages</div>
                                <div class="week-stat">${uniqueEmployes} employés</div>
                                <div class="week-stat">${week.totalQuantite.toFixed(2)} quantité</div>
                                <div class="week-stat">${formatFCFA(week.totalPrix)}</div>
                            </div>
                        </div>
                        <div class="week-content" id="week-${week.year}-${week.weekNumber}">
                            <div class="table-container">
                                <table class="week-table">
                                    <thead>
                                        <tr>
                                            ${userRole === 'admin' ? '<th>ID</th>' : ''}
                                            <th>Date</th>
                                            <th>Employé</th>
                                            <th>Présence</th>
                                            <th>Activité</th>
                                            <th>Bloc</th>
                                            <th>Sous-quantités</th>
                                            <th>Quantité totale</th>
                                            <th>Prix unitaire</th>
                                            <th>Prix total</th>
                                            ${userRole === 'admin' ? '<th>Chef</th>' : ''}
                                        </tr>
                                    </thead>
                                    <tbody>
                                        ${week.pointages.map(pointage => {
                                            const subQuantities = pointage.sub_quantities || [];
                                            const sousQuantitesFormatees = subQuantities.length > 0 ? subQuantities.join('+') : '-';
                                            const isPresent = pointage.presence === 'Présent';
                                            
                                            return `
                                                <tr>
                                                    ${userRole === 'admin' ? `<td>${pointage.id}</td>` : ''}
                                                    <td>${pointage.date}</td>
                                                    <td>${pointage.employee_name || 'N/A'}</td>
                                                    <td>
                                                        <span style="color: ${isPresent ? 'var(--success)' : 'var(--danger)'}; font-weight: 500;">
                                                            ${pointage.presence}
                                                        </span>
                                                    </td>
                                                    <td>${getActivityName(pointage.activity)}</td>
                                                    <td>${pointage.bloc || '-'}</td>
                                                    <td>${sousQuantitesFormatees}</td>
                                                    <td>${pointage.qty_total || 0}</td>
                                                    <td>${formatFCFA(pointage.unit_price || 0)}</td>
                                                    <td style="font-weight: 500;">${formatFCFA(pointage.total_price || 0)}</td>
                                                    ${userRole === 'admin' ? `<td>${pointage.chef_name || 'N/A'}</td>` : ''}
                                                </tr>
                                            `;
                                        }).join('')}
                                        <tr class="week-total">
                                            ${userRole === 'admin' ? '<td colspan="6"></td>' : '<td colspan="5"></td>'}
                                            <td><strong>Total semaine:</strong></td>
                                            <td><strong>${week.totalQuantite.toFixed(2)}</strong></td>
                                            <td></td>
                                            <td><strong>${formatFCFA(week.totalPrix)}</strong></td>
                                            ${userRole === 'admin' ? '<td></td>' : ''}
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                `;
            });
            
            return html;
        }

        // Basculer l'affichage du contenu d'une semaine
        function toggleWeekContent(weekId) {
            const content = document.getElementById(`week-${weekId}`);
            content.classList.toggle('expanded');
        }

        // =============================================
        // FONCTIONS POUR LA GESTION DE LA PAIE (CORRIGÉES)
        // =============================================

        // Générer un bulletin de paie professionnel
        function genererBulletinHTML(bulletin) {
            const user = getCurrentUser();
            const isAdmin = user.role === 'ADMINISTRATEUR';
            
            return `
                <div class="bulletin-content">
                    <!-- En-tête -->
                    <div class="bulletin-header">
                        <div class="company-info">
                            <div class="company-logo">
                                <div class="logo-icon">🌴</div>
                                <div class="company-name">MKJ SERVICE</div>
                            </div>
                            <div class="company-details">
                                Plantation de palmiers à huile<br>
                                BP 1234, Makouké, Gabon<br>
                                Tél: +212710716991<br>
                                Email: contact@mkj-service.com
                            </div>
                        </div>
                        
                        <div class="document-title">
                            <div class="title-main">BULLETIN DE PAIE</div>
                            <div class="title-sub">Période: ${bulletin.periode}</div>
                        </div>
                        
                        <div class="employee-header-section">
                            <div class="employee-photo">
                                ${bulletin.employee_photo ? 
                                    `<img src="${bulletin.employee_photo}" style="width:100%;height:100%;object-fit:cover;">` : 
                                    `<div class="photo-placeholder">PHOTO</div>`
                                }
                            </div>
                            <div class="employee-details-compact">
                                <div class="info-row">
                                    <div class="info-label">Matricule:</div>
                                    <div class="info-value">${bulletin.employee_id}</div>
                                </div>
                                <div class="info-row">
                                    <div class="info-label">Nom:</div>
                                    <div class="info-value">${bulletin.employee_nom}</div>
                                </div>
                                <div class="info-row">
                                    <div class="info-label">Prénom:</div>
                                    <div class="info-value">${bulletin.employee_prenom}</div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Informations de période -->
                    <div class="period-info">
                        <div class="period-dates">
                            <div class="period-item">
                                <div class="period-label">Période:</div>
                                <div>${bulletin.periode}</div>
                            </div>
                            <div class="period-item">
                                <div class="period-label">Date de paie:</div>
                                <div>${new Date(bulletin.date_generation).toLocaleDateString('fr-FR')}</div>
                            </div>
                        </div>
                        <div class="period-item">
                            <div class="period-label">Statut:</div>
                            <div style="color: var(--success); font-weight: 600;">${bulletin.statut}</div>
                        </div>
                    </div>

                    <!-- Tableau principal -->
                    <div class="table-container-bulletin">
                        <table class="main-table">
                            <thead>
                                <tr>
                                    <th class="designation">DÉSIGNATION</th>
                                    <th class="number">NOMBRE</th>
                                    <th class="base">BASE</th>
                                    <th class="rate">TAUX %</th>
                                    <th class="gains">GAINS</th>
                                    <th class="deductions">RETENUES</th>
                                    <th class="net">NET</th>
                                </tr>
                            </thead>
                            <tbody>
                                <!-- Salaire de base -->
                                <tr class="activity-row">
                                    <td class="designation">Salaire de base</td>
                                    <td class="number">1</td>
                                    <td class="base">${formatFCFA(bulletin.salaire_base)}</td>
                                    <td class="rate">100%</td>
                                    <td class="gains">${formatFCFA(bulletin.salaire_base)}</td>
                                    <td class="deductions">-</td>
                                    <td class="net">${formatFCFA(bulletin.salaire_base)}</td>
                                </tr>
                                
                                <!-- Heures supplémentaires -->
                                ${bulletin.heures_supplementaires > 0 ? `
                                <tr>
                                    <td class="designation">Heures supplémentaires</td>
                                    <td class="number">${bulletin.heures_supplementaires}</td>
                                    <td class="base">${formatFCFA(bulletin.taux_horaire)}</td>
                                    <td class="rate">125%</td>
                                    <td class="gains">${formatFCFA(bulletin.montant_heures_supp)}</td>
                                    <td class="deductions">-</td>
                                    <td class="net">${formatFCFA(bulletin.montant_heures_supp)}</td>
                                </tr>
                                ` : ''}
                                
                                <!-- Primes -->
                                ${bulletin.prime_anciennete > 0 ? `
                                <tr>
                                    <td class="designation">Prime d'ancienneté</td>
                                    <td class="number">-</td>
                                    <td class="base">-</td>
                                    <td class="rate">-</td>
                                    <td class="gains">${formatFCFA(bulletin.prime_anciennete)}</td>
                                    <td class="deductions">-</td>
                                    <td class="net">${formatFCFA(bulletin.prime_anciennete)}</td>
                                </tr>
                                ` : ''}
                                
                                ${bulletin.prime_rendement > 0 ? `
                                <tr>
                                    <td class="designation">Prime de rendement</td>
                                    <td class="number">-</td>
                                    <td class="base">-</td>
                                    <td class="rate">-</td>
                                    <td class="gains">${formatFCFA(bulletin.prime_rendement)}</td>
                                    <td class="deductions">-</td>
                                    <td class="net">${formatFCFA(bulletin.prime_rendement)}</td>
                                </tr>
                                ` : ''}
                                
                                <!-- Sous-total gains -->
                                <tr class="subtotal">
                                    <td class="designation">TOTAL DES GAINS</td>
                                    <td class="number"></td>
                                    <td class="base"></td>
                                    <td class="rate"></td>
                                    <td class="gains">${formatFCFA(bulletin.salaire_brut)}</td>
                                    <td class="deductions"></td>
                                    <td class="net">${formatFCFA(bulletin.salaire_brut)}</td>
                                </tr>
                                
                                <!-- Cotisations sociales -->
                                <tr>
                                    <td class="designation">CNPS (Retraite)</td>
                                    <td class="number">-</td>
                                    <td class="base">${formatFCFA(bulletin.base_cnps)}</td>
                                    <td class="rate">${bulletin.taux_cnps}%</td>
                                    <td class="gains">-</td>
                                    <td class="deductions">${formatFCFA(bulletin.montant_cnps)}</td>
                                    <td class="net">-${formatFCFA(bulletin.montant_cnps)}</td>
                                </tr>
                                
                                <tr>
                                    <td class="designation">Assurance maladie</td>
                                    <td class="number">-</td>
                                    <td class="base">${formatFCFA(bulletin.base_assurance)}</td>
                                    <td class="rate">${bulletin.taux_assurance}%</td>
                                    <td class="gains">-</td>
                                    <td class="deductions">${formatFCFA(bulletin.montant_assurance)}</td>
                                    <td class="net">-${formatFCFA(bulletin.montant_assurance)}</td>
                                </tr>
                                
                                <!-- IRPP -->
                                ${bulletin.montant_irpp > 0 ? `
                                <tr>
                                    <td class="designation">IRPP (Impôt sur le revenu)</td>
                                    <td class="number">-</td>
                                    <td class="base">${formatFCFA(bulletin.base_irpp)}</td>
                                    <td class="rate">${bulletin.taux_irpp}%</td>
                                    <td class="gains">-</td>
                                    <td class="deductions">${formatFCFA(bulletin.montant_irpp)}</td>
                                    <td class="net">-${formatFCFA(bulletin.montant_irpp)}</td>
                                </tr>
                                ` : ''}
                                
                                <!-- Sous-total retenues -->
                                <tr class="subtotal">
                                    <td class="designation">TOTAL DES RETENUES</td>
                                    <td class="number"></td>
                                    <td class="base"></td>
                                    <td class="rate"></td>
                                    <td class="gains"></td>
                                    <td class="deductions">${formatFCFA(bulletin.total_retenues)}</td>
                                    <td class="net">-${formatFCFA(bulletin.total_retenues)}</td>
                                </tr>
                                
                                <!-- Net à payer -->
                                <tr class="total">
                                    <td class="designation">NET À PAYER</td>
                                    <td class="number"></td>
                                    <td class="base"></td>
                                    <td class="rate"></td>
                                    <td class="gains"></td>
                                    <td class="deductions"></td>
                                    <td class="net">${formatFCFA(bulletin.net_a_payer)}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>

                    <!-- Récapitulatif -->
                    <div class="summary-section">
                        <div class="summary-left">
                            <div class="summary-title">RÉCAPITULATIF COTISATIONS PATRONALES</div>
                            <table class="summary-table">
                                <tr>
                                    <td class="label">CNPS Patronale</td>
                                    <td class="value">${formatFCFA(bulletin.cnps_patronale)}</td>
                                </tr>
                                <tr>
                                    <td class="label">Assurance Patronale</td>
                                    <td class="value">${formatFCFA(bulletin.assurance_patronale)}</td>
                                </tr>
                                <tr>
                                    <td class="label">Taxe de formation</td>
                                    <td class="value">${formatFCFA(bulletin.taxe_formation)}</td>
                                </tr>
                                <tr class="total-row">
                                    <td class="label">Total charges patronales</td>
                                    <td class="value">${formatFCFA(bulletin.total_charges_patronales)}</td>
                                </tr>
                            </table>
                        </div>
                        
                        <div class="summary-right">
                            <div class="summary-title">COÛT TOTAL EMPLOYEUR</div>
                            <table class="summary-table">
                                <tr>
                                    <td class="label">Salaire brut</td>
                                    <td class="value">${formatFCFA(bulletin.salaire_brut)}</td>
                                </tr>
                                <tr>
                                    <td class="label">Charges patronales</td>
                                    <td class="value">${formatFCFA(bulletin.total_charges_patronales)}</td>
                                </tr>
                                <tr class="total-row">
                                    <td class="label">Coût total employeur</td>
                                    <td class="value">${formatFCFA(bulletin.cout_total_employeur)}</td>
                                </tr>
                            </table>
                        </div>
                    </div>

                    <!-- Pied de page -->
                    <div class="bulletin-footer">
                        <div class="legal-mentions">
                            Le présent bulletin est établi en double exemplaire, l'un remis à l'intéressé, l'autre conservé par l'employeur.<br>
                            En cas de différence, les écritures comptables de l'employeur feront seules foi.
                        </div>
                        
                        <div class="signature-section">
                            <div class="signature-stamp">
                                Cachet et<br>Signature
                            </div>
                            <div class="signature-line">
                                Le Responsable des Ressources Humaines
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // =============================================
        // INITIALISATION DE L'APPLICATION
        // =============================================

        // Au chargement de la page
        document.addEventListener('DOMContentLoaded', function() {
            // Vérifier si un utilisateur est déjà connecté
            const currentUser = getCurrentUser();
            if (currentUser) {
                updateUIForUser(currentUser);
                showSection('dashboard');
            } else {
                showSection('home');
            }

            // Initialiser la date du jour pour les formulaires
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('presenceDate').value = today;
            document.getElementById('pointageDate').value = today;

            // Afficher un message de bienvenue
            console.log('🌴 MKJ SERVICE - Système de gestion du personnel chargé avec succès');
        });

        // Gestion des erreurs globales
        window.addEventListener('error', function(e) {
            console.error('Erreur globale:', e.error);
            showAlert('Une erreur est survenue dans l\'application', 'error');
        });

        // Gestion des promesses rejetées
        window.addEventListener('unhandledrejection', function(e) {
            console.error('Promesse rejetée:', e.reason);
            showAlert('Erreur: ' + (e.reason?.message || 'Erreur inconnue'), 'error');
            e.preventDefault();
        });

    </script>
</body>
</html>
