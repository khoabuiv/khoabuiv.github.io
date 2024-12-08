---
layout: default
title: Calculator
---
<h1>Risk Analysis Calculator</h1>
<form id="calculator">
    <input type="number" id="assetValue" placeholder="Asset Value"><br>
    <input type="number" id="exposureFactor" placeholder="Exposure Factor "><br>
    <button type="button" onclick="calculate()">Calculate</button>
</form>
<p id="result"></p>
<script>
    function calculate() {
        const assetValue = parseFloat(document.getElementById('assetValue').value);
        const exposureFactor = parseFloat(document.getElementById('exposureFactor').value);
        let result = assetValue * exposureFactor;

        switch (operation) {
            case 'add':
                result = num1 + num2;
                break;
            case 'subtract':
                result = num1 - num2;
                break;
            case 'multiply':
                result = num1 * num2;
                break;
            case 'divide':
                result = num1 / num2;
                break;
            default:
                result = 'Invalid operation';
        }

        document.getElementById('result').innerText = `Result: ${result}`;
    }
</script>