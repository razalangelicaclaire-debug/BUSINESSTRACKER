# BUSINESSTRACKER
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>OWNOVA | Business Companion</title>

<style>
* {
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    margin: 0;
    background: #f5f5ed;
    color: black;
}

.sidebar {
    width: 235px;
    height: 100vh;
    background: #183d2c;
    color: pink;
    position: fixed;
    padding: 25px 15px;
    top: 0;
    left: 0;
}

.logo {
    font-size: 27px;
    font-weight: bold;
    margin: 10px 12px;
}

.logo span {
    color: #b8d5a9;
}

.sidebar p {
    color: #a7c1ae;
    font-size: 11px;
    margin: 30px 12px 12px;
    letter-spacing: 1px;
}

.sidebar button {
    display: block;
    width: 100%;
    background: transparent;
    color: #dce9df;
    border: none;
    padding: 13px;
    margin: 5px 0;
    text-align: left;
    border-radius: 8px;
    cursor: pointer;
    font-size: 14px;
}

.sidebar button:hover,
.sidebar button.active {
    background: #315c43;
    color: white;
}

.main {
    margin-left: 235px;
    padding: 30px;
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;
}

.header h1 {
    margin: 0;
    font-size: 25px;
}

.header p {
    color: #829187;
    font-size: 13px;
}

.badge {
    background: #dcebdc;
    color: #315c43;
    padding: 10px 15px;
    border-radius: 20px;
    font-size: 12px;
}

.page {
    display: none;
    margin-top: 25px;
}

.page.active {
    display: block;
}

.stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 15px;
}

.card {
    background: white;
    padding: 20px;
    border-radius: 13px;
    box-shadow: 0 3px 12px #00000008;
}

.card small {
    color: #819087;
}

.card h2 {
    margin: 12px 0 5px;
    color: #28583d;
    font-size: 25px;
}

.panel {
    background: white;
    border-radius: 13px;
    padding: 22px;
    margin-top: 20px;
    box-shadow: 0 3px 12px #00000008;
}

.panel h2 {
    margin-top: 0;
}

input, select {
    width: 100%;
    padding: 12px;
    margin: 7px 0 13px;
    border: 1px solid #dce3dc;
    border-radius: 7px;
    background: #fff;
    outline: none;
}

input:focus, select:focus {
    border-color: #548365;
}

label {
    font-size: 12px;
    font-weight: bold;
}

.btn {
    background: #315e43;
    color: white;
    border: none;
    padding: 12px 16px;
    border-radius: 7px;
    cursor: pointer;
    font-weight: bold;
}

.btn:hover {
    background: #1b422d;
}

.delete {
    background: #bd5550;
    padding: 7px 10px;
    font-size: 11px;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 15px;
}

th, td {
    padding: 12px 8px;
    border-bottom: 1px solid #edf0e9;
    text-align: left;
    font-size: 12px;
}

th {
    color: #718075;
    background: #f5f7f2;
}

.scroll {
    overflow-x: auto;
}

.grid2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 18px;
}

.notice {
    background: #edf4e8;
    padding: 15px;
    border-radius: 9px;
    margin-top: 12px;
    font-size: 13px;
}

footer {
    text-align: center;
    color: #96a397;
    font-size: 11px;
    margin-top: 35px;
}

@media(max-width:850px) {
    .sidebar {
        width: 100%;
        height: auto;
        position: relative;
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        padding: 10px;
    }

    .sidebar p {
        display: none;
    }

    .logo {
        width: 100%;
    }

    .sidebar button {
        width: auto;
        padding: 9px;
        font-size: 11px;
    }

    .main {
        margin-left: 0;
        padding: 18px;
    }

    .stats {
        grid-template-columns: 1fr 1fr;
    }
}

@media(max-width:500px) {
    .grid2 {
        grid-template-columns: 1fr;
    }
}
</style>
</head>

<body>

<!-- SIDEBAR -->

<div class="sidebar">

    <div class="logo">BUSINESS<span>TRACKER.</span></div>

    <p>BUSINESS MANAGEMENT</p>

    <button class="active" onclick="showPage('dashboard',this)">
        ◈ Dashboard
    </button>

    <button onclick="showPage('products',this)">
        ◇ Products
    </button>

    <button onclick="showPage('orders',this)">
        ▣ Orders
    </button>

    <button onclick="showPage('customers',this)">
        ♙ Customers
    </button>

    <button onclick="showPage('expenses',this)">
        ₱ Expenses
    </button>

    <button onclick="showPage('appointments',this)">
        ◷ Appointments
    </button>

    <button onclick="showPage('reports',this)">
        ▤ Reports
    </button>

