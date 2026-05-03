<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SafeRide – Your Safety, Our Priority</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --green: #00C86F;
    --green-dark: #00A85E;
    --green-light: #E6FAF1;
    --black: #0A0A0A;
    --gray-900: #111827;
    --gray-800: #1F2937;
    --gray-700: #374151;
    --gray-500: #6B7280;
    --gray-300: #D1D5DB;
    --gray-100: #F3F4F6;
    --white: #FFFFFF;
    --amber: #F59E0B;
    --red: #EF4444;
    --blue: #3B82F6;
    --radius: 16px;
    --shadow: 0 4px 24px rgba(0,0,0,0.08);
    --shadow-lg: 0 12px 48px rgba(0,0,0,0.14);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--gray-100);
    color: var(--gray-900);
    min-height: 100vh;
  }

  h1,h2,h3,h4,h5 { font-family: 'Syne', sans-serif; }

  /* ===== LAYOUT ===== */
  .app { display: flex; flex-direction: column; min-height: 100vh; }

  /* ===== NAV ===== */
  nav {
    background: var(--black);
    padding: 0 32px;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 20px rgba(0,0,0,0.3);
  }
  .logo {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 800;
    color: var(--white);
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
  }
  .logo-dot { color: var(--green); }
  .logo-icon {
    width: 36px; height: 36px;
    background: var(--green);
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
  }
  .nav-links { display: flex; align-items: center; gap: 8px; }
  .nav-btn {
    background: none;
    border: none;
    color: var(--gray-300);
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    font-weight: 500;
    padding: 8px 16px;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.2s;
  }
  .nav-btn:hover { color: var(--white); background: var(--gray-800); }
  .nav-btn.active { color: var(--green); }
  .nav-btn.primary {
    background: var(--green);
    color: var(--black);
    font-weight: 600;
  }
  .nav-btn.primary:hover { background: var(--green-dark); color: var(--white); }
  .nav-user {
    display: flex; align-items: center; gap: 12px;
    color: var(--white);
    font-size: 14px;
  }
  .nav-avatar {
    width: 36px; height: 36px;
    background: var(--green);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-weight: 700;
    color: var(--black);
    font-size: 14px;
  }

  /* ===== SCREENS ===== */
  .screen { display: none; flex: 1; }
  .screen.active { display: block; }

  /* ===== HERO ===== */
  .hero {
    background: var(--black);
    color: var(--white);
    padding: 80px 48px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 64px;
    align-items: center;
    min-height: calc(100vh - 64px);
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -50%;
    right: -20%;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(0,200,111,0.15) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,200,111,0.15);
    border: 1px solid rgba(0,200,111,0.3);
    border-radius: 100px;
    padding: 6px 16px;
    font-size: 13px;
    color: var(--green);
    margin-bottom: 24px;
    font-weight: 500;
  }
  .hero h1 {
    font-size: 62px;
    font-weight: 800;
    line-height: 1.08;
    letter-spacing: -2px;
    margin-bottom: 24px;
  }
  .hero h1 span { color: var(--green); }
  .hero p {
    font-size: 18px;
    color: rgba(255,255,255,0.6);
    line-height: 1.7;
    margin-bottom: 40px;
  }
  .hero-actions { display: flex; gap: 16px; flex-wrap: wrap; }
  .btn {
    padding: 14px 28px;
    border-radius: 12px;
    border: none;
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.25s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    text-decoration: none;
  }
  .btn-primary {
    background: var(--green);
    color: var(--black);
  }
  .btn-primary:hover {
    background: var(--green-dark);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,200,111,0.35);
  }
  .btn-outline {
    background: transparent;
    color: var(--white);
    border: 1.5px solid rgba(255,255,255,0.25);
  }
  .btn-outline:hover {
    border-color: var(--white);
    background: rgba(255,255,255,0.08);
  }
  .btn-dark {
    background: var(--gray-800);
    color: var(--white);
  }
  .btn-dark:hover { background: var(--gray-700); }
  .btn-danger { background: var(--red); color: var(--white); }
  .btn-danger:hover { background: #DC2626; }
  .btn-sm { padding: 8px 18px; font-size: 13px; border-radius: 8px; }

  /* Hero card */
  .hero-card {
    background: var(--gray-900);
    border: 1px solid var(--gray-800);
    border-radius: 24px;
    padding: 32px;
    box-shadow: var(--shadow-lg);
  }
  .hero-card h3 {
    font-size: 20px;
    color: var(--white);
    margin-bottom: 24px;
  }
  .hero-stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-top: 32px;
  }
  .hero-stat {
    text-align: center;
    padding: 16px;
    background: rgba(255,255,255,0.04);
    border-radius: 12px;
    border: 1px solid rgba(255,255,255,0.06);
  }
  .hero-stat .num {
    font-size: 26px;
    font-weight: 800;
    color: var(--green);
    font-family: 'Syne', sans-serif;
  }
  .hero-stat .lbl {
    font-size: 12px;
    color: var(--gray-500);
    margin-top: 4px;
  }

  /* Features */
  .features {
    padding: 80px 48px;
    background: var(--white);
  }
  .section-label {
    font-size: 12px;
    font-weight: 600;
    color: var(--green);
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 12px;
  }
  .section-title {
    font-size: 40px;
    font-weight: 800;
    color: var(--black);
    margin-bottom: 16px;
  }
  .section-sub {
    font-size: 16px;
    color: var(--gray-500);
    margin-bottom: 56px;
  }
  .features-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
  }
  .feature-card {
    padding: 32px;
    border-radius: var(--radius);
    border: 1px solid var(--gray-100);
    transition: all 0.3s;
  }
  .feature-card:hover {
    box-shadow: var(--shadow-lg);
    transform: translateY(-4px);
    border-color: var(--green-light);
  }
  .feature-icon {
    width: 52px; height: 52px;
    border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px;
    margin-bottom: 20px;
  }
  .feature-card h4 { font-size: 18px; margin-bottom: 10px; }
  .feature-card p { font-size: 14px; color: var(--gray-500); line-height: 1.7; }

  /* ===== FORMS ===== */
  .auth-screen {
    display: flex;
    min-height: calc(100vh - 64px);
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, var(--gray-900) 0%, var(--black) 100%);
    padding: 40px;
  }
  .auth-card {
    background: var(--white);
    border-radius: 24px;
    padding: 48px;
    width: 100%;
    max-width: 460px;
    box-shadow: var(--shadow-lg);
  }
  .auth-card h2 { font-size: 28px; margin-bottom: 6px; }
  .auth-card .sub { font-size: 14px; color: var(--gray-500); margin-bottom: 32px; }
  .form-group { margin-bottom: 20px; }
  .form-label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: var(--gray-700);
    margin-bottom: 8px;
  }
  .form-input {
    width: 100%;
    padding: 12px 16px;
    border: 1.5px solid var(--gray-300);
    border-radius: 10px;
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    color: var(--gray-900);
    background: var(--white);
    transition: border-color 0.2s;
    outline: none;
  }
  .form-input:focus { border-color: var(--green); box-shadow: 0 0 0 3px rgba(0,200,111,0.1); }
  .form-select {
    width: 100%;
    padding: 12px 16px;
    border: 1.5px solid var(--gray-300);
    border-radius: 10px;
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    background: var(--white);
    outline: none;
    cursor: pointer;
  }
  .form-select:focus { border-color: var(--green); }
  .form-submit {
    width: 100%;
    padding: 14px;
    background: var(--green);
    color: var(--black);
    font-family: 'Syne', sans-serif;
    font-size: 16px;
    font-weight: 700;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    transition: all 0.25s;
    margin-top: 8px;
  }
  .form-submit:hover { background: var(--green-dark); }
  .form-submit:disabled { opacity: 0.6; cursor: not-allowed; }
  .form-switch {
    text-align: center;
    margin-top: 24px;
    font-size: 14px;
    color: var(--gray-500);
  }
  .form-switch a { color: var(--green); cursor: pointer; font-weight: 600; text-decoration: none; }

  /* Role toggle */
  .role-toggle {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 28px;
  }
  .role-option {
    padding: 14px;
    border: 2px solid var(--gray-200, #E5E7EB);
    border-radius: 12px;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s;
  }
  .role-option.selected {
    border-color: var(--green);
    background: var(--green-light);
  }
  .role-option .role-icon { font-size: 24px; margin-bottom: 6px; }
  .role-option .role-name { font-size: 13px; font-weight: 600; color: var(--gray-700); }

  /* ===== DASHBOARD ===== */
  .dashboard {
    display: grid;
    grid-template-columns: 280px 1fr;
    min-height: calc(100vh - 64px);
  }
  .sidebar {
    background: var(--black);
    padding: 32px 20px;
    display: flex;
    flex-direction: column;
    gap: 4px;
  }
  .sidebar-section {
    font-size: 11px;
    font-weight: 600;
    color: var(--gray-500);
    text-transform: uppercase;
    letter-spacing: 1.5px;
    padding: 16px 12px 8px;
  }
  .sidebar-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px 16px;
    border-radius: 10px;
    cursor: pointer;
    color: var(--gray-300);
    font-size: 14px;
    font-weight: 500;
    transition: all 0.2s;
    border: none;
    background: none;
    width: 100%;
    text-align: left;
  }
  .sidebar-item:hover { background: var(--gray-800); color: var(--white); }
  .sidebar-item.active { background: rgba(0,200,111,0.15); color: var(--green); }
  .sidebar-item .icon { font-size: 18px; width: 20px; text-align: center; }
  .sidebar-bottom { margin-top: auto; }

  .main-content { padding: 32px; overflow-y: auto; }
  .page-header { margin-bottom: 32px; }
  .page-header h2 { font-size: 28px; font-weight: 800; }
  .page-header p { font-size: 14px; color: var(--gray-500); margin-top: 4px; }

  /* Stats grid */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin-bottom: 32px;
  }
  .stat-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow);
    border: 1px solid var(--gray-100);
  }
  .stat-card .stat-icon {
    width: 44px; height: 44px;
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 20px;
    margin-bottom: 16px;
  }
  .stat-card .stat-value {
    font-size: 28px;
    font-weight: 800;
    font-family: 'Syne', sans-serif;
    color: var(--gray-900);
  }
  .stat-card .stat-label {
    font-size: 13px;
    color: var(--gray-500);
    margin-top: 4px;
  }
  .stat-card .stat-change {
    font-size: 12px;
    font-weight: 600;
    margin-top: 8px;
    display: inline-flex;
    align-items: center;
    gap: 4px;
  }
  .stat-change.up { color: var(--green); }
  .stat-change.neutral { color: var(--gray-500); }

  /* Cards */
  .card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow);
    border: 1px solid var(--gray-100);
    margin-bottom: 24px;
  }
  .card-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  .card-title { font-size: 17px; font-weight: 700; }

  /* Ride booking */
  .booking-layout {
    display: grid;
    grid-template-columns: 420px 1fr;
    gap: 24px;
  }
  .booking-panel { display: flex; flex-direction: column; gap: 16px; }

  .location-input-group {
    background: var(--white);
    border-radius: var(--radius);
    padding: 20px;
    box-shadow: var(--shadow);
    border: 1px solid var(--gray-100);
  }
  .location-input-group h3 { font-size: 16px; margin-bottom: 16px; }
  .location-row {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
  }
  .location-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .location-dot.pickup { background: var(--green); }
  .location-dot.drop { background: var(--red); }

  /* Vehicle selector */
  .vehicle-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .vehicle-card {
    border: 2px solid var(--gray-200, #E5E7EB);
    border-radius: 12px;
    padding: 16px;
    cursor: pointer;
    transition: all 0.2s;
    background: var(--white);
  }
  .vehicle-card:hover { border-color: var(--green-dark); }
  .vehicle-card.selected { border-color: var(--green); background: var(--green-light); }
  .vehicle-card .v-icon { font-size: 28px; margin-bottom: 8px; }
  .vehicle-card .v-name { font-size: 14px; font-weight: 700; }
  .vehicle-card .v-desc { font-size: 11px; color: var(--gray-500); margin-top: 2px; }
  .vehicle-card .v-fare {
    font-size: 16px;
    font-weight: 800;
    color: var(--green);
    font-family: 'Syne', sans-serif;
    margin-top: 8px;
  }
  .vehicle-card .v-time { font-size: 11px; color: var(--gray-500); }

  /* Map placeholder */
  .map-placeholder {
    background: linear-gradient(135deg, #1a2e1a 0%, #0d1f0d 100%);
    border-radius: var(--radius);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 500px;
    position: relative;
    overflow: hidden;
    border: 1px solid rgba(0,200,111,0.2);
  }
  .map-grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,200,111,0.05) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,200,111,0.05) 1px, transparent 1px);
    background-size: 40px 40px;
  }
  .map-marker {
    position: absolute;
    font-size: 32px;
    filter: drop-shadow(0 4px 8px rgba(0,0,0,0.5));
    animation: bounce 2s ease-in-out infinite;
  }
  @keyframes bounce {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }
  .map-route {
    position: absolute;
    width: 3px;
    background: var(--green);
    border-radius: 2px;
    opacity: 0.7;
  }
  .map-info {
    position: relative;
    z-index: 2;
    text-align: center;
    color: rgba(255,255,255,0.5);
  }

  /* Ride status card */
  .ride-status-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow-lg);
    border: 1px solid var(--gray-100);
  }
  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 6px 14px;
    border-radius: 100px;
    font-size: 13px;
    font-weight: 600;
  }
  .status-badge.searching { background: rgba(245,158,11,0.12); color: var(--amber); }
  .status-badge.accepted { background: rgba(59,130,246,0.12); color: var(--blue); }
  .status-badge.started { background: rgba(0,200,111,0.12); color: var(--green); }
  .status-badge.completed { background: rgba(0,200,111,0.12); color: var(--green); }
  .status-badge.cancelled { background: rgba(239,68,68,0.12); color: var(--red); }
  .status-dot { width: 8px; height: 8px; border-radius: 50%; background: currentColor; }
  .pulse { animation: pulse 1.5s ease-in-out infinite; }
  @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }

  /* OTP display */
  .otp-display {
    background: var(--gray-900);
    color: var(--green);
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    letter-spacing: 12px;
    text-align: center;
    padding: 20px;
    border-radius: 12px;
    margin: 16px 0;
  }

  /* Driver card */
  .driver-info {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 20px;
    background: var(--gray-100);
    border-radius: 12px;
    margin: 16px 0;
  }
  .driver-avatar {
    width: 56px; height: 56px;
    background: var(--green);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px;
    font-weight: 800;
    font-family: 'Syne', sans-serif;
    color: var(--black);
    flex-shrink: 0;
  }
  .driver-details .name { font-size: 16px; font-weight: 700; }
  .driver-details .vehicle { font-size: 13px; color: var(--gray-500); margin-top: 2px; }
  .driver-details .rating {
    display: flex; align-items: center; gap: 4px;
    font-size: 13px; font-weight: 600; color: var(--amber);
    margin-top: 4px;
  }

  /* Ride history table */
  .rides-table { width: 100%; border-collapse: collapse; }
  .rides-table th {
    text-align: left;
    font-size: 12px;
    font-weight: 600;
    color: var(--gray-500);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    padding: 10px 16px;
    border-bottom: 1px solid var(--gray-100);
  }
  .rides-table td {
    padding: 14px 16px;
    font-size: 14px;
    border-bottom: 1px solid var(--gray-100);
    vertical-align: middle;
  }
  .rides-table tr:last-child td { border-bottom: none; }
  .rides-table tr:hover td { background: var(--gray-100); }
  .ride-id-col { font-family: monospace; font-size: 12px; color: var(--gray-500); }
  .fare-col { font-weight: 700; color: var(--green); font-family: 'Syne', sans-serif; }

  /* Profile */
  .profile-header {
    background: linear-gradient(135deg, var(--black), var(--gray-900));
    border-radius: var(--radius);
    padding: 32px;
    color: var(--white);
    display: flex;
    align-items: center;
    gap: 24px;
    margin-bottom: 24px;
  }
  .profile-avatar {
    width: 80px; height: 80px;
    background: var(--green);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 32px;
    font-weight: 800;
    font-family: 'Syne', sans-serif;
    color: var(--black);
    flex-shrink: 0;
  }
  .profile-info h3 { font-size: 22px; }
  .profile-info p { color: rgba(255,255,255,0.6); margin-top: 4px; }
  .profile-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(0,200,111,0.2);
    color: var(--green);
    border: 1px solid rgba(0,200,111,0.3);
    border-radius: 100px;
    padding: 4px 12px;
    font-size: 12px;
    font-weight: 600;
    margin-top: 8px;
  }

  /* Toast */
  .toast-container {
    position: fixed;
    bottom: 24px;
    right: 24px;
    z-index: 9999;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .toast {
    background: var(--gray-900);
    color: var(--white);
    padding: 14px 20px;
    border-radius: 12px;
    font-size: 14px;
    max-width: 360px;
    display: flex;
    align-items: center;
    gap: 12px;
    box-shadow: var(--shadow-lg);
    animation: slideIn 0.3s ease;
    border-left: 4px solid var(--green);
  }
  .toast.error { border-left-color: var(--red); }
  .toast.info { border-left-color: var(--blue); }
  @keyframes slideIn { from { transform: translateX(100%); opacity: 0; } to { transform: translateX(0); opacity: 1; } }

  /* Loading */
  .spinner {
    width: 24px; height: 24px;
    border: 3px solid rgba(0,200,111,0.2);
    border-top-color: var(--green);
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
    display: inline-block;
  }
  @keyframes spin { to { transform: rotate(360deg); } }

  /* Tabs */
  .tabs {
    display: flex;
    gap: 4px;
    background: var(--gray-100);
    padding: 4px;
    border-radius: 10px;
    margin-bottom: 24px;
  }
  .tab {
    flex: 1;
    padding: 10px 16px;
    border: none;
    background: none;
    border-radius: 8px;
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    font-weight: 500;
    color: var(--gray-500);
    cursor: pointer;
    transition: all 0.2s;
  }
  .tab.active {
    background: var(--white);
    color: var(--gray-900);
    font-weight: 600;
    box-shadow: 0 1px 4px rgba(0,0,0,0.1);
  }

  /* Driver dashboard specific */
  .driver-status-toggle {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 20px;
    background: var(--white);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    margin-bottom: 24px;
  }
  .toggle-switch {
    width: 56px; height: 30px;
    background: var(--gray-300);
    border-radius: 15px;
    position: relative;
    cursor: pointer;
    transition: background 0.3s;
    border: none;
  }
  .toggle-switch.on { background: var(--green); }
  .toggle-knob {
    position: absolute;
    top: 3px; left: 3px;
    width: 24px; height: 24px;
    background: white;
    border-radius: 50%;
    transition: transform 0.3s;
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
  }
  .toggle-switch.on .toggle-knob { transform: translateX(26px); }

  /* Notification item */
  .notif-item {
    display: flex;
    gap: 14px;
    padding: 16px 0;
    border-bottom: 1px solid var(--gray-100);
  }
  .notif-icon {
    width: 40px; height: 40px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
  }
  .notif-text .title { font-size: 14px; font-weight: 600; }
  .notif-text .time { font-size: 12px; color: var(--gray-500); margin-top: 2px; }

  /* Responsive */
  @media (max-width: 1024px) {
    .hero { grid-template-columns: 1fr; padding: 48px 24px; }
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .booking-layout { grid-template-columns: 1fr; }
    .features-grid { grid-template-columns: 1fr 1fr; }
    .dashboard { grid-template-columns: 1fr; }
    .sidebar { display: none; }
  }

  .hidden { display: none !important; }
  .flex { display: flex; }
  .items-center { align-items: center; }
  .justify-between { justify-content: space-between; }
  .gap-2 { gap: 8px; }
  .gap-3 { gap: 12px; }
  .gap-4 { gap: 16px; }
  .mt-2 { margin-top: 8px; }
  .mt-4 { margin-top: 16px; }
  .mb-4 { margin-bottom: 16px; }
  .text-sm { font-size: 13px; }
  .text-gray { color: var(--gray-500); }
  .text-green { color: var(--green); }
  .font-bold { font-weight: 700; }
  .w-full { width: 100%; }
  .divider { border: none; border-top: 1px solid var(--gray-100); margin: 16px 0; }
</style>
</head>
<body>

<div id="app" class="app">
  <!-- NAV -->
  <nav id="main-nav">
    <a class="logo" href="#" onclick="showScreen('home')">
      <div class="logo-icon">🚗</div>
      Safe<span class="logo-dot">Ride</span>
    </a>
    <div class="nav-links" id="nav-guest">
      <button class="nav-btn" onclick="showScreen('home')">Home</button>
      <button class="nav-btn" onclick="showScreen('login')">Sign In</button>
      <button class="nav-btn primary" onclick="showScreen('register')">Get Started</button>
    </div>
    <div class="nav-links hidden" id="nav-user">
      <div class="nav-user">
        <div class="nav-avatar" id="nav-avatar-text">U</div>
        <span id="nav-user-name">User</span>
        <button class="nav-btn" onclick="logout()">Sign Out</button>
      </div>
    </div>
  </nav>

  <!-- TOAST -->
  <div class="toast-container" id="toasts"></div>

  <!-- ===== HOME SCREEN ===== -->
  <div class="screen active" id="screen-home">
    <section class="hero">
      <div>
        <div class="hero-badge">⚡ Now Available in 50+ Cities</div>
        <h1>Your Safety,<br>Our <span>Priority</span></h1>
        <p>SafeRide connects you with verified, professional drivers for a comfortable, safe, and affordable ride — anytime, anywhere.</p>
        <div class="hero-actions">
          <button class="btn btn-primary" onclick="showScreen('register')">🚗 Book a Ride</button>
          <button class="btn btn-outline" onclick="showScreen('register')">🏍 Become a Driver</button>
        </div>
      </div>
      <div class="hero-card">
        <h3>⚡ Quick Book</h3>
        <div class="form-group">
          <div class="location-row">
            <div class="location-dot pickup"></div>
            <input class="form-input" placeholder="Pickup location" style="flex:1">
          </div>
          <div class="location-row">
            <div class="location-dot drop"></div>
            <input class="form-input" placeholder="Drop location" style="flex:1">
          </div>
        </div>
        <button class="btn btn-primary w-full" onclick="showScreen('register')" style="justify-content:center">Find Rides →</button>
        <div class="hero-stats">
          <div class="hero-stat"><div class="num">2M+</div><div class="lbl">Happy Riders</div></div>
          <div class="hero-stat"><div class="num">50K+</div><div class="lbl">Drivers</div></div>
          <div class="hero-stat"><div class="num">4.8★</div><div class="lbl">App Rating</div></div>
        </div>
      </div>
    </section>

    <section class="features">
      <div class="section-label">Why SafeRide</div>
      <h2 class="section-title">Rides You Can Trust</h2>
      <p class="section-sub">Every driver verified. Every ride tracked. Your safety is always our #1 priority.</p>
      <div class="features-grid">
        <div class="feature-card">
          <div class="feature-icon" style="background:#E6FAF1">🛡️</div>
          <h4>Verified Drivers</h4>
          <p>Background checks, license verification, and vehicle inspection for every driver before they join SafeRide.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon" style="background:#EFF6FF">📍</div>
          <h4>Live GPS Tracking</h4>
          <p>Share your live location with family and friends. Know exactly where your driver is at all times.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon" style="background:#FEF3C7">⚡</div>
          <h4>Fast Pickup</h4>
          <p>Our intelligent matching system connects you with the nearest available driver in under 3 minutes.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon" style="background:#FCE7F3">💳</div>
          <h4>Multiple Payments</h4>
          <p>Pay by cash, UPI, wallet, or card. Completely hassle-free with instant digital receipts.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon" style="background:#ECFDF5">🌟</div>
          <h4>Ride Quality Rating</h4>
          <p>Rate every ride. Our quality control ensures consistently high standards across all drivers.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon" style="background:#F5F3FF">🚗</div>
          <h4>5 Vehicle Types</h4>
          <p>From budget bikes to premium SUVs — choose the ride that fits your mood and pocket.</p>
        </div>
      </div>
    </section>
  </div>

  <!-- ===== LOGIN SCREEN ===== -->
  <div class="screen" id="screen-login">
    <div class="auth-screen">
      <div class="auth-card">
        <div style="text-align:center;margin-bottom:24px">
          <div style="font-size:40px;margin-bottom:12px">🚗</div>
          <h2>Welcome Back</h2>
          <p class="sub">Sign in to continue your SafeRide journey</p>
        </div>
        <div class="form-group">
          <label class="form-label">Email or Phone</label>
          <input class="form-input" id="login-identifier" type="text" placeholder="your@email.com or 9876543210">
        </div>
        <div class="form-group">
          <label class="form-label">Password</label>
          <input class="form-input" id="login-password" type="password" placeholder="••••••••">
        </div>
        <button class="form-submit" id="login-btn" onclick="doLogin()">Sign In →</button>
        <div style="text-align:center;margin-top:16px">
          <p class="text-sm text-gray">Demo: <strong>arjun@example.com</strong> / <strong>rider123</strong></p>
          <p class="text-sm text-gray mt-2">Driver: <strong>ravi@example.com</strong> / <strong>driver123</strong></p>
        </div>
        <div class="form-switch">Don't have an account? <a onclick="showScreen('register')">Create one</a></div>
      </div>
    </div>
  </div>

  <!-- ===== REGISTER SCREEN ===== -->
  <div class="screen" id="screen-register">
    <div class="auth-screen">
      <div class="auth-card">
        <div style="text-align:center;margin-bottom:24px">
          <div style="font-size:40px;margin-bottom:12px">🛡️</div>
          <h2>Join SafeRide</h2>
          <p class="sub">Create your account to get started</p>
        </div>
        <div class="role-toggle" id="role-toggle">
          <div class="role-option selected" onclick="selectRole('RIDER',this)">
            <div class="role-icon">🧑‍💼</div>
            <div class="role-name">I'm a Rider</div>
          </div>
          <div class="role-option" onclick="selectRole('DRIVER',this)">
            <div class="role-icon">🚗</div>
            <div class="role-name">I'm a Driver</div>
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Full Name</label>
          <input class="form-input" id="reg-name" type="text" placeholder="Your full name">
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input class="form-input" id="reg-email" type="email" placeholder="your@email.com">
        </div>
        <div class="form-group">
          <label class="form-label">Phone Number</label>
          <input class="form-input" id="reg-phone" type="tel" placeholder="9876543210">
        </div>
        <div class="form-group">
          <label class="form-label">Password</label>
          <input class="form-input" id="reg-password" type="password" placeholder="Min 6 characters">
        </div>
        <button class="form-submit" id="register-btn" onclick="doRegister()">Create Account →</button>
        <div class="form-switch">Already a member? <a onclick="showScreen('login')">Sign in</a></div>
      </div>
    </div>
  </div>

  <!-- ===== RIDER DASHBOARD ===== -->
  <div class="screen" id="screen-rider">
    <div class="dashboard">
      <aside class="sidebar">
        <button class="sidebar-item active" onclick="showPanel('panel-book')">
          <span class="icon">🚗</span> Book a Ride
        </button>
        <button class="sidebar-item" onclick="showPanel('panel-history')">
          <span class="icon">📋</span> My Rides
        </button>
        <button class="sidebar-item" onclick="showPanel('panel-profile')">
          <span class="icon">👤</span> Profile
        </button>
        <button class="sidebar-item" onclick="showPanel('panel-wallet')">
          <span class="icon">💰</span> Wallet
        </button>
        <button class="sidebar-item" onclick="showPanel('panel-notifications')">
          <span class="icon">🔔</span> Notifications
        </button>
        <div class="sidebar-bottom">
          <div style="padding:12px;background:rgba(0,200,111,0.1);border-radius:10px;margin-bottom:8px">
            <div style="color:rgba(255,255,255,0.5);font-size:11px;margin-bottom:4px">WALLET BALANCE</div>
            <div style="color:#00C86F;font-size:20px;font-weight:800;font-family:'Syne',sans-serif" id="sidebar-wallet">₹500.00</div>
          </div>
          <button class="sidebar-item" onclick="logout()">
            <span class="icon">🚪</span> Sign Out
          </button>
        </div>
      </aside>

      <main class="main-content">
        <!-- BOOK RIDE PANEL -->
        <div id="panel-book">
          <div class="page-header">
            <h2>Book a Ride</h2>
            <p>Where would you like to go today?</p>
          </div>
          <div class="booking-layout">
            <div class="booking-panel">
              <div class="location-input-group">
                <h3>📍 Your Route</h3>
                <div class="location-row">
                  <div class="location-dot pickup"></div>
                  <input class="form-input" id="pickup-addr" placeholder="Pickup location" value="Hitech City, Hyderabad">
                </div>
                <div style="margin-left:5px;height:20px;border-left:2px dashed #D1D5DB"></div>
                <div class="location-row">
                  <div class="location-dot drop"></div>
                  <input class="form-input" id="drop-addr" placeholder="Drop location" value="Charminar, Hyderabad">
                </div>
                <div class="divider"></div>
                <div class="flex gap-2">
                  <select class="form-select" id="payment-method">
                    <option value="CASH">💵 Cash</option>
                    <option value="UPI">📱 UPI</option>
                    <option value="WALLET">👛 Wallet</option>
                    <option value="CARD">💳 Card</option>
                  </select>
                </div>
              </div>

              <div class="card">
                <div class="card-header">
                  <div class="card-title">🚗 Choose Vehicle</div>
                  <span class="text-sm text-gray">Surge: 1.0×</span>
                </div>
                <div class="vehicle-grid" id="vehicle-grid">
                  <div class="vehicle-card selected" onclick="selectVehicle('BIKE',this)">
                    <div class="v-icon">🏍</div>
                    <div class="v-name">SafeBike</div>
                    <div class="v-desc">Quick & affordable</div>
                    <div class="v-fare">₹86</div>
                    <div class="v-time">~12 min</div>
                  </div>
                  <div class="vehicle-card" onclick="selectVehicle('AUTO',this)">
                    <div class="v-icon">🛺</div>
                    <div class="v-name">SafeAuto</div>
                    <div class="v-desc">Comfortable auto</div>
                    <div class="v-fare">₹118</div>
                    <div class="v-time">~14 min</div>
                  </div>
                  <div class="vehicle-card" onclick="selectVehicle('MINI',this)">
                    <div class="v-icon">🚗</div>
                    <div class="v-name">SafeMini</div>
                    <div class="v-desc">Budget hatchback</div>
                    <div class="v-fare">₹142</div>
                    <div class="v-time">~12 min</div>
                  </div>
                  <div class="vehicle-card" onclick="selectVehicle('SEDAN',this)">
                    <div class="v-icon">🚙</div>
                    <div class="v-name">SafeSedan</div>
                    <div class="v-desc">Premium experience</div>
                    <div class="v-fare">₹178</div>
                    <div class="v-time">~12 min</div>
                  </div>
                  <div class="vehicle-card" onclick="selectVehicle('SUV',this)">
                    <div class="v-icon">🚐</div>
                    <div class="v-name">SafeSUV</div>
                    <div class="v-desc">Spacious for groups</div>
                    <div class="v-fare">₹214</div>
                    <div class="v-time">~12 min</div>
                  </div>
                </div>
                <button class="btn btn-primary w-full mt-4" style="justify-content:center;font-size:16px" onclick="bookRide()">
                  🚀 Book SafeBike – ₹86
                </button>
              </div>
            </div>

            <!-- MAP -->
            <div>
              <div class="map-placeholder" id="map-area">
                <div class="map-grid"></div>
                <div class="map-marker" style="top:30%;left:35%">📍</div>
                <div class="map-marker" style="top:65%;left:55%;animation-delay:0.5s">🏁</div>
                <div style="position:absolute;top:30%;left:37%;width:2px;height:35%;background:linear-gradient(to bottom,#00C86F,#EF4444);border-radius:2px;z-index:1"></div>
                <div class="map-info" style="position:absolute;bottom:24px;left:0;right:0">
                  <div style="font-size:13px;color:rgba(255,255,255,0.4)">🗺 Interactive map with Google Maps API</div>
                  <div style="font-size:11px;color:rgba(255,255,255,0.25);margin-top:4px">Configure GOOGLE_MAPS_API_KEY in application.properties</div>
                </div>

                <!-- Active ride overlay -->
                <div id="active-ride-overlay" class="hidden" style="position:absolute;bottom:0;left:0;right:0;background:rgba(10,10,10,0.95);backdrop-filter:blur(12px);border-radius:0 0 16px 16px;padding:24px">
                  <div id="active-ride-content"></div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- HISTORY PANEL -->
        <div id="panel-history" class="hidden">
          <div class="page-header">
            <h2>My Rides</h2>
            <p>Your complete ride history</p>
          </div>
          <div class="card">
            <div class="tabs">
              <button class="tab active">All Rides</button>
              <button class="tab">Completed</button>
              <button class="tab">Cancelled</button>
            </div>
            <table class="rides-table">
              <thead>
                <tr>
                  <th>Ride ID</th>
                  <th>Route</th>
                  <th>Vehicle</th>
                  <th>Fare</th>
                  <th>Status</th>
                  <th>Date</th>
                </tr>
              </thead>
              <tbody id="history-tbody">
                <tr><td colspan="6" style="text-align:center;padding:40px;color:var(--gray-500)">No rides yet. Book your first SafeRide!</td></tr>
              </tbody>
            </table>
          </div>
        </div>

        <!-- PROFILE PANEL -->
        <div id="panel-profile" class="hidden">
          <div class="page-header">
            <h2>My Profile</h2>
            <p>Manage your account details</p>
          </div>
          <div class="profile-header">
            <div class="profile-avatar" id="profile-avatar">A</div>
            <div class="profile-info">
              <h3 id="profile-name">Loading...</h3>
              <p id="profile-email">loading@email.com</p>
              <div class="profile-badge">✅ Verified Rider</div>
            </div>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px">
            <div class="card">
              <div class="card-title mb-4">Account Details</div>
              <div class="form-group">
                <label class="form-label">Full Name</label>
                <input class="form-input" id="profile-name-input" type="text">
              </div>
              <div class="form-group">
                <label class="form-label">Email</label>
                <input class="form-input" id="profile-email-input" type="email">
              </div>
              <div class="form-group">
                <label class="form-label">Phone</label>
                <input class="form-input" id="profile-phone-input" type="tel">
              </div>
              <button class="btn btn-primary" onclick="showToast('Profile updated successfully!','success')">Save Changes</button>
            </div>
            <div>
              <div class="stats-grid" style="grid-template-columns:1fr 1fr">
                <div class="stat-card">
                  <div class="stat-icon" style="background:#E6FAF1">🚗</div>
                  <div class="stat-value" id="profile-rides">0</div>
                  <div class="stat-label">Total Rides</div>
                </div>
                <div class="stat-card">
                  <div class="stat-icon" style="background:#FEF3C7">⭐</div>
                  <div class="stat-value">4.8</div>
                  <div class="stat-label">Your Rating</div>
                </div>
              </div>
              <div class="card">
                <div class="card-title mb-4">Preferences</div>
                <div class="form-group">
                  <label class="form-label">Default Payment</label>
                  <select class="form-select">
                    <option>💵 Cash</option>
                    <option>📱 UPI</option>
                    <option>💳 Card</option>
                  </select>
                </div>
                <div class="form-group">
                  <label class="form-label">Language</label>
                  <select class="form-select">
                    <option>English</option>
                    <option>हिंदी</option>
                    <option>తెలుగు</option>
                  </select>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- WALLET PANEL -->
        <div id="panel-wallet" class="hidden">
          <div class="page-header">
            <h2>SafeRide Wallet</h2>
            <p>Manage your balance and transactions</p>
          </div>
          <div style="display:grid;grid-template-columns:1fr 2fr;gap:24px">
            <div>
              <div class="card" style="background:linear-gradient(135deg,#0A0A0A,#1F2937);color:white;border-color:transparent">
                <div style="color:rgba(255,255,255,0.5);font-size:13px;margin-bottom:8px">Current Balance</div>
                <div style="font-size:40px;font-weight:800;font-family:'Syne',sans-serif;color:var(--green)" id="wallet-balance-display">₹500.00</div>
                <div style="color:rgba(255,255,255,0.4);font-size:12px;margin-top:8px">SafeRide Wallet</div>
              </div>
              <div class="card">
                <div class="card-title mb-4">Add Money</div>
                <div class="form-group">
                  <label class="form-label">Amount (₹)</label>
                  <input class="form-input" id="add-money-amt" type="number" placeholder="100" min="1">
                </div>
                <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:16px">
                  <button class="btn btn-dark btn-sm" onclick="setAmount(100)">₹100</button>
                  <button class="btn btn-dark btn-sm" onclick="setAmount(200)">₹200</button>
                  <button class="btn btn-dark btn-sm" onclick="setAmount(500)">₹500</button>
                </div>
                <button class="btn btn-primary w-full" style="justify-content:center" onclick="addMoney()">Add to Wallet</button>
              </div>
            </div>
            <div class="card">
              <div class="card-title mb-4">Transaction History</div>
              <div id="txn-list">
                <div class="notif-item">
                  <div class="notif-icon" style="background:#E6FAF1">💰</div>
                  <div class="notif-text">
                    <div class="title">Wallet topped up</div>
                    <div class="time">+₹500.00 · 2 days ago</div>
                  </div>
                  <div style="margin-left:auto;color:var(--green);font-weight:700">+₹500</div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- NOTIFICATIONS PANEL -->
        <div id="panel-notifications" class="hidden">
          <div class="page-header">
            <h2>Notifications</h2>
            <p>Stay updated with your ride activity</p>
          </div>
          <div class="card">
            <div id="notif-list">
              <div class="notif-item">
                <div class="notif-icon" style="background:#E6FAF1;font-size:20px">🎉</div>
                <div class="notif-text">
                  <div class="title">Welcome to SafeRide!</div>
                  <div class="time">Your account was created successfully · Just now</div>
                </div>
              </div>
              <div class="notif-item">
                <div class="notif-icon" style="background:#EFF6FF;font-size:20px">💰</div>
                <div class="notif-text">
                  <div class="title">₹50 Cashback Credited</div>
                  <div class="time">Use code SAFE50 on your first ride · 1 day ago</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>

  <!-- ===== DRIVER DASHBOARD ===== -->
  <div class="screen" id="screen-driver">
    <div class="dashboard">
      <aside class="sidebar">
        <button class="sidebar-item active" onclick="showDriverPanel('dpanel-home')">
          <span class="icon">🏠</span> Dashboard
        </button>
        <button class="sidebar-item" onclick="showDriverPanel('dpanel-earnings')">
          <span class="icon">💵</span> Earnings
        </button>
        <button class="sidebar-item" onclick="showDriverPanel('dpanel-rides')">
          <span class="icon">📋</span> Ride History
        </button>
        <button class="sidebar-item" onclick="showDriverPanel('dpanel-profile')">
          <span class="icon">👤</span> Profile
        </button>
        <div class="sidebar-bottom">
          <div style="padding:12px;background:rgba(0,200,111,0.1);border-radius:10px;margin-bottom:8px">
            <div style="color:rgba(255,255,255,0.5);font-size:11px;margin-bottom:4px">TODAY'S EARNINGS</div>
            <div style="color:#00C86F;font-size:20px;font-weight:800;font-family:'Syne',sans-serif" id="driver-sidebar-earnings">₹0.00</div>
          </div>
          <button class="sidebar-item" onclick="logout()">
            <span class="icon">🚪</span> Sign Out
          </button>
        </div>
      </aside>

      <main class="main-content">
        <!-- DRIVER HOME -->
        <div id="dpanel-home">
          <div class="page-header flex justify-between items-center">
            <div>
              <h2>Driver Dashboard</h2>
              <p id="driver-welcome-msg">Good morning! Ready to earn?</p>
            </div>
          </div>

          <div class="driver-status-toggle">
            <button class="toggle-switch" id="driver-toggle" onclick="toggleDriverStatus()">
              <div class="toggle-knob"></div>
            </button>
            <div>
              <div style="font-weight:600" id="driver-status-text">Go Online</div>
              <div class="text-sm text-gray">Toggle to start accepting rides</div>
            </div>
            <div id="driver-online-badge" class="status-badge hidden" style="margin-left:auto">
              <div class="status-dot pulse"></div>
              <span>Online</span>
            </div>
          </div>

          <div class="stats-grid">
            <div class="stat-card">
              <div class="stat-icon" style="background:#E6FAF1">💵</div>
              <div class="stat-value" id="drv-earnings">₹0</div>
              <div class="stat-label">Today's Earnings</div>
            </div>
            <div class="stat-card">
              <div class="stat-icon" style="background:#EFF6FF">🚗</div>
              <div class="stat-value" id="drv-rides">0</div>
              <div class="stat-label">Today's Rides</div>
            </div>
            <div class="stat-card">
              <div class="stat-icon" style="background:#FEF3C7">⭐</div>
              <div class="stat-value">4.8</div>
              <div class="stat-label">Your Rating</div>
            </div>
            <div class="stat-card">
              <div class="stat-icon" style="background:#FCE7F3">⏱</div>
              <div class="stat-value" id="drv-hours">0h</div>
              <div class="stat-label">Hours Online</div>
            </div>
          </div>

          <!-- Incoming Ride Request -->
          <div id="ride-request-card" class="hidden">
            <div class="card" style="border:2px solid var(--green);animation:pulse 1.5s infinite">
              <div class="card-header">
                <div class="card-title">🚨 New Ride Request!</div>
                <span class="status-badge searching"><div class="status-dot pulse"></div>New</span>
              </div>
              <div id="ride-request-details"></div>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:16px">
                <button class="btn btn-danger" onclick="rejectRide()">✕ Decline</button>
                <button class="btn btn-primary" onclick="acceptRide()" style="justify-content:center">✓ Accept</button>
              </div>
            </div>
          </div>

          <!-- Active Trip -->
          <div id="active-trip-card" class="hidden">
            <div class="card" style="border:2px solid var(--blue)">
              <div class="card-header">
                <div class="card-title">🚗 Active Trip</div>
                <span class="status-badge accepted" id="active-trip-status">Accepted</span>
              </div>
              <div id="active-trip-details"></div>
            </div>
          </div>
        </div>

        <!-- DRIVER EARNINGS -->
        <div id="dpanel-earnings" class="hidden">
          <div class="page-header"><h2>Earnings</h2><p>Track your daily and weekly earnings</p></div>
          <div class="stats-grid" style="grid-template-columns:repeat(3,1fr)">
            <div class="stat-card">
              <div class="stat-icon" style="background:#E6FAF1">📅</div>
              <div class="stat-value" id="weekly-earn">₹0</div>
              <div class="stat-label">This Week</div>
            </div>
            <div class="stat-card">
              <div class="stat-icon" style="background:#EFF6FF">📆</div>
              <div class="stat-value" id="monthly-earn">₹0</div>
              <div class="stat-label">This Month</div>
            </div>
            <div class="stat-card">
              <div class="stat-icon" style="background:#FEF3C7">🏆</div>
              <div class="stat-value" id="total-earn">₹0</div>
              <div class="stat-label">Total Earned</div>
            </div>
          </div>
          <div class="card">
            <div class="card-title mb-4">Earnings Breakdown</div>
            <div style="height:200px;display:flex;align-items:flex-end;gap:12px;padding:16px 0;border-bottom:2px solid var(--gray-100)">
              <div style="display:flex;flex-direction:column;align-items:center;gap:8px;flex:1" id="earnings-chart">
                <div style="text-align:center;color:var(--gray-500);font-size:13px">Start accepting rides to see earnings chart</div>
              </div>
            </div>
          </div>
        </div>

        <!-- DRIVER RIDES -->
        <div id="dpanel-rides" class="hidden">
          <div class="page-header"><h2>Ride History</h2><p>All completed and cancelled trips</p></div>
          <div class="card">
            <table class="rides-table">
              <thead>
                <tr>
                  <th>Ride ID</th><th>Passenger</th><th>Route</th><th>Fare</th><th>Status</th><th>Date</th>
                </tr>
              </thead>
              <tbody id="driver-history-tbody">
                <tr><td colspan="6" style="text-align:center;padding:40px;color:var(--gray-500)">No rides yet. Go online to start accepting rides!</td></tr>
              </tbody>
            </table>
          </div>
        </div>

        <!-- DRIVER PROFILE -->
        <div id="dpanel-profile" class="hidden">
          <div class="page-header"><h2>Driver Profile</h2></div>
          <div class="profile-header">
            <div class="profile-avatar" id="driver-profile-avatar">D</div>
            <div class="profile-info">
              <h3 id="driver-profile-name">Driver Name</h3>
              <p id="driver-profile-email">email@example.com</p>
              <div class="profile-badge">🚗 Verified Driver</div>
            </div>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px">
            <div class="card">
              <div class="card-title mb-4">Vehicle Information</div>
              <table style="width:100%;font-size:14px">
                <tr><td style="padding:8px 0;color:var(--gray-500)">Vehicle Type</td><td style="font-weight:600" id="drv-vehicle-type">Bike</td></tr>
                <tr><td style="padding:8px 0;color:var(--gray-500)">Vehicle Model</td><td style="font-weight:600" id="drv-vehicle-model">Honda Activa</td></tr>
                <tr><td style="padding:8px 0;color:var(--gray-500)">Vehicle Number</td><td style="font-weight:600" id="drv-vehicle-number">TS09EF5678</td></tr>
                <tr><td style="padding:8px 0;color:var(--gray-500)">License Number</td><td style="font-weight:600" id="drv-license">TS09AB1234</td></tr>
              </table>
            </div>
            <div class="card">
              <div class="card-title mb-4">Performance</div>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px">
                <div class="stat-card" style="padding:16px">
                  <div class="stat-value" style="font-size:22px">4.8⭐</div>
                  <div class="stat-label">Rating</div>
                </div>
                <div class="stat-card" style="padding:16px">
                  <div class="stat-value" style="font-size:22px" id="drv-total-rides">0</div>
                  <div class="stat-label">Total Rides</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</div>

<script>
// ============================================================
//  SafeRide Frontend Application
// ============================================================

const API_BASE = 'http://localhost:8080/api';

let state = {
  user: null,
  token: null,
  selectedVehicle: 'BIKE',
  selectedFare: 86,
  driverOnline: false,
  currentRide: null,
  driverRides: [],
  riderRides: [],
  walletBalance: 0
};

// ===== API CALLS =====
async function apiCall(method, path, body = null) {
  const headers = { 'Content-Type': 'application/json' };
  if (state.token) headers['Authorization'] = `Bearer ${state.token}`;
  try {
    const res = await fetch(`${API_BASE}${path}`, {
      method,
      headers,
      body: body ? JSON.stringify(body) : null
    });
    const data = await res.json();
    if (!data.success && data.message) throw new Error(data.message);
    return data;
  } catch (e) {
    if (e.message === 'Failed to fetch') {
      // API not running - use mock data
      return mockApiCall(method, path, body);
    }
    throw e;
  }
}

// ===== MOCK DATA (when backend not running) =====
let mockRideCounter = 1;
function mockApiCall(method, path, body) {
  if (path === '/auth/login') {
    const users = {
      'arjun@example.com': { id:1, name:'Arjun Sharma', email:'arjun@example.com', phone:'9876543210', role:'RIDER', rating:4.8, totalRides:12, walletBalance:500, isVerified:true },
      '9876543210': { id:1, name:'Arjun Sharma', email:'arjun@example.com', phone:'9876543210', role:'RIDER', rating:4.8, totalRides:12, walletBalance:500, isVerified:true },
      'ravi@example.com': { id:2, name:'Ravi Kumar', email:'ravi@example.com', phone:'9876543211', role:'DRIVER', rating:4.9, totalRides:234, walletBalance:0, isVerified:true },
      'admin@saferide.com': { id:3, name:'Admin', email:'admin@saferide.com', phone:'9000000000', role:'ADMIN', rating:5.0, totalRides:0, walletBalance:0, isVerified:true }
    };
    const user = users[body.identifier];
    if (!user || body.password.length < 4) return { success:false, message:'Invalid credentials' };
    return { success:true, data:{ accessToken:'mock_token_' + Date.now(), refreshToken:'mock_refresh', tokenType:'Bearer', user } };
  }
  if (path === '/auth/register') {
    return { success:true, data:{ accessToken:'mock_token_' + Date.now(), refreshToken:'mock_refresh', tokenType:'Bearer',
      user:{ id:99, name:body.name, email:body.email, phone:body.phone, role:body.role||'RIDER', rating:5.0, totalRides:0, walletBalance:0, isVerified:false }
    }};
  }
  if (path === '/rides/book') {
    const rideId = `SR-2024-${String(mockRideCounter++).padStart(5,'0')}`;
    return { success:true, data:{ rideId, status:'SEARCHING', estimatedFare:state.selectedFare, vehicleType:state.selectedVehicle, otp:'4782', pickupAddress:body.pickupAddress, dropAddress:body.dropAddress } };
  }
  return { success:true, data:{} };
}

// ===== SCREENS =====
function showScreen(name) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(`screen-${name}`)?.classList.add('active');
}

