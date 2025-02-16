<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CMMS Maintenance Dashboard</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.0/css/bootstrap.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.1/chart.min.js"></script>
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f9fa;
        }
        .sidebar {
            width: 250px;
            height: 100vh;
            position: fixed;
            left: 0;
            top: 0;
            background: #222;
            color: white;
            padding: 20px;
        }
        .sidebar a {
            display: block;
            padding: 12px;
            color: white;
            text-decoration: none;
            margin-bottom: 10px;
            border-radius: 5px;
        }
        .sidebar a:hover {
            background: #007bff;
        }
        .content {
            margin-left: 270px;
            padding: 20px;
        }
        .card {
            border-radius: 10px;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
        }
        .btn {
            margin: 5px;
        }
        .dark-mode {
            background-color: #121212 !important;
            color: white !important;
        }
    </style>
</head>
<body>

    <!-- Sidebar -->
    <div class="sidebar">
        <h2>⚙️ CMMS</h2>
        <a href="#">📊 Dashboard</a>
        <a href="#">📝 Work Orders</a>
        <a href="#">🔔 Alerts</a>
        <a href="#">👷 Technicians</a>
        <a href="#">⚙️ Settings</a>
        <button class="btn btn-secondary w-100" onclick="toggleDarkMode()">🌙 Toggle Dark Mode</button>
    </div>

    <!-- Main Content -->
    <div class="content">

        <!-- Dashboard Header -->
        <div class="d-flex justify-content-between align-items-center mb-4">
            <h2 class="text-primary">🔧 CMMS Maintenance Dashboard</h2>
        </div>

        <div class="row">
            <!-- Work Order Overview -->
            <div class="col-md-6">
                <div class="card p-3">
                    <h5>📊 Work Order Overview</h5>
                    <canvas id="workOrderChart"></canvas>
                </div>
            </div>

            <!-- Real-Time Alerts -->
            <div class="col-md-6">
                <div class="card p-3">
                    <h5>🔔 Real-Time Alerts</h5>
                    <ul class="list-group">
                        <li class="list-group-item text-danger">🔥 CNC Machine Overheating - <b>Urgent!</b></li>
                        <li class="list-group-item text-warning">🛠 Maintenance Needed - Hydraulic Pump</li>
                        <li class="list-group-item text-info">🔄 Conveyor System Check Required</li>
                    </ul>
                </div>
            </div>
        </div>

        <div class="row mt-3">
            <!-- Technician Activity -->
            <div class="col-md-6">
                <div class="card p-3">
                    <h5>👷 Technician Activity</h5>
                    <ul class="list-group">
                        <li class="list-group-item">✅ John Doe - Fixed Conveyor Belt (2h ago)</li>
                        <li class="list-group-item">🔧 Jane Smith - Replaced Hydraulic Pump (4h ago)</li>
                        <li class="list-group-item">🔍 Alex Johnson - Inspected Cooling System (1d ago)</li>
                    </ul>
                </div>
            </div>

            <!-- System Performance Metrics (New Section) -->
            <div class="col-md-6">
                <div class="card p-3">
                    <h5>📈 System Performance Metrics</h5>
                    <ul class="list-group">
                        <li class="list-group-item">
                            <i class="fas fa-server text-success"></i> System Uptime: <span id="uptime">99.98%</span>
                        </li>
                        <li class="list-group-item">
                            <i class="fas fa-stopwatch text-primary"></i> Avg. Completion Time: <span id="completion-time">4.2 hrs</span>
                        </li>
                        <li class="list-group-item">
                            <i class="fas fa-user-cog text-warning"></i> Active Technicians: <span id="active-techs">7</span>
                        </li>
                        <li class="list-group-item">
                            <i class="fas fa-history text-info"></i> Recent Activity:
                            <ul id="activity-log" class="mt-2">
                                <li>✅ Work Order #231 completed.</li>
                                <li>🔄 Technician John assigned to Order #240.</li>
                                <li>⚠️ New Alert: Hydraulic Pump Issue.</li>
                            </ul>
                        </li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Work Order Actions -->
        <div class="mt-4 text-center">
            <button class="btn btn-primary">➕ Create Work Order</button>
            <button class="btn btn-success">✔️ Mark Completed</button>
            <button class="btn btn-warning">🔄 Reassign Order</button>
            <button class="btn btn-danger">🗑️ Delete Order</button>
        </div>

    </div>

    <!-- JavaScript -->
    <script>
        // Work Order Chart Data
        const ctx = document.getElementById('workOrderChart').getContext('2d');
        const workOrderChart = new Chart(ctx, {
            type: 'pie',
            data: {
                labels: ['Open', 'In Progress', 'Completed'],
                datasets: [{
                    data: [10, 6, 20],
                    backgroundColor: ['#ff5733', '#FFC300', '#33FF57']
                }]
            }
        });

        // Dark Mode Toggle
        function toggleDarkMode() {
            document.body.classList.toggle("dark-mode");
            let cards = document.querySelectorAll(".card, .sidebar");
            cards.forEach(card => card.classList.toggle("bg-dark"));
        }
    </script>

</body>
</html>