</div>


<!-- MAIN CONTENT -->

<div class="main">

<div class="header">
    <div>
        <h1 id="pageTitle">Business Overview</h1>
        <p>Welcome to your business workspace.</p>
    </div>

    <div class="badge" id="today"></div>
</div>


<!-- DASHBOARD -->

<section class="page active" id="dashboard">

    <div class="stats">

        <div class="card">
            <small>Total Products</small>
            <h2 id="totalProducts">0</h2>
        </div>

        <div class="card">
            <small>Total Customers</small>
            <h2 id="totalCustomers">0</h2>
        </div>

        <div class="card">
            <small>Total Revenue</small>
            <h2 id="totalRevenue">₱0</h2>
        </div>

        <div class="card">
            <small>Net Profit</small>
            <h2 id="netProfit">₱0</h2>
        </div>

    </div>

    <div class="panel">
        <h2>Business Summary</h2>
        <p>Here's what's happening in your business.</p>

        <div class="notice">
            Keep your business organized with BUSINESSTRACKER.
            Monitor your sales, expenses, customers, and products
            in one place.
        </div>
    </div>

    <div class="panel">
        <h2>Recent Orders</h2>

        <div class="scroll">
        <table>
            <thead>
                <tr>
                    <th>Customer</th>
                    <th>Product</th>
                    <th>Quantity</th>
                    <th>Total</th>
                </tr>
            </thead>
            <tbody id="recentOrders"></tbody>
        </table>
        </div>
    </div>

</section>


<!-- PRODUCTS -->

<section class="page" id="products">

    <div class="panel">
        <h2>◇ Product Management</h2>

        <label>Product Name</label>
        <input id="pName" placeholder="Enter product name">

        <label>Product Price</label>
        <input id="pPrice" type="number" min="0.01" step="0.01" placeholder="Enter price">

        <label>Available Stock</label>
        <input id="pStock" type="number" min="0" step="1" placeholder="Enter quantity">

        <button class="btn" onclick="addProduct()">
            + Add Product
        </button>
    </div>

    <div class="panel">
        <h2>Product Inventory</h2>

        <div class="scroll">
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Product</th>
                    <th>Price</th>
                    <th>Stock</th>
                    <th>Action</th>
                </tr>
            </thead>

            <tbody id="productList"></tbody>
        </table>
        </div>
    </div>

</section>


<!-- ORDERS -->

<section class="page" id="orders">

    <div class="panel">
        <h2>▣ Create Customer Order</h2>

        <label>Customer Name</label>
        <input id="orderCustomer" placeholder="Customer name">

        <label>Select Product</label>
        <select id="orderProduct">
            <option value="">Choose product</option>
        </select>

        <label>Quantity</label>
        <input id="orderQty" type="number" min="1" step="1" value="1">

        <button class="btn" onclick="createOrder()">
            Complete Order
        </button>
    </div>

    <div class="panel">
        <h2>Order History</h2>

        <div class="scroll">
        <table>
            <thead>
                <tr>
                    <th>Customer</th>
                    <th>Product</th>
                    <th>Quantity</th>
                    <th>Total</th>
                </tr>
            </thead>

            <tbody id="orderList"></tbody>
        </table>
        </div>
    </div>

</section>


<!-- CUSTOMERS -->

<section class="page" id="customers">

    <div class="panel">
        <h2>♙ Customer Management</h2>

        <label>Customer Name</label>
        <input id="cName" placeholder="Customer name">

        <label>Contact Number</label>
        <input id="cContact" placeholder="Contact number">

        <button class="btn" onclick="addCustomer()">
            + Add Customer
        </button>
    </div>

    <div class="panel">
        <h2>Customer Database</h2>

        <div class="scroll">
        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Contact</th>
                    <th>Loyalty Points</th>
                </tr>
            </thead>

            <tbody id="customerList"></tbody>
        </table>
        </div>
    </div>

</section>


<!-- EXPENSES -->