function showPanel(id) {
  document.querySelectorAll('#screen-rider .main-content > div').forEach(p => p.classList.add('hidden'));
  document.getElementById(id)?.classList.remove('hidden');
  document.querySelectorAll('.sidebar-item').forEach(b => b.classList.remove('active'));
  event?.currentTarget?.classList.add('active');
}

function showDriverPanel(id) {
  document.querySelectorAll('#screen-driver .main-content > div').forEach(p => p.classList.add('hidden'));
  document.getElementById(id)?.classList.remove('hidden');
  document.querySelectorAll('#screen-driver .sidebar-item').forEach(b => b.classList.remove('active'));
  event?.currentTarget?.classList.add('active');
}

// ===== AUTH =====
let selectedRole = 'RIDER';
function selectRole(role, el) {
  selectedRole = role;
  document.querySelectorAll('.role-option').forEach(e => e.classList.remove('selected'));
  el.classList.add('selected');
}

async function doLogin() {
  const identifier = document.getElementById('login-identifier').value.trim();
  const password = document.getElementById('login-password').value;
  if (!identifier || !password) return showToast('Please fill in all fields', 'error');

  const btn = document.getElementById('login-btn');
  btn.disabled = true;
  btn.innerHTML = '<span class="spinner"></span> Signing in...';
  try {
    const res = await apiCall('POST', '/auth/login', { identifier, password });
    if (res.data) {
      handleAuthSuccess(res.data);
    } else {
      showToast(res.message || 'Login failed', 'error');
    }
  } catch(e) {
    showToast(e.message || 'Login failed. Please try again.', 'error');
  } finally {
    btn.disabled = false;
    btn.innerHTML = 'Sign In →';
  }
}

