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