<section class="page" id="expenses">

    <div class="panel">
        <h2>₱ Business Expense Tracker</h2>

        <label>Expense Description</label>
        <input id="eName" placeholder="Example: Electricity bill">

        <label>Amount</label>
        <input id="eAmount" type="number" min="0.01" step="0.01" placeholder="Enter amount">

        <button class="btn" onclick="addExpense()">
            + Record Expense
        </button>
    </div>

    <div class="panel">
        <h2>Expense History</h2>

        <table>
            <thead>
                <tr>
                    <th>Description</th>
                    <th>Amount</th>
                </tr>
            </thead>

            <tbody id="expenseList"></tbody>
        </table>
    </div>

</section>


<!-- APPOINTMENTS -->

<section class="page" id="appointments">

    <div class="panel">
        <h2>◷ Appointment Scheduler</h2>

        <label>Customer Name</label>
        <input id="aName" placeholder="Customer name">

        <label>Appointment Date</label>
        <input id="aDate" type="date">

        <label>Appointment Details</label>
        <input id="aDetails" placeholder="Purpose of appointment">

        <button class="btn" onclick="addAppointment()">
            + Schedule Appointment
        </button>
    </div>

    <div class="panel">
        <h2>Upcoming Appointments</h2>

        <table>
            <thead>
                <tr>
                    <th>Customer</th>
                    <th>Date</th>
                    <th>Details</th>
                </tr>
            </thead>

            <tbody id="appointmentList"></tbody>
        </table>
    </div>

</section>


<!-- REPORTS -->

<section class="page" id="reports">

    <div class="stats">

        <div class="card">
            <small>Total Revenue</small>
            <h2 id="reportRevenue">₱0</h2>
        </div>

        <div class="card">
            <small>Total Expenses</small>
            <h2 id="reportExpenses">₱0</h2>
        </div>

        <div class="card">
            <small>Net Profit</small>
            <h2 id="reportProfit">₱0</h2>
        </div>

        <div class="card">
            <small>Completed Orders</small>
            <h2 id="reportOrders">0</h2>
        </div>

    </div>

    <div class="panel">
        <h2>Business Performance</h2>

        <p>Revenue: <strong id="performanceRevenue">₱0</strong></p>
        <p>Expenses: <strong id="performanceExpenses">₱0</strong></p>
        <p>Net Profit: <strong id="performanceProfit">₱0</strong></p>

        <button class="btn" onclick="exportCSV()">
            Download Sales Report
        </button>
    </div>

</section>


<footer>
    OWNOVA © 2026 | Smart Business Companion
</footer>

</div>


<script>

// ============================
// DATA STORAGE
// ============================

let products = JSON.parse(localStorage.getItem("ownovaProducts")) || [];
let orders = JSON.parse(localStorage.getItem("ownovaOrders")) || [];
let customers = JSON.parse(localStorage.getItem("ownovaCustomers")) || [];
let expenses = JSON.parse(localStorage.getItem("ownovaExpenses")) || [];
let appointments = JSON.parse(localStorage.getItem("ownovaAppointments")) || [];

function saveData() {

    localStorage.setItem("ownovaProducts", JSON.stringify(products));
    localStorage.setItem("ownovaOrders", JSON.stringify(orders));
    localStorage.setItem("ownovaCustomers", JSON.stringify(customers));
    localStorage.setItem("ownovaExpenses", JSON.stringify(expenses));
    localStorage.setItem("ownovaAppointments", JSON.stringify(appointments));

}

function money(value) {
    return "₱" + Number(value).toLocaleString("en-PH", {
        minimumFractionDigits: 2,
        maximumFractionDigits: 2
    });
}

function safe(value) {
    return String(value).replace(/[&<>"']/g, c => ({
        "&":"&amp;", "<":"&lt;", ">":"&gt;",
        '"':"&quot;", "'":"&#39;"
    })[c]);
}


// ============================
// NAVIGATION
// ============================

function showPage(page, button) {

    document.querySelectorAll(".page").forEach(p => {
        p.classList.remove("active");
    });

    document.getElementById(page).classList.add("active");

    document.querySelectorAll(".sidebar button").forEach(b => {
        b.classList.remove("active");
    });

    button.classList.add("active");

    const titles = {
        dashboard: "Business Overview",
        products: "Product Management",
        orders: "Customer Orders",
        customers: "Customer Database",
        expenses: "Expense Tracker",
        appointments: "Appointment Scheduler",
        reports: "Business Reports"
    };

    document.getElementById("pageTitle").textContent = titles[page];

    renderAll();
}