async function doRegister() {
  const name = document.getElementById('reg-name').value.trim();
  const email = document.getElementById('reg-email').value.trim();
  const phone = document.getElementById('reg-phone').value.trim();
  const password = document.getElementById('reg-password').value;
  if (!name || !email || !phone || !password) return showToast('Please fill all fields', 'error');
  if (password.length < 6) return showToast('Password must be at least 6 characters', 'error');

  const btn = document.getElementById('register-btn');
  btn.disabled = true;
  btn.innerHTML = '<span class="spinner"></span> Creating account...';
  try {
    const res = await apiCall('POST', '/auth/register', { name, email, phone, password, role: selectedRole });
    if (res.data) {
      handleAuthSuccess(res.data);
    } else {
      showToast(res.message || 'Registration failed', 'error');
    }
  } catch(e) {
    showToast(e.message || 'Registration failed', 'error');
  } finally {
    btn.disabled = false;
    btn.innerHTML = 'Create Account →';
  }
}

function handleAuthSuccess(data) {
  state.user = data.user;
  state.token = data.accessToken;
  state.walletBalance = data.user.walletBalance || 0;
  showToast(`Welcome back, ${data.user.name}! 🎉`);
  updateNavForUser();
  if (data.user.role === 'RIDER') {
    showScreen('rider');
    populateRiderDashboard();
  } else if (data.user.role === 'DRIVER') {
    showScreen('driver');
    populateDriverDashboard();
  } else {
    showScreen('rider');
    populateRiderDashboard();
  }
}

