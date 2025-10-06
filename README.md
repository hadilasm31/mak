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
    }

    /* Header */
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
    }

    .logo {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        flex-shrink: 0;
    }

    .logo-icon {
        font-size: 1.8rem;
        color: var(--admin-color);
    }

    .logo h1 {
        font-size: 1.3rem;
        font-weight: 700;
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

    /* Main Content */
    .main-content {
        flex: 1;
        padding: 1rem;
        max-width: 1200px;
        margin: 0 auto;
        width: 100%;
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
    }

    table {
        width: 100%;
        border-collapse: collapse;
        background: white;
        border-radius: 8px;
        overflow: hidden;
        box-shadow: var(--shadow);
        min-width: 600px;
    }

    th, td {
        padding: 0.8rem;
        text-align: left;
        border-bottom: 1px solid var(--border);
        font-size: 0.85rem;
    }

    th {
        background: var(--admin-color);
        color: white;
        font-weight: 600;
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
    .table-container {
        flex: 1;
        overflow: hidden;
        margin-bottom: 10px;
    }

    .main-table {
        width: 100%;
        border-collapse: collapse;
        font-size: 8px;
    }

    .main-table th {
        background-color: var(--header-bg);
        border: 1px solid var(--border-color);
        padding: 6px 3px;
        text-align: center;
        font-weight: 600;
        color: var(--primary-color);
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

    /* Hidden sections */
    .section {
        display: none;
    }

    .section.active {
        display: block;
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
    }

    /* Petits mobiles */
    @media (max-width: 480px) {
        .header {
            padding: 0.8rem;
        }
        
        .logo h1 {
            font-size: 1.1rem;
        }
        
        .logo-icon {
            font-size: 1.5rem;
        }
        
        .nav a {
            padding: 0.3rem 0.6rem;
            font-size: 0.8rem;
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
    }

    /* Très petits écrans */
    @media (max-width: 360px) {
        .logo h1 {
            font-size: 1rem;
        }
        
        .nav a {
            padding: 0.25rem 0.5rem;
            font-size: 0.75rem;
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
    }

    /* Orientation paysage sur mobiles */
    @media (max-height: 500px) and (orientation: landscape) {
        .header {
            padding: 0.5rem;
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
