<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Costa Aires - Montería</title>
    <style>
        :root { --azul: #004a99; --celeste: #007bff; --fondo: #eef2f7; }
        body { font-family: 'Segoe UI', sans-serif; margin: 0; background: var(--fondo); color: #333; }
        .app { max-width: 450px; margin: auto; background: white; min-height: 100vh; box-shadow: 0 0 25px rgba(0,0,0,0.1); }
        header { background: linear-gradient(135deg, var(--azul), var(--celeste)); color: white; padding: 35px 20px; text-align: center; border-bottom-left-radius: 40px; border-bottom-right-radius: 40px; }
        .logo-box { width: 150px; height: 150px; background: white; border-radius: 50%; margin: 0 auto 15px; overflow: hidden; border: 4px solid white; }
        .logo-box img { width: 100%; height: 100%; object-fit: cover; }
        .content { padding: 20px; }
        .btn { display: block; width: 100%; padding: 15px; margin-bottom: 10px; border-radius: 10px; border: none; font-weight: bold; text-align: center; text-decoration: none; cursor: pointer; box-sizing: border-box; }
        .btn-call { background: var(--celeste); color: white; }
        .btn-form { background: white; color: var(--azul); border: 2px solid var(--azul); }
        .acc-item { border: 1px solid #ddd; border-radius: 10px; margin-bottom: 10px; background: #fff; overflow: hidden; }
        .acc-header { padding: 15px; cursor: pointer; font-weight: bold; color: var(--azul); display: flex; justify-content: space-between; }
        .acc-content { display: none; padding: 15px; border-top: 1px solid #eee; font-size: 14px; }
        #form-view { display: none; padding: 20px; }
        input, select, textarea { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid #ccc; border-radius: 8px; box-sizing: border-box; }
    </style>
</head>
<body>
    <div class="app">
        <div id="home">
            <header>
                <div class="logo-box"><img src="https://i.ibb.co/yvfVXsF/Gemini-Generated-Image-6p9q5n6p9q5n6p9q.png" alt="Logo"></div>
                <h2>COSTA AIRES</h2>
                <p>📍 Montería · Córdoba</p>
            </header>
            <div class="content">
                <a href="tel:+573000000000" class="btn btn-call">📞 LLAMAR TÉCNICO</a>
                <button onclick="showForm()" class="btn btn-form">📅 AGENDAR SERVICIO</button>
                <div class="acc-item">
                    <div class="acc-header" onclick="toggle('auto')">🚗 Aires Automotrices <span>▼</span></div>
                    <div id="auto" class="acc-content">
                        Reparación, instalación desde cero, limpieza de hongos y mantenimiento general.
                    </div>
                </div>
                <div class="acc-item">
                    <div class="acc-header" onclick="toggle('home')">🏠 Hogar y Construcción <span>▼</span></div>
                    <div id="home-acc" class="acc-content">
                        Mantenimiento de aires de casa, fachadas, remodelación, baldosas y electricidad.
                    </div>
                </div>
            </div>
        </div>
        <div id="form-view">
            <h3>Solicitud de Servicio</h3>
            <input type="text" id="n" placeholder="Nombre">
            <input type="number" id="t" placeholder="WhatsApp">
            <input type="text" id="u" placeholder="Barrio">
            <textarea id="f" placeholder="¿Qué necesita?" rows="3"></textarea>
            <button onclick="enviar()" id="send" class="btn btn-call">ENVIAR DATOS</button>
            <p onclick="location.reload()" style="text-align:center; cursor:pointer;">← Volver</p>
        </div>
    </div>
    <script>
        function toggle(id){ 
            var e = document.getElementById(id === 'auto' ? 'auto' : 'home-acc');
            e.style.display = (e.style.display === 'block') ? 'none' : 'block';
        }
        function showForm(){ document.getElementById('home').style.display='none'; document.getElementById('form-view').style.display='block'; }
        function enviar(){
            const btn = document.getElementById('send');
            const d = { nombre: document.getElementById('n').value, telefono: document.getElementById('t').value, ubicacion: document.getElementById('u').value, falla: document.getElementById('f').value };
            if(!d.nombre || !d.telefono) return alert("Faltan datos");
            btn.disabled = true; btn.innerText = "Enviando...";
            fetch("https://script.google.com/macros/s/AKfycbz37VihXHT89VL2sPGegc6J5JDcI-U2RZzX6wdNtg2xIw_4gm4-4ftj7bPYQkyV-eS9gg/exec", { method: 'POST', mode: 'no-cors', body: JSON.stringify(d) })
            .then(() => { alert("✅ ¡Recibido! Te llamaremos pronto."); location.reload(); });
        }
    </script>
</body>
</html>
