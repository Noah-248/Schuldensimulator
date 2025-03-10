<!DOCTYPE html>
<html>
<head>
    <title>Schuldensimulator</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 40px; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #ddd; padding: 10px; text-align: left; }
        th { background-color: #f4f4f4; }
        input { width: 100%; padding: 5px; }
        button { margin-top: 10px; padding: 10px; }
    </style>
</head>
<body>
    <h2>Schuldensimulator</h2>
    <table id="financeTable">
        <tr>
            <th>Kategorie</th>
            <th>Betrag (EUR)</th>
        </tr>
        <tr><td>Einnahmen - Taschengeld</td><td><input type="number" class="income" value="0"></td></tr>
        <tr><td>Einnahmen - Nebenjobs</td><td><input type="number" class="income" value="0"></td></tr>
        <tr><td>Einnahmen - Geldgeschenke</td><td><input type="number" class="income" value="0"></td></tr>
        <tr><td>Einnahmen - Sonstige</td><td><input type="number" class="income" value="0"></td></tr>
        <tr><td>Ausgaben - Lebensmittel</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Streaming-Dienste</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Handyvertrag</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Kleidung & Shopping</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Freizeitaktivitäten</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Transport</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Schulmaterial</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Fast Food</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Videospiele/In-App-Käufe</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Hobbys (z. B. Musik, Sport)</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Geschenke für Freunde/Familie</td><td><input type="number" class="expense" value="0"></td></tr>
        <tr><td>Ausgaben - Sonstige</td><td><input type="number" class="expense" value="0"></td></tr>
    </table>
    <button onclick="calculateBalance()">Bilanz berechnen</button>
    <h3>Ergebnis: <span id="result">0</span> EUR</h3>
    <p id="advice"></p>
    
    <script>
        function calculateBalance() {
            let incomes = document.querySelectorAll('.income');
            let expenses = document.querySelectorAll('.expense');
            let totalIncome = 0, totalExpense = 0;
            
            incomes.forEach(input => totalIncome += Number(input.value));
            expenses.forEach(input => totalExpense += Number(input.value));
            
            let balance = totalIncome - totalExpense;
            document.getElementById('result').textContent = balance;
            
            let advice = "";
            if (balance > 50) {
                advice = "Super! Du hast eine gute Finanzplanung. Überlege, ob du einen Teil sparen kannst.";
            } else if (balance > 0) {
                advice = "Gut gemacht! Dein Budget ist ausgeglichen, aber versuche vielleicht, noch etwas zu sparen.";
            } else if (balance >= -50) {
                advice = "Achtung! Du gibst mehr aus, als du einnimmst. Überlege, wo du sparen kannst.";
            } else {
                advice = "Kritische Lage! Deine Ausgaben übersteigen deine Einnahmen deutlich. Prüfe, welche Ausgaben du reduzieren kannst.";
            }
            document.getElementById('advice').textContent = advice;
        }
    </script>
</body>
</html>