function updateNavForUser() {
  document.getElementById('nav-guest').classList.add('hidden');
  document.getElementById('nav-user').classList.remove('hidden');
  document.getElementById('nav-avatar-text').textContent = state.user?.name?.[0]?.toUpperCase() || 'U';
  document.getElementById('nav-user-name').textContent = state.user?.name || 'User';
}

function logout() {
  state = { user:null, token:null, selectedVehicle:'BIKE', selectedFare:86, driverOnline:false, currentRide:null, driverRides:[], riderRides:[], walletBalance:0 };
  document.getElementById('nav-guest').classList.remove('hidden');
  document.getElementById('nav-user').classList.add('hidden');
  showScreen('home');
  showToast('Signed out successfully. See you soon!', 'info');
}

// ===== RIDER DASHBOARD =====
function populateRiderDashboard() {
  const u = state.user;
  if (!u) return;
  document.getElementById('profile-name').textContent = u.name;
  document.getElementById('profile-email').textContent = u.email;
  document.getElementById('profile-avatar').textContent = u.name[0];
  document.getElementById('profile-rides').textContent = u.totalRides;
  document.getElementById('profile-name-input').value = u.name;
  document.getElementById('profile-email-input').value = u.email;
  document.getElementById('profile-phone-input').value = u.phone;
  document.getElementById('sidebar-wallet').textContent = `₹${(u.walletBalance||0).toFixed(2)}`;
  document.getElementById('wallet-balance-display').textContent = `₹${(u.walletBalance||0).toFixed(2)}`;
}