// ============================
// PRODUCT MANAGEMENT
// ============================

function addProduct() {

    let name = document.getElementById("pName").value.trim();
    let price = Number(document.getElementById("pPrice").value);
    let stock = Number(document.getElementById("pStock").value);

    if(!name || price <= 0 || !Number.isInteger(stock) || stock < 0) {
        alert("Please enter valid product details.");
        return;
    }

    products.push({
        id: Date.now(),
        name: name,
        price: price,
        stock: stock
    });

    saveData();

    document.getElementById("pName").value = "";
    document.getElementById("pPrice").value = "";
    document.getElementById("pStock").value = "";

    renderAll();

    alert("Product successfully added!");
}

function deleteProduct(id) {

    if(!confirm("Delete this product?")) return;

    products = products.filter(p => p.id !== id);

    saveData();
    renderAll();
}

function renderProducts() {

    document.getElementById("productList").innerHTML =
        products.map(p => `
        <tr>
            <td>${p.id}</td>
            <td>${safe(p.name)}</td>
            <td>${money(p.price)}</td>
            <td>${p.stock}</td>
            <td>
                <button class="btn delete"
                onclick="deleteProduct(${p.id})">
                Delete
                </button>
            </td>
        </tr>
        `).join("") || "<tr><td colspan='5'>No products yet.</td></tr>";

    document.getElementById("orderProduct").innerHTML =
        '<option value="">Choose product</option>' +
        products.filter(p => p.stock > 0).map(p =>
            `<option value="${p.id}">${safe(p.name)} - ${money(p.price)}</option>`
        ).join("");

}


// ============================
// CUSTOMER MANAGEMENT
// ============================

function addCustomer() {

    let name = document.getElementById("cName").value.trim();
    let contact = document.getElementById("cContact").value.trim();

    if(!name || !contact) {
        alert("Please complete customer information.");
        return;
    }

    customers.push({
        id: Date.now(),
        name: name,
        contact: contact,
        points: 0
    });

    saveData();

    document.getElementById("cName").value = "";
    document.getElementById("cContact").value = "";

    renderAll();

    alert("Customer successfully registered!");
}

function renderCustomers() {

    document.getElementById("customerList").innerHTML =
        customers.map(c => `
        <tr>
            <td>${safe(c.name)}</td>
            <td>${safe(c.contact)}</td>
            <td>⭐ ${c.points}</td>
        </tr>
        `).join("") || "<tr><td colspan='3'>No customers yet.</td></tr>";

}


// ============================
// ORDER MANAGEMENT
// ============================

function createOrder() {

    let name = document.getElementById("orderCustomer").value.trim();

    let id = Number(document.getElementById("orderProduct").value);

    let qty = Number(document.getElementById("orderQty").value);

    let product = products.find(p => p.id === id);

    if(!name || !product || !Number.isInteger(qty) || qty <= 0) {
        alert("Please enter valid order details.");
        return;
    }

    if(product.stock < qty) {
        alert("Insufficient stock!");
        return;
    }

    let total = product.price * qty;

    product.stock -= qty;

    let customer = customers.find(
        c => c.name.toLowerCase() === name.toLowerCase()
    );

    if(customer) {
        customer.points += Math.floor(total / 100);
    }

    orders.push({
        id: Date.now(),
        customer: name,
        product: product.name,
        quantity: qty,
        total: total,
        date: new Date().toISOString()
    });

    saveData();

    document.getElementById("orderCustomer").value = "";
    document.getElementById("orderProduct").value = "";
    document.getElementById("orderQty").value = 1;

    renderAll();

    alert("Order completed successfully! Total: " + money(total));
}

function renderOrders() {

    let html = orders.map(o => `
        <tr>
            <td>${safe(o.customer)}</td>
            <td>${safe(o.product)}</td>
            <td>${o.quantity}</td>
            <td>${money(o.total)}</td>
        </tr>
    `).join("") || "<tr><td colspan='4'>No orders recorded.</td></tr>";

    document.getElementById("orderList").innerHTML = html;
    document.getElementById("recentOrders").innerHTML = html;

}


