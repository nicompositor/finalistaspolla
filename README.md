<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Polla de Nelson Bedoya</title>
  <style>
    :root {
      color-scheme: dark;
      --bg: #07130f;
      --panel: #0d2119;
      --panel-2: #123126;
      --text: #f5f7f3;
      --muted: #a9b8af;
      --line: rgba(245, 247, 243, 0.14);
      --gold: #f7c948;
      --green: #29d17d;
      --cyan: #50d4ff;
      --red: #ff5a66;
      --shadow: 0 24px 80px rgba(0, 0, 0, 0.34);
      --radius: 8px;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      color: var(--text);
      background:
        radial-gradient(circle at top left, rgba(41, 209, 125, 0.22), transparent 34rem),
        radial-gradient(circle at bottom right, rgba(247, 201, 72, 0.16), transparent 32rem),
        linear-gradient(135deg, #07130f 0%, #091915 52%, #050908 100%);
    }

    main {
      width: min(1120px, calc(100% - 32px));
      margin: 0 auto;
      padding: 44px 0;
    }

    .hero {
      margin-bottom: 24px;
    }

    .intro {
      padding: 34px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(13, 33, 25, 0.78);
      box-shadow: var(--shadow);
      overflow: hidden;
      position: relative;
    }

    .intro::after {
      content: "";
      position: absolute;
      inset: auto -80px -150px auto;
      width: 280px;
      height: 280px;
      border: 32px solid rgba(80, 212, 255, 0.11);
      border-radius: 50%;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin: 0 0 14px;
      color: var(--gold);
      font-size: 0.8rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .eyebrow::before {
      content: "";
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background: var(--green);
      box-shadow: 0 0 18px rgba(41, 209, 125, 0.78);
    }

    h1 {
      max-width: 720px;
      margin: 0;
      font-size: clamp(2.1rem, 5vw, 4.8rem);
      line-height: 0.97;
      letter-spacing: 0;
    }

    .intro p {
      max-width: 650px;
      margin: 20px 0 0;
      color: var(--muted);
      font-size: 1.04rem;
      line-height: 1.65;
    }

    .pitch {
      display: grid;
      grid-template-columns: 1fr;
      gap: 22px;
      padding: 24px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background:
        linear-gradient(90deg, rgba(255, 255, 255, 0.04) 1px, transparent 1px),
        linear-gradient(180deg, rgba(255, 255, 255, 0.05), transparent 46%),
        rgba(13, 33, 25, 0.86);
      background-size: 72px 72px, auto, auto;
      box-shadow: var(--shadow);
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 16px;
    }

    label {
      display: grid;
      gap: 8px;
      color: var(--muted);
      font-size: 0.86rem;
      font-weight: 700;
    }

    select {
      width: 100%;
      min-height: 48px;
      padding: 0 42px 0 14px;
      border: 1px solid rgba(245, 247, 243, 0.18);
      border-radius: var(--radius);
      color: var(--text);
      background: #07130f;
      font: inherit;
      font-weight: 750;
      outline: none;
      appearance: none;
      background-image:
        linear-gradient(45deg, transparent 50%, var(--gold) 50%),
        linear-gradient(135deg, var(--gold) 50%, transparent 50%);
      background-position:
        calc(100% - 20px) 21px,
        calc(100% - 14px) 21px;
      background-size: 6px 6px, 6px 6px;
      background-repeat: no-repeat;
    }

    select:focus {
      border-color: var(--green);
      box-shadow: 0 0 0 4px rgba(41, 209, 125, 0.16);
    }

    .actions {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      align-items: center;
      justify-content: space-between;
      padding-top: 2px;
    }

    button {
      min-height: 48px;
      border: 0;
      border-radius: var(--radius);
      padding: 0 18px;
      color: #05100c;
      background: linear-gradient(135deg, var(--gold), var(--green));
      font: inherit;
      font-weight: 900;
      cursor: pointer;
      transition: transform 160ms ease, filter 160ms ease;
    }

    button:hover {
      transform: translateY(-1px);
      filter: brightness(1.04);
    }

    button:active {
      transform: translateY(0);
    }

    .hint {
      color: var(--muted);
      font-size: 0.91rem;
    }

    .results {
      min-height: 180px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(7, 19, 15, 0.58);
      overflow: hidden;
    }

    .empty-state,
    .warning-state {
      display: grid;
      place-items: center;
      min-height: 180px;
      padding: 26px;
      text-align: center;
      color: var(--muted);
      line-height: 1.5;
    }

    .warning-state strong {
      color: var(--red);
    }

    .result-content {
      display: grid;
      gap: 18px;
      padding: 22px;
    }

    .scenario {
      display: grid;
      gap: 10px;
      margin: 0;
    }

    .scenario-title {
      color: var(--muted);
      font-size: 0.82rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .scenario-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .scenario-list li {
      border: 1px solid rgba(245, 247, 243, 0.15);
      border-radius: 999px;
      padding: 8px 12px;
      background: rgba(18, 49, 38, 0.82);
      font-weight: 800;
    }

    .winner-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
      gap: 12px;
    }

    .winner-card {
      min-height: 118px;
      padding: 18px;
      border: 1px solid rgba(247, 201, 72, 0.42);
      border-radius: var(--radius);
      background: linear-gradient(160deg, rgba(247, 201, 72, 0.16), rgba(41, 209, 125, 0.08));
    }

    .winner-card small {
      display: block;
      margin-bottom: 8px;
      color: var(--gold);
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    .winner-card strong {
      display: block;
      font-size: 1.2rem;
      line-height: 1.2;
    }

    .winner-card .points {
      margin: 12px 0 0;
      color: var(--text);
      font-size: 0.98rem;
      font-weight: 850;
    }

    .detail-row {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      color: var(--muted);
      font-size: 0.92rem;
    }

    .detail-row span {
      border: 1px solid var(--line);
      border-radius: 999px;
      padding: 7px 10px;
      background: rgba(7, 19, 15, 0.5);
    }

    @media (max-width: 860px) {
      main {
        width: min(100% - 24px, 720px);
        padding: 24px 0;
      }

      .form-grid {
        grid-template-columns: 1fr;
      }

      .intro {
        padding: 26px;
      }

      .actions {
        align-items: stretch;
      }

      button {
        width: 100%;
      }
    }

    @media (max-width: 520px) {
      .pitch,
      .intro {
        padding: 18px;
      }
    }
  </style>
</head>
<body>
  <main>
    <section class="hero" aria-labelledby="titulo">
      <div class="intro">
        <p class="eyebrow">Finales del mundial</p>
        <h1 id="titulo">Polla de Nelson Bedoya</h1>
        <p>
          Selecciona el orden exacto de los cuatro primeros puestos y consulta
          qué participante o participantes ganarían la polla en ese escenario.
        </p>
      </div>
    </section>

    <section class="pitch" aria-label="Buscador de escenarios">
      <form id="formulario-polla">
        <div class="form-grid">
          <label for="campeon">
            Campeón
            <select id="campeon" name="campeon" required></select>
          </label>

          <label for="subcampeon">
            Subcampeón
            <select id="subcampeon" name="subcampeon" required></select>
          </label>

          <label for="tercero">
            Tercer puesto
            <select id="tercero" name="tercero" required></select>
          </label>

          <label for="cuarto">
            Cuarto puesto
            <select id="cuarto" name="cuarto" required></select>
          </label>
        </div>

        <div class="actions">
          <p class="hint">Cada equipo solo puede aparecer una vez en el escenario.</p>
          <button type="submit">Buscar / Calcular Escenario</button>
        </div>
      </form>

      <section id="resultados" class="results" aria-live="polite">
        <div class="empty-state">
          Elige las cuatro posiciones y presiona buscar para consultar los ganadores.
        </div>
      </section>
    </section>
  </main>

  <script>
    /*
      ================================================================
      BASE DE DATOS DE EJEMPLO
      ================================================================

      Reemplaza o completa esta constante con tus datos reales extraídos
      de Numbers/Excel.

      Estructura usada por cada opcion:
      {
        opcion: numero de la opcion,
        orden: ["Campeón", "Subcampeón", "Tercero", "Cuarto"],
        ganadores: [
          { nombre: "Nombre 1", puntos: 2925, puesto: 1 },
          { nombre: "Nombre 2", puntos: 2785, puesto: 2 }
        ]
      }

      Los unicos equipos disponibles son Francia, Argentina, Espana e
      Inglaterra. El orden debe coincidir exactamente con la consulta.
    */
    const DATOS_POLLA = [
      { opcion: 1, orden: ["Francia", "Argentina", "Inglaterra", "España"], ganadores: [
        { nombre: "CATALINA ORTIZ ANAYA", puntos: 2925, puesto: 1 },
        { nombre: "ANDRES SANIN", puntos: 2785, puesto: 2 },
        { nombre: "GUSTAVO CAMACHO", puntos: 2690, puesto: 3 },
        { nombre: "GUILLERMO JAVIER AMAYA", puntos: 2665, puesto: 4 },
        { nombre: "ECHEVERRIA MEJIA", puntos: 2605, puesto: 5 },
        { nombre: "JUAN CARLOS HOYOS", puntos: 2565, puesto: 6 },
        { nombre: "CARLOS A HERNANDEZ", puntos: 2515, puesto: 7 }
      ] },
      { opcion: 2, orden: ["Francia", "Argentina", "España", "Inglaterra"], ganadores: [
        { nombre: "ANDRES SANIN", puntos: 2915, puesto: 1 },
        { nombre: "GUSTAVO CAMACHO", puntos: 2820, puesto: 2 },
        { nombre: "ECHEVERRIA MEJIA", puntos: 2815, puesto: 3 },
        { nombre: "GUILLERMO JAVIER AMAYA", puntos: 2795, puesto: 4 },
        { nombre: "JUAN CARLOS HOYOS", puntos: 2775, puesto: 5 },
        { nombre: "CATALINA ORTIZ ANAYA", puntos: 2715, puesto: 6 },
        { nombre: "TANYA FIGUEROA BEDOYA", puntos: 2700, puesto: 7 }
      ] },
      { opcion: 3, orden: ["Argentina", "Francia", "España", "Inglaterra"], ganadores: [
        { nombre: "PEDRO SALAMANCA", puntos: 2810, puesto: 1 },
        { nombre: "RUBEN DARIO ORTIZ", puntos: 2785, puesto: 2 },
        { nombre: "CARLOS MOSOS", puntos: 2575, puesto: 3 },
        { nombre: "P FERNANDO SALAMANCA", puntos: 2565, puesto: 4 },
        { nombre: "PAULO ANDRES FLOREZ", puntos: 2555, puesto: 5 },
        { nombre: "PABLO TORO", puntos: 2520, puesto: 6 },
        { nombre: "HERNANDO FORERO", puntos: 2510, puesto: 7 }
      ] },
      { opcion: 4, orden: ["Argentina", "Francia", "Inglaterra", "España"], ganadores: [
        { nombre: "PEDRO SALAMANCA", puntos: 2680, puesto: 1 },
        { nombre: "CARLOS MOSOS", puntos: 2655, puesto: 2 },
        { nombre: "RUBEN DARIO ORTIZ", puntos: 2655, puesto: 2 },
        { nombre: "P FERNANDO SALAMANCA", puntos: 2645, puesto: 4 },
        { nombre: "HERNANDO FORERO", puntos: 2590, puesto: 5 },
        { nombre: "JORGE MARIO SEGOVIA", puntos: 2565, puesto: 6 },
        { nombre: "CATALINA ORTIZ ANAYA", puntos: 2475, puesto: 7 },
        { nombre: "PAULO ANDRES FLOREZ", puntos: 2475, puesto: 7 }
      ] },
      { opcion: 5, orden: ["Francia", "Inglaterra", "Argentina", "España"], ganadores: [
        { nombre: "DOUGLAS ALI", puntos: 2830, puesto: 1 },
        { nombre: "ALBERTO MELO", puntos: 2730, puesto: 2 },
        { nombre: "DIEGO ALBERTO BARRAGAN", puntos: 2715, puesto: 3 },
        { nombre: "GERMAN CAMACHO", puntos: 2705, puesto: 4 },
        { nombre: "DIEGO PEREA", puntos: 2620, puesto: 5 },
        { nombre: "DIANA SANCHEZ", puntos: 2610, puesto: 6 },
        { nombre: "HERNANDO FORERO", puntos: 2610, puesto: 6 }
      ] },
      { opcion: 6, orden: ["Francia", "Inglaterra", "España", "Argentina"], ganadores: [
        { nombre: "ALBERTO MELO", puntos: 2940, puesto: 1 },
        { nombre: "DIEGO ALBERTO BARRAGAN", puntos: 2925, puesto: 2 },
        { nombre: "GERMAN CAMACHO", puntos: 2835, puesto: 3 },
        { nombre: "DIEGO PEREA", puntos: 2830, puesto: 4 },
        { nombre: "JUAN CARLOS FIGUEROA", puntos: 2800, puesto: 5 },
        { nombre: "JOSE L MARTINEZ", puntos: 2735, puesto: 6 },
        { nombre: "ENRIQUE LOPIERRE", puntos: 2700, puesto: 7 }
      ] },
      { opcion: 7, orden: ["Inglaterra", "Francia", "España", "Argentina"], ganadores: [
        { nombre: "HERNANDO FORERO", puntos: 2850, puesto: 1 },
        { nombre: "MARCELY GONZALEZ", puntos: 2835, puesto: 2 },
        { nombre: "ALBERTO MELO", puntos: 2490, puesto: 3 },
        { nombre: "DIEGO ALBERTO BARRAGAN", puntos: 2475, puesto: 4 },
        { nombre: "KATHERINE TINJACA", puntos: 2470, puesto: 5 },
        { nombre: "PEDRO SALAMANCA", puntos: 2470, puesto: 5 },
        { nombre: "RUBEN DARIO ORTIZ", puntos: 2445, puesto: 7 }
      ] },
      { opcion: 8, orden: ["Inglaterra", "Francia", "Argentina", "España"], ganadores: [
        { nombre: "HERNANDO FORERO", puntos: 3060, puesto: 1 },
        { nombre: "MARCELY GONZALEZ", puntos: 2625, puesto: 2 },
        { nombre: "CHRISTIAN CAMILO NIETO", puntos: 2445, puesto: 3 },
        { nombre: "KATHERINE TINJACA", puntos: 2390, puesto: 4 },
        { nombre: "DOUGLAS ALI", puntos: 2380, puesto: 5 },
        { nombre: "FABIO SANCHEZ UMBARILA", puntos: 2345, puesto: 6 },
        { nombre: "PEDRO SALAMANCA", puntos: 2340, puesto: 7 }
      ] },
      { opcion: 9, orden: ["Inglaterra", "España", "Argentina", "Francia"], ganadores: [
        { nombre: "HERNANDO FORERO", puntos: 2710, puesto: 1 },
        { nombre: "KATHERINE TINJACA", puntos: 2660, puesto: 2 },
        { nombre: "CARLOS H LOPEZ", puntos: 2595, puesto: 3 },
        { nombre: "JOHANNA KLEIN", puntos: 2475, puesto: 4 },
        { nombre: "FAMILIA STERLING", puntos: 2435, puesto: 5 },
        { nombre: "PABLO TORO", puntos: 2370, puesto: 6 },
        { nombre: "CHRISTIAN CAMILO NIETO", puntos: 2365, puesto: 7 }
      ] },
      { opcion: 10, orden: ["Inglaterra", "España", "Francia", "Argentina"], ganadores: [
        { nombre: "KATHERINE TINJACA", puntos: 2870, puesto: 1 },
        { nombre: "HERNANDO FORERO", puntos: 2580, puesto: 2 },
        { nombre: "CARLOS H LOPEZ", puntos: 2515, puesto: 3 },
        { nombre: "PABLO TORO", puntos: 2500, puesto: 4 },
        { nombre: "JOHANNA KLEIN", puntos: 2475, puesto: 5 },
        { nombre: "MARCELY GONZALEZ", puntos: 2435, puesto: 6 },
        { nombre: "MIGUEL ANGEL OLIVA", puntos: 2410, puesto: 7 }
      ] },
      { opcion: 11, orden: ["España", "Inglaterra", "Francia", "Argentina"], ganadores: [
        { nombre: "VICTOR HUGO PEÑA JIMENEZ", puntos: 2790, puesto: 1 },
        { nombre: "TATIANA CELY", puntos: 2665, puesto: 2 },
        { nombre: "PABLO RIOS", puntos: 2620, puesto: 3 },
        { nombre: "JONATHAN NARVAEZ", puntos: 2590, puesto: 4 },
        { nombre: "RAFAEL GONZALEZ GOMEZ", puntos: 2585, puesto: 5 },
        { nombre: "CLEMENTE GAONA", puntos: 2570, puesto: 6 },
        { nombre: "FDO RAFAEL VARELA", puntos: 2570, puesto: 6 }
      ] },
      { opcion: 12, orden: ["España", "Inglaterra", "Argentina", "Francia"], ganadores: [
        { nombre: "TATIANA CELY", puntos: 2745, puesto: 1 },
        { nombre: "VICTOR HUGO PEÑA JIMENEZ", puntos: 2580, puesto: 2 },
        { nombre: "SEBASTIAN VARELA", puntos: 2500, puesto: 3 },
        { nombre: "PABLO RIOS", puntos: 2490, puesto: 4 },
        { nombre: "JONATHAN NARVAEZ", puntos: 2460, puesto: 5 },
        { nombre: "RAFAEL GONZALEZ GOMEZ", puntos: 2455, puesto: 6 },
        { nombre: "HERNANDO FORERO", puntos: 2450, puesto: 7 }
      ] },
      { opcion: 13, orden: ["España", "Argentina", "Inglaterra", "Francia"], ganadores: [
        { nombre: "JONATHAN NARVAEZ", puntos: 2730, puesto: 1 },
        { nombre: "MARIA ALEJANDRA ARDILA", puntos: 2690, puesto: 2 },
        { nombre: "JORGE ANDRES NAVAS", puntos: 2670, puesto: 3 },
        { nombre: "RICARDO RODRIGUEZ", puntos: 2620, puesto: 4 },
        { nombre: "MARIA JULIANA CALA", puntos: 2610, puesto: 5 },
        { nombre: "OSWALDO ALEMAN", puntos: 2605, puesto: 6 },
        { nombre: "JOSE LEONARDO ESCOBAR", puntos: 2600, puesto: 7 },
        { nombre: "MIGUEL OLIVA VALLEJOS", puntos: 2600, puesto: 7 }
      ] },
      { opcion: 14, orden: ["España", "Argentina", "Francia", "Inglaterra"], ganadores: [
        { nombre: "JONATHAN NARVAEZ", puntos: 2940, puesto: 1 },
        { nombre: "RICARDO RODRIGUEZ", puntos: 2830, puesto: 2 },
        { nombre: "MARIA ALEJANDRA ARDILA", puntos: 2820, puesto: 3 },
        { nombre: "JOSE LEONARDO ESCOBAR", puntos: 2810, puesto: 4 },
        { nombre: "CARLOS MARTINEZ VH", puntos: 2805, puesto: 5 },
        { nombre: "VILMA FIGUEROA", puntos: 2805, puesto: 5 },
        { nombre: "MARIANA RODRIGUEZ", puntos: 2775, puesto: 7 }
      ] },
      { opcion: 15, orden: ["Argentina", "España", "Francia", "Inglaterra"], ganadores: [
        { nombre: "PABLO TORO", puntos: 2920, puesto: 1 },
        { nombre: "JOSE ANDRÉS RIOS", puntos: 2715, puesto: 2 },
        { nombre: "JAIRO ENRIQUE CASTRO", puntos: 2705, puesto: 3 },
        { nombre: "MILCIADES DUSAN", puntos: 2595, puesto: 4 },
        { nombre: "JONATHAN NARVAEZ", puntos: 2490, puesto: 5 },
        { nombre: "KATHERINE TINJACA", puntos: 2450, puesto: 6 },
        { nombre: "JOSE WILMER VARELA", puntos: 2440, puesto: 7 },
        { nombre: "PABLO RIOS", puntos: 2440, puesto: 7 }
      ] },
      { opcion: 16, orden: ["Argentina", "España", "Inglaterra", "Francia"], ganadores: [
        { nombre: "PABLO TORO", puntos: 2710, puesto: 1 },
        { nombre: "JOSE ANDRÉS RIOS", puntos: 2585, puesto: 2 },
        { nombre: "JAIRO ENRIQUE CASTRO", puntos: 2575, puesto: 3 },
        { nombre: "MILCIADES DUSAN", puntos: 2465, puesto: 4 },
        { nombre: "PEDRO SALAMANCA", puntos: 2410, puesto: 5 },
        { nombre: "RUBEN DARIO ORTIZ", puntos: 2385, puesto: 6 },
        { nombre: "KATHERINE TINJACA", puntos: 2320, puesto: 7 }
      ] }
    ];

    /*
      Lista fija de equipos disponibles. No se agregan mas opciones al buscador.
    */
    const EQUIPOS = ["Francia", "Argentina", "España", "Inglaterra"];
    const BANDERAS = {
      Francia: "🇫🇷",
      Argentina: "🇦🇷",
      España: "🇪🇸",
      Inglaterra: "🏴󠁧󠁢󠁥󠁮󠁧󠁿"
    };

    const CAMPOS = [
      { id: "campeon", etiqueta: "Seleccionar Campeón" },
      { id: "subcampeon", etiqueta: "Seleccionar Subcampeón" },
      { id: "tercero", etiqueta: "Seleccionar Tercero" },
      { id: "cuarto", etiqueta: "Seleccionar Cuarto" }
    ];

    const formulario = document.querySelector("#formulario-polla");
    const resultados = document.querySelector("#resultados");

    inicializarSelects();
    formulario.addEventListener("submit", buscarEscenario);

    function inicializarSelects() {
      CAMPOS.forEach(({ id }) => {
        document.querySelector(`#${id}`).addEventListener("change", actualizarSelects);
      });

      actualizarSelects();
    }

    function actualizarSelects() {
      CAMPOS.forEach(({ id, etiqueta }) => {
        const select = document.querySelector(`#${id}`);
        const valorActual = select.value;

        select.innerHTML = "";
        select.appendChild(crearOpcion("", etiqueta));

        EQUIPOS.forEach((equipo) => {
          select.appendChild(crearOpcion(equipo, formatearEquipo(equipo)));
        });

        if (valorActual) {
          select.value = valorActual;
        }
      });
    }

    function crearOpcion(valor, texto) {
      const option = document.createElement("option");
      option.value = valor;
      option.textContent = texto;
      return option;
    }

    function obtenerSeleccion() {
      return CAMPOS.map(({ id }) => document.querySelector(`#${id}`).value);
    }

    function buscarEscenario(evento) {
      evento.preventDefault();
      actualizarSelects();

      const seleccion = obtenerSeleccion();

      if (seleccion.some((valor) => valor === "")) {
        mostrarAdvertencia("Selecciona los cuatro puestos antes de buscar.");
        return;
      }

      const escenario = DATOS_POLLA.find((fila) => {
        return fila.orden.length === seleccion.length &&
          fila.orden.every((equipo, indice) => equipo === seleccion[indice]);
      });

      if (!escenario) {
        mostrarSinRegistros(seleccion);
        return;
      }

      mostrarResultado(escenario);
    }

    function mostrarResultado(escenario) {
      resultados.innerHTML = `
        <div class="result-content">
          <div class="scenario">
            <span class="scenario-title">Escenario consultado</span>
            <ol class="scenario-list">
              ${escenario.orden.map((equipo, indice) => `
                <li>${indice + 1}. ${escaparHtml(formatearEquipo(equipo))}</li>
              `).join("")}
            </ol>
          </div>

          <div class="winner-grid">
            ${escenario.ganadores.map((ganador) => `
              <article class="winner-card">
                <small>Puesto ${escaparHtml(String(ganador.puesto))}</small>
                <strong>${escaparHtml(ganador.nombre)}</strong>
                <p class="points">${escaparHtml(formatearPuntos(ganador.puntos))} puntos</p>
              </article>
            `).join("")}
          </div>

          <div class="detail-row">
            <span>Opción ${escaparHtml(String(escenario.opcion))}</span>
            <span>${escenario.ganadores.length} registros encontrados</span>
          </div>
        </div>
      `;
    }

    function mostrarSinRegistros(seleccion) {
      resultados.innerHTML = `
        <div class="warning-state">
          <div>
            <strong>No hay registros para esta combinación exacta de resultados.</strong>
            <br>
            Escenario consultado: ${seleccion.map(formatearEquipo).map(escaparHtml).join(" / ")}
          </div>
        </div>
      `;
    }

    function mostrarAdvertencia(mensaje) {
      resultados.innerHTML = `
        <div class="warning-state">
          <strong>${escaparHtml(mensaje)}</strong>
        </div>
      `;
    }

    function escaparHtml(valor) {
      return valor
        .replaceAll("&", "&amp;")
        .replaceAll("<", "&lt;")
        .replaceAll(">", "&gt;")
        .replaceAll('"', "&quot;")
        .replaceAll("'", "&#039;");
    }

    function formatearEquipo(equipo) {
      return `${BANDERAS[equipo] || ""} ${equipo}`.trim();
    }

    function formatearPuntos(puntos) {
      return new Intl.NumberFormat("es-CO").format(puntos);
    }
  </script>
</body>
</html>