// ===== VEHICLE SELECTION =====
const vehicleData = {
  BIKE: { icon:'🏍', name:'SafeBike', fare:86, time:'12 min' },
  AUTO: { icon:'🛺', name:'SafeAuto', fare:118, time:'14 min' },
  MINI: { icon:'🚗', name:'SafeMini', fare:142, time:'12 min' },
  SEDAN: { icon:'🚙', name:'SafeSedan', fare:178, time:'12 min' },
  SUV: { icon:'🚐', name:'SafeSUV', fare:214, time:'15 min' }
};

function selectVehicle(type, el) {
  state.selectedVehicle = type;
  state.selectedFare = vehicleData[type].fare;
  document.querySelectorAll('.vehicle-card').forEach(c => c.classList.remove('selected'));
  el.classList.add('selected');
  const v = vehicleData[type];
  document.querySelector('#panel-book .btn-primary[onclick="bookRide()"]').textContent =
    `🚀 Book ${v.name} – ₹${v.fare}`;
}

// ===== RIDE BOOKING =====
async function bookRide() {
  const pickup = document.getElementById('pickup-addr').value.trim();
  const drop = document.getElementById('drop-addr').value.trim();
  if (!pickup || !drop) return showToast('Please enter pickup and drop locations', 'error');
  if (!state.user) return showScreen('login');

  try {
    showToast('🔍 Finding nearby drivers...', 'info');
    const res = await apiCall('POST', '/rides/book', {
      pickupAddress: pickup,
      pickupLatitude: 17.3850, pickupLongitude: 78.4867,
      dropAddress: drop,
      dropLatitude: 17.3616, dropLongitude: 78.4747,
      vehicleType: state.selectedVehicle,
      paymentMethod: document.getElementById('payment-method').value
    });

    if (res.data || res.rideId) {
      const ride = res.data || res;
      state.currentRide = ride;
      state.riderRides.unshift(ride);
      showActiveRide(ride);
      setTimeout(() => simulateDriverFound(ride), 3000);
    }
  } catch(e) {
    showToast(e.message || 'Booking failed. Please try again.', 'error');
  }
}