// ============================
// EXPENSE TRACKER
// ============================

function addExpense() {

    let name = document.getElementById("eName").value.trim();
    let amount = Number(document.getElementById("eAmount").value);

    if(!name || amount <= 0) {
        alert("Enter valid expense details.");
        return;
    }

    expenses.push({
        id: Date.now(),
        name: name,
        amount: amount
    });

    saveData();

    document.getElementById("eName").value = "";
    document.getElementById("eAmount").value = "";

    renderAll();

    alert("Expense recorded!");
}

function renderExpenses() {

    document.getElementById("expenseList").innerHTML =
        expenses.map(e => `
        <tr>
            <td>${safe(e.name)}</td>
            <td>${money(e.amount)}</td>
        </tr>
        `).join("") || "<tr><td colspan='2'>No expenses recorded.</td></tr>";

}


// ============================
// APPOINTMENT SCHEDULER
// ============================

function addAppointment() {

    let name = document.getElementById("aName").value.trim();
    let date = document.getElementById("aDate").value;
    let details = document.getElementById("aDetails").value.trim();

    if(!name || !date || !details) {
        alert("Complete all appointment details.");
        return;
    }

    if(date < new Date().toLocaleDateString("en-CA")) {
        alert("Please select today or a future date.");
        return;
    }

    appointments.push({
        id: Date.now(),
        name: name,
        date: date,
        details: details
    });

    saveData();

    document.getElementById("aName").v
    document.getElementById("aDate").value = "";
    document.getElementById("aDetails").value = "";

    renderAll();

    alert("Appointment scheduled!");
}

function renderAppointments() {

    document.getElementById("appointmentList").innerHTML =
        appointments
        .sort((a,b) => a.date.localeCompare(b.date))
        .map(a => `
        <tr>
            <td>${safe(a.name)}</td>
            <td>${safe(a.date)}</td>
            <td>${safe(a.details)}</td>
        </tr>
        `).join("") || "<tr><td colspan='3'>No appointments yet.</td></tr>";

}


// ============================
// BUSINESS REPORTS
// ============================

function renderDashboard() {

    let revenue = orders.reduce((sum,o) => sum + o.total, 0);

    let totalExpenses = expenses.reduce((sum,e) => sum + e.amount, 0);

    let profit = revenue - totalExpenses;

    document.getElementById("totalProducts").textContent = products.length;

    document.getElementById("totalCustomers").textContent = customers.length;

    document.getElementById("totalRevenue").textContent = money(revenue);

    document.getElementById("netProfit").textContent = money(profit);

    document.getElementById("reportRevenue").textContent = money(revenue);

    document.getElementById("reportExpenses").textContent = money(totalExpenses);

    document.getElementById("reportProfit").textContent = money(profit);

    document.getElementById("reportOrders").textContent = orders.length;

    document.getElementById("performanceRevenue").textContent = money(revenue);

    document.getElementById("performanceExpenses").textContent = money(totalExpenses);

    document.getElementById("performanceProfit").textContent = money(profit);

}


// ============================
// EXPORT REPORT
// ============================

function exportCSV() {

    if(!orders.length) {
        alert("No orders to export.");
        return;
    }

    let rows = [
        ["Customer", "Product", "Quantity", "Total"]
    ];

    orders.forEach(o => {
        rows.push([
            o.customer,
            o.product,
            o.quantity,
            o.total
        ]);
    });

    let csv = rows.map(row =>
        row.map(value =>
            '"' + String(value).replace(/"/g,'""') + '"'
        ).join(",")
    ).join("\n");

    let blob = new Blob([csv], {
        type: "text/csv;charset=utf-8;"
    });

    let link = document.createElement("a");

    link.href = URL.createObjectURL(blob);
    link.download = "OWNOVA-Business-Report.csv";
    link.click();

    URL.revokeObjectURL(link.href);
}


// ============================
// UPDATE EVERYTHING
// ============================

function renderAll() {

    renderProducts();
    renderCustomers();
    renderOrders();
    renderExpenses();
    renderAppointments();
    renderDashboard();

}

document.getElementById("today").textContent =
    new Date().toLocaleDateString("en-PH", {
        month: "long",
        day: "numeric",
        year: "numeric"
    });

renderAll();

</script>

</body>
</html>
