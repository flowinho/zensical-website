---
title: "KDA Ratio Rechner"
icon: lucide/calculator
hide:
- footer
---

<style>

        /* Spinner entfernen */
        input::-webkit-outer-spin-button,
        input::-webkit-inner-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }
        input[type=number] {
            -moz-appearance: textfield;
        }

        /* Haupt-Container (Karte) */
        .card {
            background-color: #ebebebff;
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 4px 12px -12px rgba(0, 0, 0, 0.5);
            border: 1px solid #9d36a7ff;
            width: 100%;
            max-width: 360px;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            position: relative;
            overflow: hidden;
            box-sizing: border-box;
            color: #000000;
        }

        /* Dekorativer Streifen oben */
        .glow-strip {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #422dffff, #a855f7, #ec4899);
        }

        .card h1 {
            margin: 0 0 0.5rem 0;
            text-align: center;
            font-size: 1.5rem;
            letter-spacing: 0.05em;
            color: #000000;
        }

        /* Eingabefelder Wrapper */
        .inputs-container {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        /* Floating Label Logik */
        .input-group {
            position: relative;
        }

        .input-field {
            display: block;
            width: 100%;
            padding: 0.75rem 1rem;
            font-size: 0.875rem;
            background-color: #e0cde9ff; /* Etwas heller als Card BG */
            border: 1px solid #585858ff;
            border-radius: 0.5rem;
            color: inherit;
            box-sizing: border-box;
            outline: none;
            transition: border-color 0.2s;
            font-family: inherit;
        }

        .input-field:focus {
            border-color: var(--accent-blue);
        }

        /* Spezifische Farben für die Inputs beim Tippen */
        #kills { color: #3c4d3fff; }
        #deaths { color: #3c4d3fff; }
        #assists { color: #3c4d3fff; }

        #kills:focus { border-color: #3c4d3fff; }
        #deaths:focus { border-color: #3c4d3fff; }
        #assists:focus { border-color: #3c4d3fff; }

        .floating-label {
            position: absolute;
            left: 1rem;
            top: 50%;
            transform: translateY(-50%);
            font-size: 0.875rem;
            color: #000000;
            pointer-events: none;
            transition: all 0.2s ease-out;
            background-color: transparent;
            padding: 0 0.25rem;
        }

        /* Wenn Input Fokus hat oder nicht leer ist */
        .input-field:focus + .floating-label,
        .input-field:not(:placeholder-shown) + .floating-label {
            top: 0;
            transform: translateY(-50%) scale(0.85);
            background-color: #e0cde9ff; /* Damit die Linie überdeckt wird */
            border-radius: 4px;
        }
        
        .input-field:focus + .floating-label {
             color: inherit; /* Nimmt die Farbe des Inputs an, wenn Fokus */
        }
        
        /* Ergebnis Box */
        .result-box {
            text-align: center;
            margin-top: 1rem;
            padding: 1.5rem;
            background-color: #e2e2e2ff; /* Fast schwarz */
            border-radius: 0.75rem;
            border: 1px solid #1e293b;
        }

        .result-label {
            color: #000000;
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 0.25rem;
            display: block;
        }

        #result {
            font-size: 3rem;
            font-weight: bold;
            display: block;
            transition: color 0.3s, text-shadow 0.3s;
            color: #000000;
        }

        /* Hilfsklassen für JS Farben */
        .text-gray { color: var(--text-muted); }
        .text-blue { color: var(--accent-blue); }
        .text-gold { 
            color: var(--accent-gold); 
            text-shadow: 0 0 20px rgba(250, 204, 21, 0.5);
        }
        .text-white { color: var(--text-main); }

    </style>

# KDA Rechner

<div class="card">
    <div class="glow-strip"></div>
    <h1>KDA RECHNER</h1>

    <div class="inputs-container">
        <div class="input-group">
            <!-- placeholder=" " ist wichtig für den CSS :placeholder-shown Hack -->
            <input type="number" id="kills" class="input-field" placeholder=" ">
            <label for="kills" class="floating-label">Kills</label>
        </div>

        <div class="input-group">
            <input type="number" id="deaths" class="input-field" placeholder=" ">
            <label for="deaths" class="floating-label">Deaths</label>
        </div>

        <div class="input-group">
            <input type="number" id="assists" class="input-field" placeholder=" ">
            <label for="assists" class="floating-label">Assists</label>
        </div>
    </div>

    <div class="result-box">
        <span class="result-label">Ratio</span>
        <span id="result" class="text-white">0.00</span>
    </div>
</div>

<script>
        const killsInput = document.getElementById('kills');
        const deathsInput = document.getElementById('deaths');
        const assistsInput = document.getElementById('assists');
        const resultDisplay = document.getElementById('result');

        function calculateKDA() {
            const k = parseFloat(killsInput.value) || 0;
            const d = parseFloat(deathsInput.value) || 0;
            const a = parseFloat(assistsInput.value) || 0;

            const divisor = d === 0 ? 1 : d;
            const kda = (k + a) / divisor;

            resultDisplay.textContent = kda.toFixed(2);
            updateColor(kda);
        }

        function updateColor(score) {
            // Alle Farbklassen entfernen
            resultDisplay.classList.remove('text-gray', 'text-blue', 'text-gold', 'text-white');
            
            if (score < 1) {
                resultDisplay.classList.add('text-gray');
            } else if (score >= 3 && score < 5) {
                resultDisplay.classList.add('text-blue');
            } else if (score >= 5) {
                resultDisplay.classList.add('text-gold');
                return;
            } else {
                resultDisplay.classList.add('text-white');
            }
        }

        killsInput.addEventListener('input', calculateKDA);
        deathsInput.addEventListener('input', calculateKDA);
        assistsInput.addEventListener('input', calculateKDA);
    </script>