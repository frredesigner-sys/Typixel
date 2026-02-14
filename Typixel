<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="mobile-web-app-capable" content="yes">
    <title>Typixel - Graphic Design Management</title>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #6366f1;
            --primary-dark: #4f46e5;
            --secondary: #8b5cf6;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --info: #3b82f6;
            --dark: #1f2937;
            --light: #f9fafb;
            --text: #111827;
            --text-muted: #6b7280;
            --border: #e5e7eb;
            --shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
            --shadow-lg: 0 10px 25px rgba(0,0,0,0.1);
            --radius: 12px;
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        [data-theme="dark"] {
            --light: #111827;
            --text: #f9fafb;
            --text-muted: #9ca3af;
            --border: #374151;
            --dark: #f9fafb;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--light);
            color: var(--text);
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            overflow-x: hidden;
        }

        /* Mobile First Layout */
        .app-container {
            display: flex;
            min-height: 100vh;
            position: relative;
        }

        /* Mobile Sidebar */
        .sidebar {
            position: fixed;
            top: 0;
            left: -280px;
            width: 280px;
            height: 100vh;
            background: var(--dark);
            color: white;
            transition: var(--transition);
            z-index: 1000;
            overflow-y: auto;
        }

        .sidebar.active {
            left: 0;
            box-shadow: var(--shadow-lg);
        }

        .sidebar-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 999;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
        }

        .sidebar-overlay.active {
            opacity: 1;
            visibility: visible;
        }

        /* Desktop Sidebar */
        @media (min-width: 1024px) {
            .sidebar {
                position: relative;
                left: 0;
                width: 280px;
                box-shadow: none;
            }

            .sidebar-overlay {
                display: none;
            }

            .main-content {
                margin-left: 280px;
            }
        }

        .sidebar-header {
            padding: 1.5rem;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            font-size: 1.5rem;
            font-weight: 700;
            color: white;
            text-decoration: none;
        }

        .sidebar-close {
            display: block;
            background: none;
            border: none;
            color: white;
            cursor: pointer;
            padding: 0.5rem;
            border-radius: 8px;
            transition: var(--transition);
        }

        .sidebar-close:hover {
            background: rgba(255,255,255,0.1);
        }

        @media (min-width: 1024px) {
            .sidebar-close {
                display: none;
            }
        }

        .sidebar-nav {
            padding: 1rem 0;
        }

        .nav-item {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.875rem 1.5rem;
            color: rgba(255,255,255,0.8);
            text-decoration: none;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .nav-item::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 3px;
            background: var(--primary);
            transform: translateX(-100%);
            transition: var(--transition);
        }

        .nav-item:hover, .nav-item.active {
            background: rgba(255,255,255,0.1);
            color: white;
        }

        .nav-item.active::before {
            transform: translateX(0);
        }

        /* Mobile Header */
        .mobile-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 1rem;
            background: white;
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        @media (min-width: 1024px) {
            .mobile-header {
                display: none;
            }
        }

        .menu-toggle {
            background: none;
            border: none;
            padding: 0.5rem;
            cursor: pointer;
            border-radius: 8px;
            transition: var(--transition);
        }

        .menu-toggle:hover {
            background: var(--light);
        }

        .mobile-logo {
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--primary);
        }

        .mobile-actions {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        /* Main Content */
        .main-content {
            flex: 1;
            min-height: 100vh;
            background: var(--light);
            transition: var(--transition);
        }

        /* Desktop Header */
        .desktop-header {
            display: none;
            background: white;
            border-bottom: 1px solid var(--border);
            padding: 1rem 2rem;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        @media (min-width: 1024px) {
            .desktop-header {
                display: flex;
                align-items: center;
                justify-content: space-between;
            }
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 1rem;
            flex: 1;
        }

        .search-container {
            position: relative;
            flex: 1;
            max-width: 400px;
        }

        .search-input {
            width: 100%;
            padding: 0.625rem 1rem 0.625rem 2.5rem;
            border: 1px solid var(--border);
            border-radius: 10px;
            font-size: 0.875rem;
            transition: var(--transition);
        }

        .search-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .search-icon {
            position: absolute;
            left: 0.75rem;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-muted);
            width: 18px;
            height: 18px;
        }

        .header-right {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .header-action {
            background: none;
            border: none;
            padding: 0.5rem;
            cursor: pointer;
            border-radius: 8px;
            transition: var(--transition);
            position: relative;
        }

        .header-action:hover {
            background: var(--light);
        }

        .notification-badge {
            position: absolute;
            top: 0.25rem;
            right: 0.25rem;
            width: 8px;
            height: 8px;
            background: var(--danger);
            border-radius: 50%;
            border: 2px solid white;
        }

        /* Page Content */
        .page-content {
            padding: 1.5rem;
        }

        @media (min-width: 1024px) {
            .page-content {
                padding: 2rem;
            }
        }

        /* Mobile Bottom Navigation */
        .mobile-bottom-nav {
            display: flex;
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            border-top: 1px solid var(--border);
            z-index: 100;
        }

        @media (min-width: 1024px) {
            .mobile-bottom-nav {
                display: none;
            }
        }

        .bottom-nav-item {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.25rem;
            padding: 0.75rem 0.5rem;
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            transition: var(--transition);
            position: relative;
        }

        .bottom-nav-item.active {
            color: var(--primary);
        }

        .bottom-nav-item .icon {
            width: 20px;
            height: 20px;
        }

        .bottom-nav-item .label {
            font-size: 0.75rem;
            font-weight: 500;
        }

        /* Cards */
        .card {
            background: white;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            margin-bottom: 1.5rem;
            overflow: hidden;
            transition: var(--transition);
        }

        .card:hover {
            box-shadow: var(--shadow-lg);
            transform: translateY(-2px);
        }

        .card-header {
            padding: 1.25rem 1.5rem;
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .card-title {
            font-size: 1.125rem;
            font-weight: 600;
            color: var(--text);
        }

        .card-body {
            padding: 1.5rem;
        }

        /* Stats Grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .stat-card {
            background: white;
            border-radius: var(--radius);
            padding: 1.5rem;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
        }

        .stat-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-lg);
        }

        .stat-icon {
            width: 48px;
            height: 48px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            margin-bottom: 1rem;
        }

        .stat-value {
            font-size: 2rem;
            font-weight: 700;
            color: var(--text);
            margin-bottom: 0.25rem;
        }

        .stat-label {
            color: var(--text-muted);
            font-size: 0.875rem;
        }

        .stat-change {
            display: inline-flex;
            align-items: center;
            gap: 0.25rem;
            margin-top: 0.5rem;
            padding: 0.25rem 0.5rem;
            border-radius: 6px;
            font-size: 0.75rem;
            font-weight: 500;
        }

        .stat-change.positive {
            background: rgba(16, 185, 129, 0.1);
            color: var(--success);
        }

        .stat-change.negative {
            background: rgba(239, 68, 68, 0.1);
            color: var(--danger);
        }

        /* Tables */
        .table-container {
            background: white;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            overflow: hidden;
        }

        .table-header {
            padding: 1.25rem 1.5rem;
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .table-title {
            font-size: 1.125rem;
            font-weight: 600;
        }

        .table-wrapper {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th {
            text-align: left;
            padding: 1rem 1.5rem;
            background: var(--light);
            font-weight: 600;
            color: var(--text);
            font-size: 0.875rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        td {
            padding: 1rem 1.5rem;
            border-top: 1px solid var(--border);
        }

        tr:hover {
            background: var(--light);
        }

        /* Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.625rem 1.25rem;
            border: none;
            border-radius: 8px;
            font-weight: 500;
            cursor: pointer;
            transition: var(--transition);
            text-decoration: none;
            font-size: 0.875rem;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-primary:hover {
            background: var(--primary-dark);
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
        }

        .btn-secondary {
            background: var(--light);
            color: var(--text);
            border: 1px solid var(--border);
        }

        .btn-secondary:hover {
            background: var(--border);
        }

        .btn-danger {
            background: var(--danger);
            color: white;
        }

        .btn-danger:hover {
            background: #dc2626;
        }

        .btn-sm {
            padding: 0.5rem 1rem;
            font-size: 0.8125rem;
        }

        .btn-icon {
            background: none;
            border: none;
            padding: 0.5rem;
            cursor: pointer;
            border-radius: 8px;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .btn-icon:hover {
            background: var(--light);
        }

        /* Forms */
        .form-group {
            margin-bottom: 1.25rem;
        }

        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--text);
            font-size: 0.875rem;
        }

        .form-control {
            width: 100%;
            padding: 0.625rem 1rem;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 0.875rem;
            transition: var(--transition);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .form-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
        }

        /* Badges */
        .badge {
            display: inline-flex;
            align-items: center;
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .badge-success {
            background: rgba(16, 185, 129, 0.1);
            color: var(--success);
        }

        .badge-warning {
            background: rgba(245, 158, 11, 0.1);
            color: var(--warning);
        }

        .badge-danger {
            background: rgba(239, 68, 68, 0.1);
            color: var(--danger);
        }

        .badge-primary {
            background: rgba(99, 102, 241, 0.1);
            color: var(--primary);
        }

        /* Avatar */
        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 0.875rem;
        }

        .avatar-lg {
            width: 56px;
            height: 56px;
            font-size: 1.125rem;
        }

        /* Dropdown */
        .dropdown {
            position: relative;
        }

        .dropdown-menu {
            position: absolute;
            top: 100%;
            right: 0;
            margin-top: 0.5rem;
            background: white;
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            min-width: 200px;
            opacity: 0;
            visibility: hidden;
            transform: translateY(-10px);
            transition: var(--transition);
            z-index: 1000;
        }

        .dropdown.active .dropdown-menu {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .dropdown-item {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.75rem 1rem;
            color: var(--text);
            text-decoration: none;
            transition: var(--transition);
        }

        .dropdown-item:hover {
            background: var(--light);
        }

        .dropdown-divider {
            height: 1px;
            background: var(--border);
            margin: 0.5rem 0;
        }

        /* Modal */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
            padding: 1rem;
        }

        .modal.active {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background: white;
            border-radius: var(--radius);
            max-width: 500px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            transform: scale(0.9);
            transition: var(--transition);
        }

        .modal.active .modal-content {
            transform: scale(1);
        }

        .modal-header {
            padding: 1.5rem;
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .modal-title {
            font-size: 1.25rem;
            font-weight: 600;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-muted);
            padding: 0.25rem;
            line-height: 1;
        }

        .modal-body {
            padding: 1.5rem;
        }

        .modal-footer {
            padding: 1.5rem;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 1rem;
            justify-content: flex-end;
        }

        /* Toast */
        .toast-container {
            position: fixed;
            top: 1rem;
            right: 1rem;
            z-index: 3000;
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .toast {
            background: white;
            border-radius: var(--radius);
            padding: 1rem 1.25rem;
            box-shadow: var(--shadow-lg);
            display: flex;
            align-items: center;
            gap: 0.75rem;
            min-width: 300px;
            animation: slideIn 0.3s ease-out;
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .toast-icon {
            width: 20px;
            height: 20px;
            flex-shrink: 0;
        }

        .toast-content {
            flex: 1;
        }

        .toast-title {
            font-weight: 600;
            margin-bottom: 0.25rem;
        }

        .toast-message {
            font-size: 0.875rem;
            color: var(--text-muted);
        }

        .toast-close {
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            padding: 0.25rem;
        }

        .toast.success .toast-icon {
            color: var(--success);
        }

        .toast.error .toast-icon {
            color: var(--danger);
        }

        .toast.warning .toast-icon {
            color: var(--warning);
        }

        .toast.info .toast-icon {
            color: var(--info);
        }

        /* Chat */
        .chat-container {
            display: grid;
            grid-template-columns: 300px 1fr;
            height: calc(100vh - 80px);
            background: white;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            overflow: hidden;
        }

        @media (max-width: 768px) {
            .chat-container {
                grid-template-columns: 1fr;
                height: calc(100vh - 140px);
            }
        }

        .chat-sidebar {
            border-right: 1px solid var(--border);
            overflow-y: auto;
        }

        .chat-user-item {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            padding: 1rem;
            cursor: pointer;
            transition: var(--transition);
            border-bottom: 1px solid var(--border);
        }

        .chat-user-item:hover {
            background: var(--light);
        }

        .chat-user-item.active {
            background: rgba(99, 102, 241, 0.1);
        }

        .chat-user-info {
            flex: 1;
        }

        .chat-user-name {
            font-weight: 500;
            margin-bottom: 0.25rem;
        }

        .chat-user-message {
            font-size: 0.875rem;
            color: var(--text-muted);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .chat-user-time {
            font-size: 0.75rem;
            color: var(--text-muted);
        }

        .chat-main {
            display: flex;
            flex-direction: column;
        }

        .chat-messages {
            flex: 1;
            padding: 1rem;
            overflow-y: auto;
            background: var(--light);
        }

        .message {
            display: flex;
            margin-bottom: 1rem;
            animation: fadeIn 0.3s ease-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .message.sent {
            justify-content: flex-end;
        }

        .message-bubble {
            max-width: 70%;
            padding: 0.75rem 1rem;
            border-radius: 18px;
            background: white;
            box-shadow: 0 1px 2px rgba(0,0,0,0.1);
        }

        .message.sent .message-bubble {
            background: var(--primary);
            color: white;
        }

        .message-text {
            margin-bottom: 0.25rem;
            word-wrap: break-word;
        }

        .message-time {
            font-size: 0.75rem;
            opacity: 0.7;
        }

        .chat-input-container {
            padding: 1rem;
            border-top: 1px solid var(--border);
            background: white;
        }

        .chat-input-wrapper {
            display: flex;
            gap: 0.75rem;
            align-items: center;
        }

        .chat-input {
            flex: 1;
            padding: 0.75rem 1rem;
            border: 1px solid var(--border);
            border-radius: 25px;
            font-size: 0.875rem;
            transition: var(--transition);
        }

        .chat-input:focus {
            outline: none;
            border-color: var(--primary);
        }

        .chat-send-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--primary);
            color: white;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }

        .chat-send-btn:hover {
            background: var(--primary-dark);
            transform: scale(1.05);
        }

        /* Work Cards */
        .work-card {
            background: white;
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1rem;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border-left: 4px solid var(--primary);
        }

        .work-card:hover {
            transform: translateX(4px);
            box-shadow: var(--shadow-lg);
        }

        .work-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 1rem;
        }

        .work-title {
            font-size: 1.125rem;
            font-weight: 600;
            color: var(--text);
        }

        .work-status {
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 500;
            text-transform: uppercase;
        }

        .work-status.pending {
            background: rgba(245, 158, 11, 0.1);
            color: var(--warning);
        }

        .work-status.in-progress {
            background: rgba(99, 102, 241, 0.1);
            color: var(--primary);
        }

        .work-status.completed {
            background: rgba(16, 185, 129, 0.1);
            color: var(--success);
        }

        .work-description {
            color: var(--text-muted);
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .work-meta {
            display: flex;
            gap: 1.5rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .work-meta-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-muted);
            font-size: 0.875rem;
        }

        .work-actions {
            display: flex;
            gap: 0.75rem;
            flex-wrap: wrap;
        }

        /* File Upload */
        .file-upload {
            border: 2px dashed var(--border);
            border-radius: var(--radius);
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
            background: var(--light);
        }

        .file-upload:hover {
            border-color: var(--primary);
            background: rgba(99, 102, 241, 0.05);
        }

        .file-upload-icon {
            width: 48px;
            height: 48px;
            margin: 0 auto 1rem;
            color: var(--text-muted);
        }

        .file-upload-text {
            font-weight: 500;
            margin-bottom: 0.5rem;
        }

        .file-upload-hint {
            font-size: 0.875rem;
            color: var(--text-muted);
        }

        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 3rem 1rem;
        }

        .empty-state-icon {
            width: 64px;
            height: 64px;
            margin: 0 auto 1rem;
            color: var(--text-muted);
        }

        .empty-state-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .empty-state-text {
            color: var(--text-muted);
        }

        /* Loading Spinner */
        .spinner {
            width: 40px;
            height: 40px;
            border: 3px solid var(--border);
            border-top-color: var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 2rem auto;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

        /* Progress Bar */
        .progress-bar {
            width: 100%;
            height: 8px;
            background: var(--border);
            border-radius: 9999px;
            overflow: hidden;
            margin: 0.5rem 0;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            border-radius: 9999px;
            transition: width 0.5s ease-out;
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid var(--border);
            overflow-x: auto;
        }

        .tab {
            padding: 0.75rem 1.25rem;
            background: none;
            border: none;
            color: var(--text-muted);
            font-weight: 500;
            cursor: pointer;
            position: relative;
            transition: var(--transition);
            white-space: nowrap;
        }

        .tab:hover {
            color: var(--text);
        }

        .tab.active {
            color: var(--primary);
        }

        .tab.active::after {
            content: '';
            position: absolute;
            bottom: -1px;
            left: 0;
            right: 0;
            height: 2px;
            background: var(--primary);
        }

        /* Floating Action Button */
        .fab {
            position: fixed;
            bottom: 5rem;
            right: 1.5rem;
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            cursor: pointer;
            box-shadow: var(--shadow-lg);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
            z-index: 90;
        }

        .fab:hover {
            transform: scale(1.1);
            box-shadow: 0 8px 25px rgba(99, 102, 241, 0.4);
        }

        @media (min-width: 1024px) {
            .fab {
                bottom: 2rem;
                right: 2rem;
            }
        }

        /* Dark Mode Toggle */
        .theme-toggle {
            position: relative;
            width: 48px;
            height: 24px;
            background: var(--border);
            border-radius: 9999px;
            cursor: pointer;
            transition: var(--transition);
        }

        .theme-toggle::after {
            content: '';
            position: absolute;
            top: 2px;
            left: 2px;
            width: 20px;
            height: 20px;
            background: white;
            border-radius: 50%;
            transition: var(--transition);
        }

        [data-theme="dark"] .theme-toggle {
            background: var(--primary);
        }

        [data-theme="dark"] .theme-toggle::after {
            transform: translateX(24px);
        }

        /* Pull to Refresh */
        .pull-to-refresh {
            position: fixed;
            top: -60px;
            left: 0;
            right: 0;
            height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: white;
            box-shadow: var(--shadow);
            transition: var(--transition);
            z-index: 99;
        }

        .pull-to-refresh.active {
            top: 0;
        }

        /* Responsive Utilities */
        .hide-mobile {
            display: none;
        }

        @media (min-width: 1024px) {
            .hide-mobile {
                display: block;
            }
        }

        .hide-desktop {
            display: block;
        }

        @media (min-width: 1024px) {
            .hide-desktop {
                display: none;
            }
        }

        /* Animations */
        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.5;
            }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        .bounce {
            animation: bounce 1s infinite;
        }

        /* Touch Optimizations */
        @media (hover: none) {
            .nav-item:active,
            .btn:active,
            .card:active {
                transform: scale(0.98);
            }
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--light);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--border);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--text-muted);
        }
    </style>
</head>

<body>
    <div id="app" class="app-container">
        <!-- Mobile Header -->
        <header class="mobile-header">
            <button class="menu-toggle" onclick="app.toggleSidebar()">
                <i data-lucide="menu" class="icon"></i>
            </button>
            <div class="mobile-logo">Typixel</div>
            <div class="mobile-actions">
                <button class="header-action" onclick="app.openNotifications()">
                    <i data-lucide="bell" class="icon"></i>
                    <span class="notification-badge"></span>
                </button>
                <div class="dropdown">
                    <button class="header-action" onclick="app.toggleDropdown(this)">
                        <i data-lucide="user" class="icon"></i>
                    </button>
                    <div class="dropdown-menu">
                        <a href="#" class="dropdown-item" onclick="app.navigate('profile')">
                            <i data-lucide="user" class="icon"></i>
                            Profile
                        </a>
                        <a href="#" class="dropdown-item" onclick="app.navigate('settings')">
                            <i data-lucide="settings" class="icon"></i>
                            Settings
                        </a>
                        <div class="dropdown-divider"></div>
                        <a href="#" class="dropdown-item" onclick="app.logout()">
                            <i data-lucide="log-out" class="icon"></i>
                            Logout
                        </a>
                    </div>
                </div>
            </div>
        </header>

        <!-- Sidebar -->
        <aside class="sidebar" id="sidebar">
            <div class="sidebar-header">
                <a href="#" class="logo">
                    <i data-lucide="palette" class="icon"></i>
                    Typixel
                </a>
                <button class="sidebar-close" onclick="app.toggleSidebar()">
                    <i data-lucide="x" class="icon"></i>
                </button>
            </div>
            <nav class="sidebar-nav">
                <a href="#" class="nav-item active" onclick="app.navigate('dashboard')">
                    <i data-lucide="home" class="icon"></i>
                    Dashboard
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('projects')">
                    <i data-lucide="briefcase" class="icon"></i>
                    Projects
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('clients')">
                    <i data-lucide="users" class="icon"></i>
                    Clients
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('editors')">
                    <i data-lucide="user-check" class="icon"></i>
                    Editors
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('invoices')">
                    <i data-lucide="file-text" class="icon"></i>
                    Invoices
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('chat')">
                    <i data-lucide="message-circle" class="icon"></i>
                    Chat
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('support')">
                    <i data-lucide="help-circle" class="icon"></i>
                    Support
                </a>
                <a href="#" class="nav-item" onclick="app.navigate('analytics')">
                    <i data-lucide="bar-chart-2" class="icon"></i>
                    Analytics
                </a>
            </nav>
        </aside>

        <!-- Sidebar Overlay -->
        <div class="sidebar-overlay" id="sidebar-overlay" onclick="app.toggleSidebar()"></div>

        <!-- Main Content -->
        <main class="main-content">
            <!-- Desktop Header -->
            <header class="desktop-header">
                <div class="header-left">
                    <div class="search-container">
                        <i data-lucide="search" class="search-icon"></i>
                        <input type="text" class="search-input" placeholder="Search projects, clients, or editors..." onkeyup="app.handleSearch(event)">
                    </div>
                </div>
                <div class="header-right">
                    <button class="header-action" onclick="app.toggleTheme()">
                        <i data-lucide="moon" class="icon"></i>
                    </button>
                    <button class="header-action" onclick="app.openNotifications()">
                        <i data-lucide="bell" class="icon"></i>
                        <span class="notification-badge"></span>
                    </button>
                    <div class="dropdown">
                        <button class="header-action" onclick="app.toggleDropdown(this)">
                            <i data-lucide="user" class="icon"></i>
                        </button>
                        <div class="dropdown-menu">
                            <a href="#" class="dropdown-item" onclick="app.navigate('profile')">
                                <i data-lucide="user" class="icon"></i>
                                Profile
                            </a>
                            <a href="#" class="dropdown-item" onclick="app.navigate('settings')">
                                <i data-lucide="settings" class="icon"></i>
                                Settings
                            </a>
                            <div class="dropdown-divider"></div>
                            <a href="#" class="dropdown-item" onclick="app.logout()">
                                <i data-lucide="log-out" class="icon"></i>
                                Logout
                            </a>
                        </div>
                    </div>
                </div>
            </header>

            <!-- Page Content -->
            <div class="page-content" id="page-content">
                <!-- Content will be dynamically loaded here -->
            </div>

            <!-- Mobile Bottom Navigation -->
            <nav class="mobile-bottom-nav">
                <button class="bottom-nav-item active" onclick="app.navigate('dashboard')">
                    <i data-lucide="home" class="icon"></i>
                    <span class="label">Home</span>
                </button>
                <button class="bottom-nav-item" onclick="app.navigate('projects')">
                    <i data-lucide="briefcase" class="icon"></i>
                    <span class="label">Projects</span>
                </button>
                <button class="bottom-nav-item" onclick="app.navigate('chat')">
                    <i data-lucide="message-circle" class="icon"></i>
                    <span class="label">Chat</span>
                </button>
                <button class="bottom-nav-item" onclick="app.navigate('notifications')">
                    <i data-lucide="bell" class="icon"></i>
                    <span class="label">Alerts</span>
                </button>
                <button class="bottom-nav-item" onclick="app.navigate('profile')">
                    <i data-lucide="user" class="icon"></i>
                    <span class="label">Profile</span>
                </button>
            </nav>

            <!-- Floating Action Button -->
            <button class="fab" onclick="app.showQuickActions()">
                <i data-lucide="plus" class="icon"></i>
            </button>
        </main>
    </div>

    <!-- Toast Container -->
    <div class="toast-container" id="toast-container"></div>

    <!-- Pull to Refresh -->
    <div class="pull-to-refresh" id="pull-to-refresh">
        <i data-lucide="refresh-cw" class="icon pulse"></i>
    </div>

    <script>
        // App State and Logic
        const app = {
            currentUser: null,
            currentPage: 'dashboard',
            data: {
                users: [
                    { id: 1, name: 'Admin', email: 'rifadwork@gmail.com', password: '123', role: 'admin', approved: true, avatar: 'AD' },
                    { id: 2, name: 'John Doe', email: 'john@example.com', password: '123', role: 'editor', approved: true, avatar: 'JD', totalWorkTime: 120, pendingSalary: 15000 },
                    { id: 3, name: 'Jane Smith', email: 'jane@example.com', password: '123', role: 'editor', approved: true, avatar: 'JS', totalWorkTime: 80, pendingSalary: 10000 },
                    { id: 4, name: 'Mike Johnson', email: 'mike@example.com', password: '123', role: 'editor', approved: false, avatar: 'MJ' }
                ],
                clients: [
                    { id: 1, name: 'Acme Corp', email: 'contact@acme.com', phone: '+1234567890', address: '123 Main St, City', avatar: 'AC' },
                    { id: 2, name: 'TechStart', email: 'hello@techstart.com', phone: '+0987654321', address: '456 Oak Ave, Town', avatar: 'TS' }
                ],
                projects: [
                    { id: 1, name: 'Brand Redesign', description: 'Complete brand identity redesign', clientId: 1, budget: 50000, assignedEditorId: 2, deadline: '2024-02-15', status: 'in-progress', progress: 65 },
                    { id: 2, name: 'Website UI', description: 'Modern website user interface', clientId: 2, budget: 30000, assignedEditorId: 3, deadline: '2024-02-20', status: 'in-progress', progress: 40 },
                    { id: 3, name: 'Marketing Materials', description: 'Brochure and flyer designs', clientId: 1, budget: 25000, assignedEditorId: null, deadline: '2024-03-01', status: 'pending', progress: 0 }
                ],
                workAssignments: [
                    { id: 1, projectId: 1, editorId: 2, description: 'Create logo variations', deadline: '2024-02-10', status: 'in-progress', createdAt: '2024-01-20' },
                    { id: 2, projectId: 2, editorId: 3, description: 'Design homepage mockup', deadline: '2024-02-15', status: 'pending', createdAt: '2024-01-22' }
                ],
                invoices: [
                    { id: 1, projectId: 1, editorId: 2, amount: 15000, date: '2024-01-15', status: 'paid' },
                    { id: 2, projectId: 2, editorId: 3, amount: 10000, date: '2024-01-20', status: 'pending' }
                ],
                messages: [
                    { id: 1, senderId: 1, receiverId: 2, text: 'Please check the latest designs', timestamp: '2024-01-25T10:00:00' },
                    { id: 2, senderId: 2, receiverId: 1, text: 'Sure, I\'ll review them now', timestamp: '2024-01-25T10:05:00' }
                ],
                notifications: [
                    { id: 1, userId: 2, title: 'New Work Assignment', message: 'You have been assigned to Brand Redesign', read: false, timestamp: '2024-01-25T09:00:00' },
                    { id: 2, userId: 1, title: 'Project Update', message: 'Brand Redesign is 65% complete', read: false, timestamp: '2024-01-25T08:30:00' }
                ],
                tickets: []
            },

            init: function () {
                // Check login
                const savedUser = localStorage.getItem('currentUser');
                if (savedUser) {
                    this.currentUser = JSON.parse(savedUser);
                } else {
                    this.showLogin();
                    return;
                }

                // Load data
                this.loadData();
                
                // Render initial page
                this.renderApp();
                
                // Setup event listeners
                this.setupEventListeners();
                
                // Initialize icons
                lucide.createIcons();
                
                // Setup pull to refresh
                this.setupPullToRefresh();
                
                // Check for theme preference
                const savedTheme = localStorage.getItem('theme') || 'light';
                document.documentElement.setAttribute('data-theme', savedTheme);
            },

            showLogin: function () {
                document.getElementById('app').innerHTML = `
                    <div style="min-height: 100vh; display: flex; align-items: center; justify-content: center; background: linear-gradient(135deg, var(--primary), var(--secondary)); padding: 1rem;">
                        <div style="background: white; border-radius: var(--radius); padding: 2rem; width: 100%; max-width: 400px; box-shadow: var(--shadow-lg);">
                            <div style="text-align: center; margin-bottom: 2rem;">
                                <div style="width: 64px; height: 64px; background: linear-gradient(135deg, var(--primary), var(--secondary)); border-radius: 16px; display: flex; align-items: center; justify-content: center; margin: 0 auto 1rem;">
                                    <i data-lucide="palette" style="color: white; width: 32px; height: 32px;"></i>
                                </div>
                                <h1 style="font-size: 1.875rem; font-weight: 700; color: var(--text); margin-bottom: 0.5rem;">Welcome to Typixel</h1>
                                <p style="color: var(--text-muted);">Graphic Design Management System</p>
                            </div>
                            <form onsubmit="app.login(event)">
                                <div class="form-group">
                                    <label class="form-label">Email</label>
                                    <input type="email" class="form-control" id="login-email" required placeholder="Enter your email">
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Password</label>
                                    <input type="password" class="form-control" id="login-password" required placeholder="Enter your password">
                                </div>
                                <button type="submit" class="btn btn-primary" style="width: 100%; margin-bottom: 1rem;">
                                    Sign In
                                </button>
                                <button type="button" class="btn btn-secondary" style="width: 100%;" onclick="app.showJoinTeam()">
                                    Join Our Team
                                </button>
                            </form>
                        </div>
                    </div>
                `;
                lucide.createIcons();
            },

            login: function (event) {
                event.preventDefault();
                const email = document.getElementById('login-email').value;
                const password = document.getElementById('login-password').value;
                
                const user = this.data.users.find(u => u.email === email && u.password === password);
                
                if (user && user.approved) {
                    this.currentUser = user;
                    localStorage.setItem('currentUser', JSON.stringify(user));
                    this.init();
                } else if (user && !user.approved) {
                    this.showToast('warning', 'Account Pending', 'Your account is awaiting approval');
                } else {
                    this.showToast('error', 'Login Failed', 'Invalid email or password');
                }
            },

            logout: function () {
                localStorage.removeItem('currentUser');
                this.currentUser = null;
                this.showLogin();
            },

            showJoinTeam: function () {
                document.getElementById('app').innerHTML = `
                    <div style="min-height: 100vh; display: flex; align-items: center; justify-content: center; background: linear-gradient(135deg, var(--primary), var(--secondary)); padding: 1rem;">
                        <div style="background: white; border-radius: var(--radius); padding: 2rem; width: 100%; max-width: 500px; box-shadow: var(--shadow-lg); max-height: 90vh; overflow-y: auto;">
                            <div style="text-align: center; margin-bottom: 2rem;">
                                <button onclick="app.showLogin()" style="position: absolute; top: 1rem; left: 1rem; background: none; border: none; padding: 0.5rem;">
                                    <i data-lucide="arrow-left" class="icon"></i>
                                </button>
                                <h2 style="font-size: 1.5rem; font-weight: 700; color: var(--text);">Join Our Team</h2>
                                <p style="color: var(--text-muted);">Apply to become a graphic designer</p>
                            </div>
                            <form onsubmit="app.joinTeam(event)">
                                <div class="form-row">
                                    <div class="form-group">
                                        <label class="form-label">Full Name</label>
                                        <input type="text" name="name" class="form-control" required>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Email</label>
                                        <input type="email" name="email" class="form-control" required>
                                    </div>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Password</label>
                                    <input type="password" name="password" class="form-control" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Phone</label>
                                    <input type="tel" name="phone" class="form-control" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Portfolio Link</label>
                                    <input type="url" name="portfolio" class="form-control" placeholder="https://...">
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Tell us about yourself</label>
                                    <textarea name="bio" class="form-control" rows="3" placeholder="Your experience and skills..."></textarea>
                                </div>
                                <button type="submit" class="btn btn-primary" style="width: 100%;">
                                    Submit Application
                                </button>
                            </form>
                        </div>
                    </div>
                `;
                lucide.createIcons();
            },

            joinTeam: function (event) {
                event.preventDefault();
                const formData = new FormData(event.target);
                
                const editor = {
                    id: Date.now(),
                    name: formData.get('name'),
                    email: formData.get('email'),
                    password: formData.get('password'),
                    phone: formData.get('phone'),
                    role: 'editor',
                    approved: false,
                    avatar: formData.get('name').split(' ').map(n => n[0]).join('').toUpperCase(),
                    totalWorkTime: 0,
                    pendingSalary: 0,
                    portfolio: formData.get('portfolio'),
                    bio: formData.get('bio')
                };

                this.data.users.push(editor);
                this.saveData();
                
                // Notify admin
                this.addNotification(1, 'New Application', `${editor.name} has applied to join the team`);
                
                this.showToast('success', 'Application Submitted', 'Your application has been submitted. We will review it soon.');
                this.showLogin();
            },

            loadData: function () {
                const savedData = localStorage.getItem('appData');
                if (savedData) {
                    this.data = JSON.parse(savedData);
                }
            },

            saveData: function () {
                localStorage.setItem('appData', JSON.stringify(this.data));
            },

            renderApp: function () {
                const pageContent = document.getElementById('page-content');
                if (pageContent) {
                    pageContent.innerHTML = this.renderPage();
                    lucide.createIcons();
                    this.setupDropdowns();
                }
                this.updateNotificationBadge();
            },

            renderPage: function () {
                switch (this.currentPage) {
                    case 'dashboard':
                        return this.renderDashboard();
                    case 'projects':
                        return this.renderProjects();
                    case 'clients':
                        return this.renderClients();
                    case 'editors':
                        return this.renderEditors();
                    case 'invoices':
                        return this.renderInvoices();
                    case 'chat':
                        return this.renderChat();
                    case 'support':
                        return this.renderSupport();
                    case 'analytics':
                        return this.renderAnalytics();
                    case 'profile':
                        return this.renderProfile();
                    case 'settings':
                        return this.renderSettings();
                    case 'notifications':
                        return this.renderNotifications();
                    default:
                        return this.renderDashboard();
                }
            },

            renderDashboard: function () {
                const stats = this.getDashboardStats();
                const recentWork = this.data.workAssignments.slice(0, 3);
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Dashboard</h1>
                        <p class="page-subtitle" style="color: var(--text-muted);">Welcome back, ${this.currentUser.name}!</p>
                    </div>

                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="rupee" class="icon"></i>
                            </div>
                            <div class="stat-value">₹${stats.totalRevenue.toLocaleString('en-IN')}</div>
                            <div class="stat-label">Total Revenue</div>
                            <div class="stat-change positive">
                                <i data-lucide="trending-up" class="icon" style="width: 16px; height: 16px;"></i>
                                +12% from last month
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="briefcase" class="icon"></i>
                            </div>
                            <div class="stat-value">${stats.activeProjects}</div>
                            <div class="stat-label">Active Projects</div>
                            <div class="stat-change positive">
                                <i data-lucide="trending-up" class="icon" style="width: 16px; height: 16px;"></i>
                                +3 this week
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="users" class="icon"></i>
                            </div>
                            <div class="stat-value">${stats.totalClients}</div>
                            <div class="stat-label">Total Clients</div>
                            <div class="stat-change positive">
                                <i data-lucide="trending-up" class="icon" style="width: 16px; height: 16px;"></i>
                                +2 new clients
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="user-check" class="icon"></i>
                            </div>
                            <div class="stat-value">${stats.activeEditors}</div>
                            <div class="stat-label">Active Editors</div>
                            <div class="stat-change negative">
                                <i data-lucide="trending-down" class="icon" style="width: 16px; height: 16px;"></i>
                                -1 on leave
                            </div>
                        </div>
                    </div>

                    <div style="display: grid; grid-template-columns: 1fr; gap: 1.5rem; margin-bottom: 2rem;">
                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Recent Work Assignments</h3>
                                <button class="btn btn-sm btn-primary" onclick="app.navigate('projects')">View All</button>
                            </div>
                            <div class="card-body">
                                ${recentWork.length > 0 ? recentWork.map(work => {
                                    const project = this.data.projects.find(p => p.id === work.projectId);
                                    const editor = this.data.users.find(u => u.id === work.editorId);
                                    return `
                                        <div style="padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                            <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 0.5rem;">
                                                <div>
                                                    <div style="font-weight: 600; color: var(--text);">${project ? project.name : 'Unknown'}</div>
                                                    <div style="font-size: 0.875rem; color: var(--text-muted);">
                                                        Assigned to: ${editor ? editor.name : 'Unassigned'}
                                                    </div>
                                                </div>
                                                <span class="badge badge-${work.status === 'completed' ? 'success' : work.status === 'in-progress' ? 'primary' : 'warning'}">
                                                    ${work.status}
                                                </span>
                                            </div>
                                            <div class="progress-bar">
                                                <div class="progress-fill" style="width: ${project ? project.progress : 0}%"></div>
                                            </div>
                                        </div>
                                    `;
                                }).join('') : '<p style="text-align: center; color: var(--text-muted);">No recent work assignments</p>'}
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Quick Actions</h3>
                            </div>
                            <div class="card-body">
                                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 1rem;">
                                    <button class="btn btn-primary" style="height: auto; padding: 1.5rem 1rem; flex-direction: column;" onclick="app.openModal('add-project')">
                                        <i data-lucide="plus" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        New Project
                                    </button>
                                    <button class="btn btn-secondary" style="height: auto; padding: 1.5rem 1rem; flex-direction: column;" onclick="app.openModal('add-client')">
                                        <i data-lucide="user-plus" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        Add Client
                                    </button>
                                    <button class="btn btn-secondary" style="height: auto; padding: 1.5rem 1rem; flex-direction: column;" onclick="app.navigate('invoices')">
                                        <i data-lucide="file-text" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        Invoices
                                    </button>
                                    <button class="btn btn-secondary" style="height: auto; padding: 1.5rem 1rem; flex-direction: column;" onclick="app.navigate('analytics')">
                                        <i data-lucide="bar-chart-2" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        Analytics
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            },

            renderProjects: function () {
                const projects = this.data.projects;
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Projects</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Manage all your design projects</p>
                        </div>
                        <button class="btn btn-primary" onclick="app.openModal('add-project')">
                            <i data-lucide="plus" class="icon"></i>
                            New Project
                        </button>
                    </div>

                    <div class="tabs">
                        <button class="tab active" onclick="app.switchTab(this, 'all')">All Projects</button>
                        <button class="tab" onclick="app.switchTab(this, 'pending')">Pending</button>
                        <button class="tab" onclick="app.switchTab(this, 'in-progress')">In Progress</button>
                        <button class="tab" onclick="app.switchTab(this, 'completed')">Completed</button>
                    </div>

                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">All Projects</h3>
                            <div class="dropdown">
                                <button class="btn btn-sm btn-secondary" onclick="app.toggleDropdown(this)">
                                    <i data-lucide="filter" class="icon"></i>
                                    Filter
                                </button>
                                <div class="dropdown-menu">
                                    <a href="#" class="dropdown-item">Last 7 days</a>
                                    <a href="#" class="dropdown-item">Last 30 days</a>
                                    <a href="#" class="dropdown-item">Last 3 months</a>
                                </div>
                            </div>
                        </div>
                        <div class="table-wrapper">
                            <table>
                                <thead>
                                    <tr>
                                        <th>Project Name</th>
                                        <th>Client</th>
                                        <th>Editor</th>
                                        <th>Budget</th>
                                        <th>Progress</th>
                                        <th>Deadline</th>
                                        <th>Status</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${projects.map(project => {
                                        const client = this.data.clients.find(c => c.id === project.clientId);
                                        const editor = this.data.users.find(u => u.id === project.assignedEditorId);
                                        return `
                                            <tr>
                                                <td>
                                                    <div style="font-weight: 600;">${project.name}</div>
                                                    <div style="font-size: 0.875rem; color: var(--text-muted);">${project.description}</div>
                                                </td>
                                                <td>
                                                    <div style="display: flex; align-items: center; gap: 0.5rem;">
                                                        <div class="avatar" style="width: 32px; height: 32px; font-size: 0.75rem;">${client ? client.avatar : 'NA'}</div>
                                                        <div>${client ? client.name : 'No Client'}</div>
                                                    </div>
                                                </td>
                                                <td>
                                                    ${editor ? `
                                                        <div style="display: flex; align-items: center; gap: 0.5rem;">
                                                            <div class="avatar" style="width: 32px; height: 32px; font-size: 0.75rem;">${editor.avatar}</div>
                                                            <div>${editor.name}</div>
                                                        </div>
                                                    ` : '<span style="color: var(--text-muted);">Unassigned</span>'}
                                                </td>
                                                <td>₹${project.budget.toLocaleString('en-IN')}</td>
                                                <td>
                                                    <div class="progress-bar" style="width: 100px;">
                                                        <div class="progress-fill" style="width: ${project.progress}%"></div>
                                                    </div>
                                                    <div style="font-size: 0.75rem; color: var(--text-muted);">${project.progress}%</div>
                                                </td>
                                                <td>${project.deadline}</td>
                                                <td>
                                                    <span class="badge badge-${project.status === 'completed' ? 'success' : project.status === 'in-progress' ? 'primary' : 'warning'}">
                                                        ${project.status}
                                                    </span>
                                                </td>
                                                <td>
                                                    <div style="display: flex; gap: 0.5rem;">
                                                        <button class="btn-icon" onclick="app.editProject(${project.id})">
                                                            <i data-lucide="edit-2" class="icon" style="width: 16px; height: 16px;"></i>
                                                        </button>
                                                        <button class="btn-icon" onclick="app.deleteProject(${project.id})">
                                                            <i data-lucide="trash-2" class="icon" style="width: 16px; height: 16px;"></i>
                                                        </button>
                                                    </div>
                                                </td>
                                            </tr>
                                        `;
                                    }).join('')}
                                </tbody>
                            </table>
                        </div>
                    </div>
                `;
            },

            renderClients: function () {
                const clients = this.data.clients;
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Clients</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Manage your client relationships</p>
                        </div>
                        <button class="btn btn-primary" onclick="app.openModal('add-client')">
                            <i data-lucide="plus" class="icon"></i>
                            Add Client
                        </button>
                    </div>

                    <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1.5rem;">
                        ${clients.map(client => {
                            const clientProjects = this.data.projects.filter(p => p.clientId === client.id);
                            const totalSpent = clientProjects.reduce((sum, p) => sum + p.budget, 0);
                            return `
                                <div class="card">
                                    <div class="card-body">
                                        <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1.5rem;">
                                            <div class="avatar avatar-lg">${client.avatar}</div>
                                            <div>
                                                <h3 style="font-size: 1.125rem; font-weight: 600; margin-bottom: 0.25rem;">${client.name}</h3>
                                                <p style="color: var(--text-muted); font-size: 0.875rem;">${client.email}</p>
                                            </div>
                                        </div>
                                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-bottom: 1.5rem;">
                                            <div>
                                                <div style="font-size: 0.75rem; color: var(--text-muted); margin-bottom: 0.25rem;">Phone</div>
                                                <div style="font-weight: 500;">${client.phone}</div>
                                            </div>
                                            <div>
                                                <div style="font-size: 0.75rem; color: var(--text-muted); margin-bottom: 0.25rem;">Total Projects</div>
                                                <div style="font-weight: 500;">${clientProjects.length}</div>
                                            </div>
                                        </div>
                                        <div style="margin-bottom: 1.5rem;">
                                            <div style="font-size: 0.75rem; color: var(--text-muted); margin-bottom: 0.25rem;">Total Spent</div>
                                            <div style="font-size: 1.25rem; font-weight: 700; color: var(--primary);">₹${totalSpent.toLocaleString('en-IN')}</div>
                                        </div>
                                        <div style="display: flex; gap: 0.75rem;">
                                            <button class="btn btn-sm btn-primary" style="flex: 1;" onclick="app.viewClientProjects(${client.id})">
                                                View Projects
                                            </button>
                                            <button class="btn btn-sm btn-secondary" onclick="app.editClient(${client.id})">
                                                <i data-lucide="edit-2" class="icon" style="width: 16px; height: 16px;"></i>
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            `;
                        }).join('')}
                    </div>
                `;
            },

            renderEditors: function () {
                const editors = this.data.users.filter(u => u.role === 'editor');
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Editors</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Manage your design team</p>
                        </div>
                        <button class="btn btn-primary" onclick="app.openModal('add-editor')">
                            <i data-lucide="plus" class="icon"></i>
                            Add Editor
                        </button>
                    </div>

                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">All Editors</h3>
                        </div>
                        <div class="table-wrapper">
                            <table>
                                <thead>
                                    <tr>
                                        <th>Editor</th>
                                        <th>Email</th>
                                        <th>Status</th>
                                        <th>Work Time</th>
                                        <th>Pending Salary</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${editors.map(editor => {
                                        const editorWork = this.data.workAssignments.filter(w => w.editorId === editor.id);
                                        return `
                                            <tr>
                                                <td>
                                                    <div style="display: flex; align-items: center; gap: 0.75rem;">
                                                        <div class="avatar">${editor.avatar}</div>
                                                        <div>
                                                            <div style="font-weight: 600;">${editor.name}</div>
                                                            <div style="font-size: 0.875rem; color: var(--text-muted);">${editorWork.length} projects</div>
                                                        </div>
                                                    </div>
                                                </td>
                                                <td>${editor.email}</td>
                                                <td>
                                                    <span class="badge badge-${editor.approved ? 'success' : 'warning'}">
                                                        ${editor.approved ? 'Approved' : 'Pending'}
                                                    </span>
                                                </td>
                                                <td>${editor.totalWorkTime || 0} hours</td>
                                                <td>₹${(editor.pendingSalary || 0).toLocaleString('en-IN')}</td>
                                                <td>
                                                    <div style="display: flex; gap: 0.5rem;">
                                                        ${!editor.approved ? `
                                                            <button class="btn btn-sm btn-success" onclick="app.approveEditor(${editor.id})">
                                                                Approve
                                                            </button>
                                                        ` : `
                                                            <button class="btn btn-sm btn-primary" onclick="app.updateEditorSalary(${editor.id})">
                                                                Update Salary
                                                            </button>
                                                        `}
                                                        <button class="btn-icon" onclick="app.deleteEditor(${editor.id})">
                                                            <i data-lucide="trash-2" class="icon" style="width: 16px; height: 16px;"></i>
                                                        </button>
                                                    </div>
                                                </td>
                                            </tr>
                                        `;
                                    }).join('')}
                                </tbody>
                            </table>
                        </div>
                    </div>
                `;
            },

            renderInvoices: function () {
                const invoices = this.data.invoices;
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Invoices</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Manage payments and billing</p>
                        </div>
                        <button class="btn btn-primary" onclick="app.generateInvoice()">
                            <i data-lucide="file-plus" class="icon"></i>
                            Generate Invoice
                        </button>
                    </div>

                    <div class="stats-grid" style="margin-bottom: 2rem;">
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="rupee" class="icon"></i>
                            </div>
                            <div class="stat-value">₹${invoices.filter(i => i.status === 'paid').reduce((sum, i) => sum + i.amount, 0).toLocaleString('en-IN')}</div>
                            <div class="stat-label">Total Paid</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="clock" class="icon"></i>
                            </div>
                            <div class="stat-value">₹${invoices.filter(i => i.status === 'pending').reduce((sum, i) => sum + i.amount, 0).toLocaleString('en-IN')}</div>
                            <div class="stat-label">Pending</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="file-text" class="icon"></i>
                            </div>
                            <div class="stat-value">${invoices.length}</div>
                            <div class="stat-label">Total Invoices</div>
                        </div>
                    </div>

                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">All Invoices</h3>
                        </div>
                        <div class="table-wrapper">
                            <table>
                                <thead>
                                    <tr>
                                        <th>Invoice #</th>
                                        <th>Project</th>
                                        <th>Editor</th>
                                        <th>Amount</th>
                                        <th>Date</th>
                                        <th>Status</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${invoices.map(invoice => {
                                        const project = this.data.projects.find(p => p.id === invoice.projectId);
                                        const editor = this.data.users.find(u => u.id === invoice.editorId);
                                        return `
                                            <tr>
                                                <td>#${invoice.id.toString().padStart(5, '0')}</td>
                                                <td>${project ? project.name : 'Unknown'}</td>
                                                <td>
                                                    <div style="display: flex; align-items: center; gap: 0.5rem;">
                                                        <div class="avatar" style="width: 32px; height: 32px; font-size: 0.75rem;">${editor ? editor.avatar : 'NA'}</div>
                                                        <div>${editor ? editor.name : 'Unknown'}</div>
                                                    </div>
                                                </td>
                                                <td style="font-weight: 600;">₹${invoice.amount.toLocaleString('en-IN')}</td>
                                                <td>${new Date(invoice.date).toLocaleDateString()}</td>
                                                <td>
                                                    <span class="badge badge-${invoice.status === 'paid' ? 'success' : 'warning'}">
                                                        ${invoice.status}
                                                    </span>
                                                </td>
                                                <td>
                                                    ${invoice.status === 'pending' ? `
                                                        <button class="btn btn-sm btn-success" onclick="app.markInvoicePaid(${invoice.id})">
                                                            Mark Paid
                                                        </button>
                                                    ` : `
                                                        <button class="btn btn-sm btn-secondary" onclick="app.downloadInvoice(${invoice.id})">
                                                            Download
                                                        </button>
                                                    `}
                                                </td>
                                            </tr>
                                        `;
                                    }).join('')}
                                </tbody>
                            </table>
                        </div>
                    </div>
                `;
            },

            renderChat: function () {
                const users = this.data.users.filter(u => u.id !== this.currentUser.id);
                
                return `
                    <div class="chat-container">
                        <div class="chat-sidebar">
                            <div style="padding: 1rem; border-bottom: 1px solid var(--border);">
                                <h3 style="font-size: 1.125rem; font-weight: 600;">Messages</h3>
                            </div>
                            ${users.map(user => {
                                const lastMessage = this.getLastMessage(this.currentUser.id, user.id);
                                return `
                                    <div class="chat-user-item" onclick="app.openChatWith(${user.id})">
                                        <div class="avatar">${user.avatar}</div>
                                        <div class="chat-user-info">
                                            <div class="chat-user-name">${user.name}</div>
                                            <div class="chat-user-message">${lastMessage ? lastMessage.text : 'No messages yet'}</div>
                                        </div>
                                        <div class="chat-user-time">${lastMessage ? this.formatTime(lastMessage.timestamp) : ''}</div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                        <div class="chat-main" id="chat-main">
                            <div class="empty-state">
                                <i data-lucide="message-circle" class="empty-state-icon"></i>
                                <h3 class="empty-state-title">Select a conversation</h3>
                                <p class="empty-state-text">Choose a user from the list to start chatting</p>
                            </div>
                        </div>
                    </div>
                `;
            },

            renderSupport: function () {
                const tickets = this.data.tickets.filter(t => 
                    this.currentUser.role === 'admin' || t.editorId === this.currentUser.id
                );
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Support</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Manage support tickets</p>
                        </div>
                    </div>

                    ${this.currentUser.role === 'editor' ? `
                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Create Support Ticket</h3>
                            </div>
                            <div class="card-body">
                                <form onsubmit="app.createTicket(event)">
                                    <div class="form-group">
                                        <label class="form-label">Subject</label>
                                        <input type="text" name="subject" class="form-control" placeholder="Brief description of your issue" required>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Priority</label>
                                        <select name="priority" class="form-control" required>
                                            <option value="low">Low</option>
                                            <option value="medium">Medium</option>
                                            <option value="high">High</option>
                                        </select>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Description</label>
                                        <textarea name="description" class="form-control" rows="5" placeholder="Describe your issue in detail..." required></textarea>
                                    </div>
                                    <button type="submit" class="btn btn-primary">
                                        <i data-lucide="send" class="icon"></i>
                                        Submit Ticket
                                    </button>
                                </form>
                            </div>
                        </div>
                    ` : ''}

                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Support Tickets</h3>
                        </div>
                        <div class="card-body">
                            ${tickets.length > 0 ? `
                                <div class="table-wrapper">
                                    <table>
                                        <thead>
                                            <tr>
                                                <th>Ticket ID</th>
                                                <th>Subject</th>
                                                <th>Priority</th>
                                                <th>Status</th>
                                                <th>Created</th>
                                                <th>Actions</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            ${tickets.map(ticket => {
                                                const editor = this.data.users.find(u => u.id === ticket.editorId);
                                                return `
                                                    <tr>
                                                        <td>#${ticket.id.toString().padStart(5, '0')}</td>
                                                        <td>${ticket.subject}</td>
                                                        <td>
                                                            <span class="badge badge-${ticket.priority === 'high' ? 'danger' : ticket.priority === 'medium' ? 'warning' : 'success'}">
                                                                ${ticket.priority}
                                                            </span>
                                                        </td>
                                                        <td>
                                                            <span class="badge badge-${ticket.status === 'resolved' ? 'success' : 'primary'}">
                                                                ${ticket.status || 'Open'}
                                                            </span>
                                                        </td>
                                                        <td>${new Date(ticket.createdAt).toLocaleDateString()}</td>
                                                        <td>
                                                            <button class="btn btn-sm btn-primary" onclick="app.viewTicket(${ticket.id})">
                                                                View
                                                            </button>
                                                        </td>
                                                    </tr>
                                                `;
                                            }).join('')}
                                        </tbody>
                                    </table>
                                </div>
                            ` : '<p style="text-align: center; color: var(--text-muted);">No support tickets</p>'}
                        </div>
                    </div>
                `;
            },

            renderAnalytics: function () {
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Analytics</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Track your business performance</p>
                        </div>
                        <div class="dropdown">
                            <button class="btn btn-secondary" onclick="app.toggleDropdown(this)">
                                <i data-lucide="calendar" class="icon"></i>
                                Last 30 Days
                            </button>
                            <div class="dropdown-menu">
                                <a href="#" class="dropdown-item">Last 7 days</a>
                                <a href="#" class="dropdown-item">Last 30 days</a>
                                <a href="#" class="dropdown-item">Last 3 months</a>
                                <a href="#" class="dropdown-item">Last year</a>
                            </div>
                        </div>
                    </div>

                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="trending-up" class="icon"></i>
                            </div>
                            <div class="stat-value">+23%</div>
                            <div class="stat-label">Revenue Growth</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="users" class="icon"></i>
                            </div>
                            <div class="stat-value">156</div>
                            <div class="stat-label">Total Users</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="briefcase" class="icon"></i>
                            </div>
                            <div class="stat-value">42</div>
                            <div class="stat-label">Projects Completed</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon">
                                <i data-lucide="star" class="icon"></i>
                            </div>
                            <div class="stat-value">4.8</div>
                            <div class="stat-label">Average Rating</div>
                        </div>
                    </div>

                    <div style="display: grid; grid-template-columns: 1fr; gap: 1.5rem;">
                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Revenue Overview</h3>
                            </div>
                            <div class="card-body">
                                <div style="height: 300px; display: flex; align-items: center; justify-content: center; background: var(--light); border-radius: 8px;">
                                    <div style="text-align: center;">
                                        <i data-lucide="bar-chart-2" class="icon" style="width: 48px; height: 48px; color: var(--text-muted); margin-bottom: 1rem;"></i>
                                        <p style="color: var(--text-muted);">Chart visualization would go here</p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Top Performing Editors</h3>
                            </div>
                            <div class="card-body">
                                ${this.data.users.filter(u => u.role === 'editor' && u.approved).slice(0, 5).map((editor, index) => `
                                    <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                        <div style="display: flex; align-items: center; gap: 1rem;">
                                            <div style="width: 32px; height: 32px; background: linear-gradient(135deg, var(--primary), var(--secondary)); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-weight: 600;">
                                                ${index + 1}
                                            </div>
                                            <div>
                                                <div style="font-weight: 600;">${editor.name}</div>
                                                <div style="font-size: 0.875rem; color: var(--text-muted);">${editor.totalWorkTime || 0} hours</div>
                                            </div>
                                        </div>
                                        <div style="text-align: right;">
                                            <div style="font-weight: 600; color: var(--primary);">₹${(editor.pendingSalary || 0).toLocaleString('en-IN')}</div>
                                            <div style="font-size: 0.875rem; color: var(--text-muted);">earned</div>
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                        </div>
                    </div>
                `;
            },

            renderProfile: function () {
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Profile</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Manage your account settings</p>
                        </div>
                    </div>

                    <div style="display: grid; grid-template-columns: 1fr; gap: 1.5rem; max-width: 800px;">
                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Personal Information</h3>
                            </div>
                            <div class="card-body">
                                <div style="display: flex; align-items: center; gap: 1.5rem; margin-bottom: 2rem;">
                                    <div class="avatar avatar-lg">${this.currentUser.avatar}</div>
                                    <div>
                                        <button class="btn btn-primary btn-sm">Change Avatar</button>
                                        <p style="font-size: 0.875rem; color: var(--text-muted); margin-top: 0.5rem;">JPG, GIF or PNG. Max size of 2MB</p>
                                    </div>
                                </div>
                                <form onsubmit="app.updateProfile(event)">
                                    <div class="form-row">
                                        <div class="form-group">
                                            <label class="form-label">Full Name</label>
                                            <input type="text" class="form-control" value="${this.currentUser.name}" readonly>
                                        </div>
                                        <div class="form-group">
                                            <label class="form-label">Email</label>
                                            <input type="email" class="form-control" value="${this.currentUser.email}" readonly>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Phone</label>
                                        <input type="tel" class="form-control" placeholder="Enter your phone number">
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Bio</label>
                                        <textarea class="form-control" rows="3" placeholder="Tell us about yourself..."></textarea>
                                    </div>
                                    <button type="submit" class="btn btn-primary">Save Changes</button>
                                </form>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Change Password</h3>
                            </div>
                            <div class="card-body">
                                <form onsubmit="app.changePassword(event)">
                                    <div class="form-group">
                                        <label class="form-label">Current Password</label>
                                        <input type="password" class="form-control" required>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">New Password</label>
                                        <input type="password" class="form-control" required>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Confirm New Password</label>
                                        <input type="password" class="form-control" required>
                                    </div>
                                    <button type="submit" class="btn btn-primary">Update Password</button>
                                </form>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Preferences</h3>
                            </div>
                            <div class="card-body">
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Dark Mode</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Toggle dark theme</div>
                                    </div>
                                    <div class="theme-toggle" onclick="app.toggleTheme()"></div>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Email Notifications</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Receive email updates</div>
                                    </div>
                                    <label class="switch">
                                        <input type="checkbox" checked>
                                        <span class="slider"></span>
                                    </label>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0;">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Push Notifications</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Receive push notifications</div>
                                    </div>
                                    <label class="switch">
                                        <input type="checkbox" checked>
                                        <span class="slider"></span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            },

            renderSettings: function () {
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Settings</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Configure your application</p>
                        </div>
                    </div>

                    <div style="display: grid; grid-template-columns: 1fr; gap: 1.5rem; max-width: 800px;">
                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">General Settings</h3>
                            </div>
                            <div class="card-body">
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Language</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Select your preferred language</div>
                                    </div>
                                    <select class="form-control" style="width: 150px;">
                                        <option>English</option>
                                        <option>Spanish</option>
                                        <option>French</option>
                                    </select>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Timezone</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Set your timezone</div>
                                    </div>
                                    <select class="form-control" style="width: 200px;">
                                        <option>UTC+05:30 (India)</option>
                                        <option>UTC+00:00 (London)</option>
                                        <option>UTC-05:00 (New York)</option>
                                    </select>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0;">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Currency</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Display currency</div>
                                    </div>
                                    <select class="form-control" style="width: 100px;">
                                        <option>₹ INR</option>
                                        <option>$ USD</option>
                                        <option>€ EUR</option>
                                    </select>
                                </div>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Security</h3>
                            </div>
                            <div class="card-body">
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Two-Factor Authentication</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Add an extra layer of security</div>
                                    </div>
                                    <button class="btn btn-primary btn-sm">Enable</button>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Session Timeout</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Auto-logout after inactivity</div>
                                    </div>
                                    <select class="form-control" style="width: 120px;">
                                        <option>30 minutes</option>
                                        <option>1 hour</option>
                                        <option>2 hours</option>
                                    </select>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0;">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Login History</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">View recent login activity</div>
                                    </div>
                                    <button class="btn btn-secondary btn-sm">View</button>
                                </div>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Data & Privacy</h3>
                            </div>
                            <div class="card-body">
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Export Data</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Download your data</div>
                                    </div>
                                    <button class="btn btn-secondary btn-sm">Export</button>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">Clear Cache</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Clear application cache</div>
                                    </div>
                                    <button class="btn btn-secondary btn-sm">Clear</button>
                                </div>
                                <div style="display: flex; align-items: center; justify-content: space-between; padding: 1rem 0;">
                                    <div>
                                        <div style="font-weight: 600; margin-bottom: 0.25rem; color: var(--danger);">Delete Account</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">Permanently delete your account</div>
                                    </div>
                                    <button class="btn btn-danger btn-sm">Delete</button>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            },

            renderNotifications: function () {
                const notifications = this.data.notifications.filter(n => n.userId === this.currentUser.id);
                
                return `
                    <div class="page-header" style="margin-bottom: 2rem;">
                        <div>
                            <h1 class="page-title" style="font-size: 1.875rem; font-weight: 700; margin-bottom: 0.5rem;">Notifications</h1>
                            <p class="page-subtitle" style="color: var(--text-muted);">Stay updated with latest activities</p>
                        </div>
                        <button class="btn btn-secondary" onclick="app.markAllNotificationsRead()">
                            Mark all as read
                        </button>
                    </div>

                    <div class="card">
                        <div class="card-body">
                            ${notifications.length > 0 ? notifications.map(notification => `
                                <div style="display: flex; align-items: start; gap: 1rem; padding: 1rem 0; border-bottom: 1px solid var(--border); ${!notification.read ? 'background: rgba(99, 102, 241, 0.05);' : ''}">
                                    <div style="width: 40px; height: 40px; background: linear-gradient(135deg, var(--primary), var(--secondary)); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; flex-shrink: 0;">
                                        <i data-lucide="bell" class="icon" style="width: 20px; height: 20px;"></i>
                                    </div>
                                    <div style="flex: 1;">
                                        <div style="font-weight: 600; margin-bottom: 0.25rem;">${notification.title}</div>
                                        <div style="color: var(--text-muted); margin-bottom: 0.5rem;">${notification.message}</div>
                                        <div style="font-size: 0.875rem; color: var(--text-muted);">${this.formatTime(notification.timestamp)}</div>
                                    </div>
                                    ${!notification.read ? '<div style="width: 8px; height: 8px; background: var(--primary); border-radius: 50%; margin-top: 0.5rem;"></div>' : ''}
                                </div>
                            `).join('') : '<p style="text-align: center; color: var(--text-muted); padding: 3rem;">No notifications</p>'}
                        </div>
                    </div>
                `;
            },

            // Navigation Functions
            navigate: function (page) {
                this.currentPage = page;
                
                // Update navigation states
                document.querySelectorAll('.nav-item, .bottom-nav-item').forEach(item => {
                    item.classList.remove('active');
                });
                
                event.target.closest('.nav-item, .bottom-nav-item')?.classList.add('active');
                
                // Close mobile sidebar
                if (window.innerWidth < 1024) {
                    this.toggleSidebar();
                }
                
                // Render page
                this.renderApp();
            },

            toggleSidebar: function () {
                const sidebar = document.getElementById('sidebar');
                const overlay = document.getElementById('sidebar-overlay');
                
                sidebar.classList.toggle('active');
                overlay.classList.toggle('active');
            },

            toggleDropdown: function (button) {
                const dropdown = button.closest('.dropdown');
                const wasActive = dropdown.classList.contains('active');
                
                // Close all dropdowns
                document.querySelectorAll('.dropdown.active').forEach(d => {
                    d.classList.remove('active');
                });
                
                // Toggle current dropdown
                if (!wasActive) {
                    dropdown.classList.add('active');
                }
            },

            toggleTheme: function () {
                const currentTheme = document.documentElement.getAttribute('data-theme');
                const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
                
                document.documentElement.setAttribute('data-theme', newTheme);
                localStorage.setItem('theme', newTheme);
                
                // Update icon
                const themeIcon = document.querySelector('.header-action[data-lucide="moon"], .header-action[data-lucide="sun"]');
                if (themeIcon) {
                    themeIcon.setAttribute('data-lucide', newTheme === 'dark' ? 'sun' : 'moon');
                    lucide.createIcons();
                }
            },

            showQuickActions: function () {
                this.openModal('quick-actions');
            },

            openModal: function (type) {
                let modalContent = '';

                switch (type) {
                    case 'add-client':
                        modalContent = `
                            <div class="modal-header">
                                <h3 class="modal-title">Add New Client</h3>
                                <button class="modal-close" onclick="app.closeModal()">&times;</button>
                            </div>
                            <div class="modal-body">
                                <form onsubmit="app.addClient(event)">
                                    <div class="form-row">
                                        <div class="form-group">
                                            <label class="form-label">Full Name</label>
                                            <input type="text" name="name" class="form-control" required>
                                        </div>
                                        <div class="form-group">
                                            <label class="form-label">Company</label>
                                            <input type="text" name="company" class="form-control" required>
                                        </div>
                                    </div>
                                    <div class="form-row">
                                        <div class="form-group">
                                            <label class="form-label">Email</label>
                                            <input type="email" name="email" class="form-control" required>
                                        </div>
                                        <div class="form-group">
                                            <label class="form-label">Phone</label>
                                            <input type="tel" name="phone" class="form-control" required>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Address</label>
                                        <textarea name="address" class="form-control" rows="2"></textarea>
                                    </div>
                                </form>
                            </div>
                            <div class="modal-footer">
                                <button class="btn btn-secondary" onclick="app.closeModal()">Cancel</button>
                                <button class="btn btn-primary" onclick="document.querySelector('#add-client-form').requestSubmit()">Add Client</button>
                            </div>
                        `;
                        break;

                    case 'add-editor':
                        modalContent = `
                            <div class="modal-header">
                                <h3 class="modal-title">Add New Editor</h3>
                                <button class="modal-close" onclick="app.closeModal()">&times;</button>
                            </div>
                            <div class="modal-body">
                                <form onsubmit="app.addEditor(event)">
                                    <div class="form-row">
                                        <div class="form-group">
                                            <label class="form-label">Full Name</label>
                                            <input type="text" name="name" class="form-control" required>
                                        </div>
                                        <div class="form-group">
                                            <label class="form-label">Email</label>
                                            <input type="email" name="email" class="form-control" required>
                                        </div>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Password</label>
                                        <input type="password" name="password" class="form-control" required>
                                    </div>
                                </form>
                            </div>
                            <div class="modal-footer">
                                <button class="btn btn-secondary" onclick="app.closeModal()">Cancel</button>
                                <button class="btn btn-primary" onclick="document.querySelector('#add-editor-form').requestSubmit()">Add Editor</button>
                            </div>
                        `;
                        break;

                    case 'add-project':
                        modalContent = `
                            <div class="modal-header">
                                <h3 class="modal-title">Create New Project</h3>
                                <button class="modal-close" onclick="app.closeModal()">&times;</button>
                            </div>
                            <div class="modal-body">
                                <form onsubmit="app.addProject(event)">
                                    <div class="form-group">
                                        <label class="form-label">Project Name</label>
                                        <input type="text" name="name" class="form-control" required>
                                    </div>
                                    <div class="form-group">
                                        <label class="form-label">Description</label>
                                        <textarea name="description" class="form-control" rows="2"></textarea>
                                    </div>
                                    <div class="form-row">
                                        <div class="form-group">
                                            <label class="form-label">Client</label>
                                            <select name="clientId" class="form-control" required>
                                                <option value="">Select Client</option>
                                                ${this.data.clients.map(client => `
                                                    <option value="${client.id}">${client.name}</option>
                                                `).join('')}
                                            </select>
                                        </div>
                                        <div class="form-group">
                                            <label class="form-label">Budget (₹)</label>
                                            <input type="number" name="budget" class="form-control" required>
                                        </div>
                                    </div>
                                    <div class="form-row">
                                        <div class="form-group">
                                            <label class="form-label">Assign Editor</label>
                                            <select name="assignedEditorId" class="form-control">
                                                <option value="">Select Editor (Optional)</option>
                                                ${this.data.users.filter(u => u.role === 'editor' && u.approved).map(editor => `
                                                    <option value="${editor.id}">${editor.name}</option>
                                                `).join('')}
                                            </select>
                                        </div>
                                        <div class="form-group">
                                            <label class="form-label">Deadline</label>
                                            <input type="date" name="deadline" class="form-control">
                                        </div>
                                    </div>
                                </form>
                            </div>
                            <div class="modal-footer">
                                <button class="btn btn-secondary" onclick="app.closeModal()">Cancel</button>
                                <button class="btn btn-primary" onclick="document.querySelector('#add-project-form').requestSubmit()">Create Project</button>
                            </div>
                        `;
                        break;

                    case 'quick-actions':
                        modalContent = `
                            <div class="modal-header">
                                <h3 class="modal-title">Quick Actions</h3>
                                <button class="modal-close" onclick="app.closeModal()">&times;</button>
                            </div>
                            <div class="modal-body">
                                <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem;">
                                    <button class="btn btn-primary" style="height: auto; padding: 1.5rem; flex-direction: column;" onclick="app.closeModal(); app.openModal('add-project')">
                                        <i data-lucide="plus" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        New Project
                                    </button>
                                    <button class="btn btn-secondary" style="height: auto; padding: 1.5rem; flex-direction: column;" onclick="app.closeModal(); app.openModal('add-client')">
                                        <i data-lucide="user-plus" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        Add Client
                                    </button>
                                    <button class="btn btn-secondary" style="height: auto; padding: 1.5rem; flex-direction: column;" onclick="app.closeModal(); app.navigate('invoices')">
                                        <i data-lucide="file-text" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        Create Invoice
                                    </button>
                                    <button class="btn btn-secondary" style="height: auto; padding: 1.5rem; flex-direction: column;" onclick="app.closeModal(); app.navigate('support')">
                                        <i data-lucide="help-circle" class="icon" style="width: 24px; height: 24px; margin-bottom: 0.5rem;"></i>
                                        Get Support
                                    </button>
                                </div>
                            </div>
                        `;
                        break;
                }

                const modal = document.createElement('div');
                modal.className = 'modal';
                modal.innerHTML = modalContent;
                document.body.appendChild(modal);
                
                setTimeout(() => modal.classList.add('active'), 10);
                lucide.createIcons();
            },

            closeModal: function () {
                const modal = document.querySelector('.modal.active');
                if (modal) {
                    modal.classList.remove('active');
                    setTimeout(() => modal.remove(), 300);
                }
            },

            // Action Functions
            addClient: function (event) {
                event.preventDefault();
                const formData = new FormData(event.target);
                
                const client = {
                    id: Date.now(),
                    name: formData.get('name'),
                    company: formData.get('company'),
                    email: formData.get('email'),
                    phone: formData.get('phone'),
                    address: formData.get('address'),
                    avatar: formData.get('name').split(' ').map(n => n[0]).join('').toUpperCase()
                };

                this.data.clients.push(client);
                this.saveData();
                this.closeModal();
                this.navigate('clients');
                this.showToast('success', 'Client Added', 'New client has been added successfully');
            },

            addEditor: function (event) {
                event.preventDefault();
                const formData = new FormData(event.target);
                
                const editor = {
                    id: Date.now(),
                    name: formData.get('name'),
                    email: formData.get('email'),
                    password: formData.get('password'),
                    role: 'editor',
                    approved: false,
                    avatar: formData.get('name').split(' ').map(n => n[0]).join('').toUpperCase(),
                    totalWorkTime: 0,
                    pendingSalary: 0
                };

                this.data.users.push(editor);
                this.saveData();
                this.closeModal();
                this.navigate('editors');
                this.showToast('success', 'Editor Added', 'New editor has been added. Waiting for approval.');
            },

            addProject: function (event) {
                event.preventDefault();
                const formData = new FormData(event.target);
                
                const project = {
                    id: Date.now(),
                    name: formData.get('name'),
                    description: formData.get('description'),
                    clientId: parseInt(formData.get('clientId')),
                    budget: parseInt(formData.get('budget')),
                    assignedEditorId: formData.get('assignedEditorId') ? parseInt(formData.get('assignedEditorId')) : null,
                    deadline: formData.get('deadline'),
                    status: 'pending',
                    progress: 0
                };

                this.data.projects.push(project);
                
                if (project.assignedEditorId) {
                    this.createWorkAssignment(project.id, project.assignedEditorId);
                }
                
                this.saveData();
                this.closeModal();
                this.navigate('projects');
                this.showToast('success', 'Project Created', 'New project has been created successfully');
            },

            createTicket: function (event) {
                event.preventDefault();
                const formData = new FormData(event.target);
                
                const ticket = {
                    id: Date.now(),
                    editorId: this.currentUser.id,
                    subject: formData.get('subject'),
                    priority: formData.get('priority'),
                    description: formData.get('description'),
                    status: 'open',
                    createdAt: new Date().toISOString()
                };
                
                this.data.tickets.push(ticket);
                this.saveData();
                
                this.addNotification(1, 'New Support Ticket', `${this.currentUser.name}: ${ticket.subject}`);
                
                event.target.reset();
                this.showToast('success', 'Ticket Submitted', 'Your support ticket has been submitted');
            },

            approveEditor: function (editorId) {
                const editor = this.data.users.find(u => u.id === editorId);
                if (editor) {
                    editor.approved = true;
                    this.saveData();
                    this.addNotification(editorId, 'Account Approved', 'Your account has been approved. You can now login.');
                    this.navigate('editors');
                    this.showToast('success', 'Editor Approved', `${editor.name} has been approved`);
                }
            },

            updateEditorSalary: function (editorId) {
                const amount = prompt('Enter amount to add to pending salary:');
                if (amount && !isNaN(amount)) {
                    const editor = this.data.users.find(u => u.id === editorId);
                    if (editor) {
                        editor.pendingSalary = (editor.pendingSalary || 0) + parseFloat(amount);
                        this.saveData();
                        this.navigate('editors');
                        this.showToast('success', 'Salary Updated', `Pending salary updated for ${editor.name}`);
                    }
                }
            },

            markInvoicePaid: function (invoiceId) {
                const invoice = this.data.invoices.find(i => i.id === invoiceId);
                if (invoice) {
                    invoice.status = 'paid';
                    this.saveData();
                    this.navigate('invoices');
                    this.showToast('success', 'Invoice Paid', 'Invoice has been marked as paid');
                }
            },

            // Chat Functions
            openChatWith: function (userId) {
                const user = this.data.users.find(u => u.id === userId);
                const messages = this.getMessages(this.currentUser.id, userId);
                
                const chatMain = document.getElementById('chat-main');
                chatMain.innerHTML = `
                    <div class="chat-header" style="padding: 1rem; border-bottom: 1px solid var(--border); display: flex; justify-content: space-between; align-items: center;">
                        <div style="display: flex; align-items: center; gap: 0.75rem;">
                            <button class="btn-icon hide-desktop" onclick="app.navigate('chat')">
                                <i data-lucide="arrow-left" class="icon"></i>
                            </button>
                            <div class="avatar">${user.avatar}</div>
                            <div>
                                <div style="font-weight: 600;">${user.name}</div>
                                <div style="font-size: 0.875rem; color: var(--text-muted);">Online</div>
                            </div>
                        </div>
                        <button class="btn-icon" onclick="app.closeChat()">
                            <i data-lucide="x" class="icon"></i>
                        </button>
                    </div>
                    <div class="chat-messages" style="flex: 1; padding: 1rem; overflow-y: auto;">
                        ${messages.map(msg => `
                            <div class="message ${msg.senderId === this.currentUser.id ? 'sent' : 'received'}">
                                <div class="message-bubble">
                                    <div class="message-text">${msg.text}</div>
                                    <div class="message-time">${this.formatTime(msg.timestamp)}</div>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                    <div class="chat-input-container">
                        <div class="chat-input-wrapper">
                            <input type="text" class="chat-input" placeholder="Type a message..." id="chat-input" onkeypress="if(event.key === 'Enter') app.sendMessage(${userId})">
                            <button class="chat-send-btn" onclick="app.sendMessage(${userId})">
                                <i data-lucide="send" class="icon"></i>
                            </button>
                        </div>
                    </div>
                `;
                
                document.getElementById('chat-input')?.focus();
                lucide.createIcons();
            },

            closeChat: function () {
                const chatMain = document.getElementById('chat-main');
                chatMain.innerHTML = `
                    <div class="empty-state">
                        <i data-lucide="message-circle" class="empty-state-icon"></i>
                        <h3 class="empty-state-title">Select a conversation</h3>
                        <p class="empty-state-text">Choose a user from the list to start chatting</p>
                    </div>
                `;
                lucide.createIcons();
            },

            sendMessage: function (receiverId) {
                const input = document.getElementById('chat-input');
                const text = input.value.trim();
                
                if (!text) return;
                
                const message = {
                    id: Date.now(),
                    senderId: this.currentUser.id,
                    receiverId: receiverId,
                    text: text,
                    timestamp: new Date().toISOString()
                };
                
                this.data.messages.push(message);
                this.saveData();
                
                input.value = '';
                this.openChatWith(receiverId);
            },

            getMessages: function (userId1, userId2) {
                return this.data.messages.filter(m => 
                    (m.senderId === userId1 && m.receiverId === userId2) || 
                    (m.senderId === userId2 && m.receiverId === userId1)
                ).sort((a, b) => new Date(a.timestamp) - new Date(b.timestamp));
            },

            getLastMessage: function (userId1, userId2) {
                const messages = this.getMessages(userId1, userId2);
                return messages.length > 0 ? messages[messages.length - 1] : null;
            },

            // Notification Functions
            addNotification: function (userId, title, message) {
                const notification = {
                    id: Date.now(),
                    userId: userId,
                    title: title,
                    message: message,
                    read: false,
                    timestamp: new Date().toISOString()
                };
                
                this.data.notifications.push(notification);
                this.saveData();
                
                if (userId === this.currentUser.id) {
                    this.showToast('info', title, message);
                    this.updateNotificationBadge();
                }
            },

            getUnreadNotifications: function () {
                return this.data.notifications.filter(n => 
                    n.userId === this.currentUser.id && !n.read
                );
            },

            updateNotificationBadge: function () {
                const unreadCount = this.getUnreadNotifications().length;
                const badges = document.querySelectorAll('.notification-badge');
                
                badges.forEach(badge => {
                    if (unreadCount > 0) {
                        badge.style.display = 'block';
                        badge.textContent = unreadCount > 9 ? '9+' : unreadCount;
                    } else {
                        badge.style.display = 'none';
                    }
                });
            },

            openNotifications: function () {
                this.navigate('notifications');
            },

            markAllNotificationsRead: function () {
                this.data.notifications.forEach(n => {
                    if (n.userId === this.currentUser.id) {
                        n.read = true;
                    }
                });
                this.saveData();
                this.updateNotificationBadge();
                this.renderApp();
            },

            // Helper Functions
            getDashboardStats: function () {
                return {
                    totalRevenue: this.data.invoices.reduce((sum, i) => sum + i.amount, 0),
                    activeProjects: this.data.projects.filter(p => p.status === 'in-progress').length,
                    totalClients: this.data.clients.length,
                    activeEditors: this.data.users.filter(u => u.role === 'editor' && u.approved).length
                };
            },

            formatTime: function (timestamp) {
                const date = new Date(timestamp);
                const now = new Date();
                const diffMs = now - date;
                const diffMins = Math.floor(diffMs / 60000);

                if (diffMins < 1) return 'Just now';
                if (diffMins < 60) return `${diffMins}m ago`;

                const diffHours = Math.floor(diffMins / 60);
                if (diffHours < 24) return `${diffHours}h ago`;

                return date.toLocaleDateString();
            },

            handleSearch: function (event) {
                const query = event.target.value.toLowerCase();
                if (query.length > 2) {
                    // Implement search functionality
                    console.log('Searching for:', query);
                }
            },

            switchTab: function (tabElement, filter) {
                // Update active tab
                tabElement.parentElement.querySelectorAll('.tab').forEach(tab => {
                    tab.classList.remove('active');
                });
                tabElement.classList.add('active');
                
                // Filter content based on tab
                console.log('Switching to filter:', filter);
            },

            setupDropdowns: function () {
                document.querySelectorAll('.dropdown').forEach(dropdown => {
                    const toggle = dropdown.querySelector('.dropdown-toggle, .header-action');
                    if (toggle) {
                        toggle.addEventListener('click', (e) => {
                            e.stopPropagation();
                            this.toggleDropdown(toggle);
                        });
                    }
                });

                document.addEventListener('click', () => {
                    document.querySelectorAll('.dropdown.active').forEach(d => {
                        d.classList.remove('active');
                    });
                });
            },

            setupEventListeners: function () {
                // Form submissions
                document.addEventListener('submit', (e) => {
                    if (e.target.id === 'profile-form') {
                        e.preventDefault();
                        this.showToast('success', 'Profile Updated', 'Your profile has been updated');
                    }
                    
                    if (e.target.id === 'password-form') {
                        e.preventDefault();
                        this.showToast('success', 'Password Changed', 'Your password has been updated');
                    }
                });

                // Handle window resize
                window.addEventListener('resize', () => {
                    if (window.innerWidth >= 1024) {
                        document.getElementById('sidebar').classList.remove('active');
                        document.getElementById('sidebar-overlay').classList.remove('active');
                    }
                });
            },

            setupPullToRefresh: function () {
                let startY = 0;
                let isPulling = false;
                
                document.addEventListener('touchstart', (e) => {
                    if (window.scrollY === 0) {
                        startY = e.touches[0].clientY;
                        isPulling = true;
                    }
                });
                
                document.addEventListener('touchmove', (e) => {
                    if (!isPulling) return;
                    
                    const currentY = e.touches[0].clientY;
                    const diff = currentY - startY;
                    
                    if (diff > 0 && diff < 150) {
                        const pullToRefresh = document.getElementById('pull-to-refresh');
                        pullToRefresh.style.transform = `translateY(${diff}px)`;
                        
                        if (diff > 100) {
                            pullToRefresh.classList.add('active');
                        } else {
                            pullToRefresh.classList.remove('active');
                        }
                    }
                });
                
                document.addEventListener('touchend', () => {
                    if (isPulling) {
                        const pullToRefresh = document.getElementById('pull-to-refresh');
                        
                        if (pullToRefresh.classList.contains('active')) {
                            // Refresh content
                            this.renderApp();
                            this.showToast('success', 'Refreshed', 'Content has been updated');
                        }
                        
                        pullToRefresh.style.transform = '';
                        pullToRefresh.classList.remove('active');
                        isPulling = false;
                    }
                });
            },

            showToast: function (type, title, message) {
                const toastContainer = document.getElementById('toast-container');
                const toast = document.createElement('div');
                toast.className = `toast ${type}`;
                
                let icon = '';
                switch (type) {
                    case 'success': icon = 'check-circle'; break;
                    case 'error': icon = 'x-circle'; break;
                    case 'warning': icon = 'alert-triangle'; break;
                    case 'info': icon = 'info'; break;
                }
                
                toast.innerHTML = `
                    <i data-lucide="${icon}" class="toast-icon"></i>
                    <div class="toast-content">
                        <div class="toast-title">${title}</div>
                        <div class="toast-message">${message}</div>
                    </div>
                    <button class="toast-close" onclick="this.parentElement.remove()">
                        <i data-lucide="x"></i>
                    </button>
                `;
                
                toastContainer.appendChild(toast);
                lucide.createIcons();
                
                setTimeout(() => {
                    if (toast.parentElement) {
                        toast.remove();
                    }
                }, 5000);
            }
        };

        // Initialize App
        document.addEventListener('DOMContentLoaded', () => {
            app.init();
        });
    </script>
</body>

</html>