function showActiveRide(ride) {
  const overlay = document.getElementById('active-ride-overlay');
  const content = document.getElementById('active-ride-content');
  overlay.classList.remove('hidden');
  content.innerHTML = `
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
      <span class="status-badge searching"><div class="status-dot pulse"></div>Searching for driver...</span>
      <span style="color:rgba(255,255,255,0.7);font-size:13px">${ride.rideId || 'SR-2024-00001'}</span>
    </div>
    <div style="color:white;font-size:15px;margin-bottom:16px">
      <div>📍 ${ride.pickupAddress || 'Pickup'}</div>
      <div style="margin:6px 0;color:rgba(255,255,255,0.4)">↓</div>
      <div>🏁 ${ride.dropAddress || 'Drop'}</div>
    </div>
    <div style="display:flex;justify-content:space-between;background:rgba(255,255,255,0.08);padding:12px;border-radius:10px">
      <div style="text-align:center">
        <div style="color:rgba(255,255,255,0.5);font-size:11px">FARE</div>
        <div style="color:#00C86F;font-weight:800;font-size:18px;font-family:'Syne',sans-serif">₹${ride.estimatedFare || state.selectedFare}</div>
      </div>
      <div style="text-align:center">
        <div style="color:rgba(255,255,255,0.5);font-size:11px">OTP</div>
        <div style="color:white;font-weight:800;font-size:18px;font-family:'Syne',sans-serif;letter-spacing:4px">${ride.otp || '4782'}</div>
      </div>
    </div>
    <button class="btn btn-danger btn-sm w-full mt-4" style="justify-content:center" onclick="cancelCurrentRide()">✕ Cancel Ride</button>
  `;
  showToast('🚗 Searching for a driver near you...', 'info');
}

