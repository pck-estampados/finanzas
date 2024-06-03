<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestión Financiera</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Gestión Financiera</h1>
    </header>
    <main>
        <section id="transactions">
            <h2>Transacciones</h2>
            <ul id="transaction-list"></ul>
        </section>
        <section id="add-transaction">
            <h2>Añadir Transacción</h2>
            <form id="transaction-form">
                <label for="title">Título:</label>
                <input type="text" id="title" required>
                <label for="amount">Cantidad:</label>
                <input type="number" id="amount" required>
                <label for="date">Fecha:</label>
                <input type="date" id="date" required>
                <label for="currency">Moneda:</label>
                <input type="text" id="currency" required>
                <label for="user">Usuario:</label>
                <input type="text" id="user" required>
                <button type="submit">Añadir</button>
            </form>
        </section>
    </main>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 1em 0;
}

main {
    padding: 1em;
}

section {
    background: white;
    margin: 1em 0;
    padding: 1em;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-top: 0.5em;
}

input, button {
    margin-top: 0.5em;
    padding: 0.5em;
    font-size: 1em;
}

button {
    background-color: #333;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #555;
}
document.addEventListener('DOMContentLoaded', () => {
    const form = document.getElementById('transaction-form');
    const transactionList = document.getElementById('transaction-list');
    const transactions = JSON.parse(localStorage.getItem('transactions')) || [];

    transactions.forEach(transaction => {
        addTransactionToDOM(transaction);
    });

    form.addEventListener('submit', (e) => {
        e.preventDefault();

        const title = document.getElementById('title').value;
        const amount = document.getElementById('amount').value;
        const date = document.getElementById('date').value;
        const currency = document.getElementById('currency').value;
        const user = document.getElementById('user').value;

        const transaction = { title, amount, date, currency, user };
        transactions.push(transaction);
        localStorage.setItem('transactions', JSON.stringify(transactions));

        addTransactionToDOM(transaction);
        form.reset();
    });

    function addTransactionToDOM(transaction) {
        const li = document.createElement('li');
        li.textContent = `${transaction.title} - ${transaction.amount} ${transaction.currency} - ${new Date(transaction.date).toLocaleDateString()} - ${transaction.user}`;
        transactionList.appendChild(li);
    }
});