function simulateDriverFound(ride) {
  const content = document.getElementById('active-ride-content');
  content.innerHTML = `
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
      <span class="status-badge accepted"><div class="status-dot"></div>Driver Found!</span>
      <span style="color:rgba(255,255,255,0.7);font-size:13px">${ride.rideId || 'SR-2024-00001'}</span>
    </div>
    <div style="display:flex;align-items:center;gap:14px;background:rgba(255,255,255,0.06);padding:16px;border-radius:12px;margin-bottom:12px">
      <div style="width:50px;height:50px;background:#00C86F;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:22px;font-weight:800;color:#000;font-family:'Syne',sans-serif">R</div>
      <div>
        <div style="color:white;font-weight:700">Ravi Kumar</div>
        <div style="color:rgba(255,255,255,0.5);font-size:13px">🏍 Honda Activa · TS09EF5678</div>
        <div style="color:#F59E0B;font-size:13px;font-weight:600">⭐ 4.8 · 234 rides</div>
      </div>
    </div>
    <div style="display:flex;justify-content:space-between;background:rgba(255,255,255,0.08);padding:12px;border-radius:10px;margin-bottom:12px">
      <div style="text-align:center">
        <div style="color:rgba(255,255,255,0.5);font-size:11px">YOUR OTP</div>
        <div style="color:#00C86F;font-weight:800;font-size:22px;font-family:'Syne',sans-serif;letter-spacing:6px">${ride.otp || '4782'}</div>
      </div>
      <div style="text-align:center">
        <div style="color:rgba(255,255,255,0.5);font-size:11px">ETA</div>
        <div style="color:white;font-weight:800;font-size:22px;font-family:'Syne',sans-serif">~3 min</div>
      </div>
      <div style="text-align:center">
        <div style="color:rgba(255,255,255,0.5);font-size:11px">FARE</div>
        <div style="color:#00C86F;font-weight:800;font-size:22px;font-family:'Syne',sans-serif">₹${ride.estimatedFare || state.selectedFare}</div>
      </div>
    </div>
    <div style="display:flex;gap:8px">
      <button class="btn btn-dark btn-sm" style="flex:1;justify-content:center">📞 Call Driver</button>
      <button class="btn btn-dark btn-sm" style="flex:1;justify-content:center">💬 Message</button>
      <button class="btn btn-danger btn-sm" style="flex:1;justify-content:center" onclick="cancelCurrentRide()">✕ Cancel</button>
    </div>
  `;
  showToast('✅ Driver found! Ravi Kumar is on the way!');
  // Update history
  updateRideHistory();
}

function cancelCurrentRide() {
  document.getElementById('active-ride-overlay').classList.add('hidden');
  state.currentRide = null;
  showToast('Ride cancelled.', 'info');
}

function updateRideHistory() {
  const tbody = document.getElementById('history-tbody');
  if (!state.riderRides.length) return;
  tbody.innerHTML = state.riderRides.map(r => `
    <tr>
      <td class="ride-id-col">${r.rideId || 'SR-2024-00001'}</td>
      <td>
        <div style="font-weight:500;font-size:13px">${(r.pickupAddress||'Hitech City').substring(0,20)}...</div>
        <div style="color:var(--gray-500);font-size:12px">→ ${(r.dropAddress||'Charminar').substring(0,20)}...</div>
      </td>
      <td><span style="background:var(--gray-100);padding:4px 10px;border-radius:100px;font-size:12px">${r.vehicleType||'BIKE'}</span></td>
      <td class="fare-col">₹${r.estimatedFare||86}</td>
      <td><span class="status-badge ${(r.status||'SEARCHING').toLowerCase()}" style="font-size:12px">${r.status||'SEARCHING'}</span></td>
      <td style="color:var(--gray-500);font-size:12px">Just now</td>
    </tr>
  `).join('');
}

// ===== DRIVER DASHBOARD =====
function populateDriverDashboard() {
  const u = state.user;
  if (!u) return;
  document.getElementById('driver-profile-name').textContent = u.name;
  document.getElementById('driver-profile-email').textContent = u.email;
  document.getElementById('driver-profile-avatar').textContent = u.name[0];
  const hour = new Date().getHours();
  const greeting = hour < 12 ? 'Good morning' : hour < 17 ? 'Good afternoon' : 'Good evening';
  document.getElementById('driver-welcome-msg').textContent = `${greeting}, ${u.name}! Ready to earn today?`;
}

let driverOnline = false;
let driverRideCount = 0;
let driverEarnings = 0;
let onlineHours = 0;
let onlineTimer = null;
let rideRequestTimeout = null;

function toggleDriverStatus() {
  driverOnline = !driverOnline;
  const toggle = document.getElementById('driver-toggle');
  const statusText = document.getElementById('driver-status-text');
  const badge = document.getElementById('driver-online-badge');
  toggle.classList.toggle('on', driverOnline);
  statusText.textContent = driverOnline ? 'You are Online' : 'Go Online';
  badge.classList.toggle('hidden', !driverOnline);
  badge.style.background = 'rgba(0,200,111,0.12)';
  badge.style.color = '#00C86F';
  if (driverOnline) {
    showToast('🟢 You are now online! Waiting for ride requests...');
    onlineTimer = setInterval(() => {
      onlineHours += 1/60;
      document.getElementById('drv-hours').textContent = onlineHours.toFixed(1) + 'h';
    }, 1000);
    // Simulate incoming ride after 5s
    rideRequestTimeout = setTimeout(simulateIncomingRide, 5000);
  } else {
    showToast('⚫ You are now offline.', 'info');
    clearInterval(onlineTimer);
    clearTimeout(rideRequestTimeout);
    document.getElementById('ride-request-card').classList.add('hidden');
  }
}

function simulateIncomingRide() {
  if (!driverOnline) return;
  const card = document.getElementById('ride-request-card');
  const details = document.getElementById('ride-request-details');
  details.innerHTML = `
    <div style="display:flex;align-items:center;gap:12px;margin-bottom:16px">
      <div style="width:44px;height:44px;background:var(--gray-100);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:20px;font-weight:700">A</div>
      <div>
        <div style="font-weight:700">Arjun Sharma</div>
        <div style="font-size:13px;color:var(--gray-500)">⭐ 4.8 · 12 rides</div>
      </div>
      <div style="margin-left:auto;text-align:right">
        <div style="font-size:22px;font-weight:800;color:var(--green);font-family:'Syne',sans-serif">₹86</div>
        <div style="font-size:12px;color:var(--gray-500)">~5.2 km</div>
      </div>
    </div>
    <div style="background:var(--gray-100);border-radius:10px;padding:14px">
      <div style="font-size:13px;margin-bottom:6px">📍 <strong>Hitech City, Hyderabad</strong></div>
      <div style="color:var(--gray-500);margin:4px 0">↓ 5.2 km · ~12 min</div>
      <div style="font-size:13px">🏁 <strong>Charminar, Old City</strong></div>
    </div>
    <div style="display:flex;gap:16px;margin-top:12px;font-size:13px">
      <span>💵 Cash Payment</span>
      <span>🏍 Bike Ride</span>
    </div>
  `;
  card.classList.remove('hidden');
  showToast('🚨 New ride request! Accept quickly!', 'info');
}

function acceptRide() {
  document.getElementById('ride-request-card').classList.add('hidden');
  driverRideCount++;
  driverEarnings += 86;
  updateDriverStats();

  const tripCard = document.getElementById('active-trip-card');
  const tripDetails = document.getElementById('active-trip-details');
  tripDetails.innerHTML = `
    <div style="display:flex;align-items:center;gap:12px;margin:16px 0;padding:14px;background:var(--gray-100);border-radius:10px">
      <div style="width:44px;height:44px;background:var(--green);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:18px;font-weight:700;color:black">A</div>
      <div>
        <div style="font-weight:700">Arjun Sharma</div>
        <div style="font-size:13px;color:var(--gray-500)">📞 9876543210</div>
      </div>
      <div style="margin-left:auto">
        <div style="font-size:22px;font-weight:800;color:var(--green);font-family:'Syne',sans-serif">₹86</div>
      </div>
    </div>
    <div style="margin-bottom:16px">
      <div style="font-size:13px;margin-bottom:6px">📍 Hitech City, Hyderabad</div>
      <div style="font-size:13px">🏁 Charminar, Old City</div>
    </div>
    <div style="font-size:15px;font-weight:600;margin-bottom:12px">OTP: <span style="font-family:'Syne',sans-serif;font-size:22px;color:var(--green);letter-spacing:4px">4782</span></div>
    <div style="display:flex;gap:10px;flex-wrap:wrap">
      <button class="btn btn-dark btn-sm" onclick="updateTripStatus('ARRIVED')">📍 Arrived at Pickup</button>
      <button class="btn btn-primary btn-sm" onclick="updateTripStatus('STARTED')">🚗 Start Ride</button>
      <button class="btn btn-primary btn-sm" style="background:var(--green-dark)" onclick="updateTripStatus('COMPLETED')">✅ Complete Ride</button>
    </div>
  `;
  tripCard.classList.remove('hidden');
  showToast('✅ Ride accepted! Head to pickup location.');
}

function rejectRide() {
  document.getElementById('ride-request-card').classList.add('hidden');
  showToast('Ride declined.', 'info');
  if (driverOnline) {
    rideRequestTimeout = setTimeout(simulateIncomingRide, 8000);
  }
}

function updateTripStatus(status) {
  const badge = document.getElementById('active-trip-status');
  const statusMap = {
    ARRIVED: { text:'Driver Arrived', cls:'accepted' },
    STARTED: { text:'Ride In Progress', cls:'started' },
    COMPLETED: { text:'Completed', cls:'completed' }
  };
  const s = statusMap[status];
  badge.textContent = s.text;
  badge.className = `status-badge ${s.cls}`;
  if (status === 'COMPLETED') {
    setTimeout(() => {
      document.getElementById('active-trip-card').classList.add('hidden');
      addDriverRideToHistory();
      showToast('🎉 Ride completed! ₹86 earned!');
      if (driverOnline) rideRequestTimeout = setTimeout(simulateIncomingRide, 6000);
    }, 1000);
  }
}

function addDriverRideToHistory() {
  const tbody = document.getElementById('driver-history-tbody');
  const now = new Date().toLocaleTimeString();
  const row = `<tr>
    <td class="ride-id-col">SR-2024-${String(driverRideCount).padStart(5,'0')}</td>
    <td>Arjun Sharma</td>
    <td><div style="font-size:13px">Hitech City → Charminar</div></td>
    <td class="fare-col">₹86</td>
    <td><span class="status-badge completed">Completed</span></td>
    <td style="color:var(--gray-500);font-size:12px">${now}</td>
  </tr>`;
  if (tbody.querySelector('td[colspan]')) tbody.innerHTML = '';
  tbody.insertAdjacentHTML('afterbegin', row);
}

function updateDriverStats() {
  document.getElementById('drv-earnings').textContent = `₹${driverEarnings}`;
  document.getElementById('drv-rides').textContent = driverRideCount;
  document.getElementById('driver-sidebar-earnings').textContent = `₹${driverEarnings}`;
  document.getElementById('drv-total-rides').textContent = driverRideCount;
  document.getElementById('weekly-earn').textContent = `₹${driverEarnings}`;
  document.getElementById('monthly-earn').textContent = `₹${driverEarnings}`;
  document.getElementById('total-earn').textContent = `₹${driverEarnings}`;
}

// ===== WALLET =====
function setAmount(amt) { document.getElementById('add-money-amt').value = amt; }
function addMoney() {
  const amt = parseFloat(document.getElementById('add-money-amt').value);
  if (!amt || amt < 1) return showToast('Enter a valid amount', 'error');
  state.walletBalance = (state.walletBalance || 0) + amt;
  document.getElementById('wallet-balance-display').textContent = `₹${state.walletBalance.toFixed(2)}`;
  document.getElementById('sidebar-wallet').textContent = `₹${state.walletBalance.toFixed(2)}`;
  document.getElementById('add-money-amt').value = '';
  const txnList = document.getElementById('txn-list');
  const newTxn = `<div class="notif-item">
    <div class="notif-icon" style="background:#E6FAF1;font-size:18px">💰</div>
    <div class="notif-text">
      <div class="title">Wallet topped up</div>
      <div class="time">+₹${amt.toFixed(2)} · Just now</div>
    </div>
    <div style="margin-left:auto;color:var(--green);font-weight:700">+₹${amt}</div>
  </div>`;
  txnList.insertAdjacentHTML('afterbegin', newTxn);
  showToast(`₹${amt} added to your wallet! 💰`);
}

// ===== TOAST =====
function showToast(msg, type = 'success') {
  const container = document.getElementById('toasts');
  const toast = document.createElement('div');
  toast.className = `toast ${type}`;
  const icons = { success:'✅', error:'❌', info:'ℹ️' };
  toast.innerHTML = `<span>${icons[type]||'✅'}</span><span>${msg}</span>`;
  container.appendChild(toast);
  setTimeout(() => { toast.style.opacity='0'; toast.style.transform='translateX(100%)'; toast.style.transition='all 0.3s'; setTimeout(() => toast.remove(), 300); }, 4000);
}

// ===== INIT =====
window.onload = () => {
  showScreen('home');
};
</script>
</body>
</html>
