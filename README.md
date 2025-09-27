# Mel-LLU-ANIMADORAS-THINGS
Paginas con las que me apoyo para info nada estrabagante
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Base de Datos para Equipos - Estadísticas de Juego</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #1a1a2e;
            color: #e6e6e6;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        h1 {
            color: #e94560;
            margin-bottom: 10px;
        }
        
        .description {
            color: #b8b8b8;
            max-width: 800px;
            margin: 0 auto 20px;
        }
        
        .teams-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        @media (max-width: 1000px) {
            .teams-container {
                grid-template-columns: 1fr;
            }
        }
        
        .team-section {
            background-color: #16213e;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
            padding: 20px;
        }
        
        .team-blue {
            border-left: 5px solid #3498db;
        }
        
        .team-red {
            border-left: 5px solid #e74c3c;
        }
        
        .team-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #0f3460;
        }
        
        .team-title-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .team-title {
            font-size: 24px;
            font-weight: 700;
        }
        
        .team-blue .team-title {
            color: #3498db;
        }
        
        .team-red .team-title {
            color: #e74c3c;
        }
        
        .edit-team-name {
            background: none;
            border: none;
            color: #b8b8b8;
            cursor: pointer;
            font-size: 16px;
            padding: 5px;
        }
        
        .team-name-input {
            background-color: #0f3460;
            border: 1px solid #3498db;
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 20px;
            font-weight: bold;
            width: 200px;
        }
        
        .team-stats {
            display: flex;
            gap: 15px;
        }
        
        .stat {
            background-color: #0f3460;
            padding: 8px 15px;
            border-radius: 4px;
            font-weight: 600;
        }
        
        .form-container {
            background-color: #0f3460;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: #e94560;
        }
        
        input, textarea, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #1a1a2e;
            border-radius: 4px;
            font-size: 16px;
            background-color: #1a1a2e;
            color: #e6e6e6;
        }
        
        textarea {
            height: 80px;
            resize: vertical;
        }
        
        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }
        
        button {
            background-color: #e94560;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
            margin-right: 10px;
            margin-top: 10px;
        }
        
        button:hover {
            background-color: #d63447;
        }
        
        .btn-blue {
            background-color: #3498db;
        }
        
        .btn-blue:hover {
            background-color: #2980b9;
        }
        
        .btn-red {
            background-color: #e74c3c;
        }
        
        .btn-red:hover {
            background-color: #c0392b;
        }
        
        .btn-danger {
            background-color: #ff6b6b;
        }
        
        .btn-danger:hover {
            background-color: #ee5a5a;
        }
        
        .players-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 15px;
        }
        
        .player-card {
            background-color: #0f3460;
            border-radius: 8px;
            padding: 15px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            transition: transform 0.3s;
        }
        
        .player-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }
        
        .player-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid #1a1a2e;
        }
        
        .player-name {
            font-weight: 600;
            font-size: 18px;
            color: #e94560;
        }
        
        .player-champion {
            font-style: italic;
            color: #b8b8b8;
            margin-bottom: 10px;
        }
        
        .player-emotes {
            font-size: 24px;
            margin-bottom: 15px;
            min-height: 40px;
            word-wrap: break-word;
        }
        
        .player-stats {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }
        
        .player-stat {
            text-align: center;
        }
        
        .stat-value {
            font-size: 20px;
            font-weight: 700;
        }
        
        .stat-label {
            font-size: 12px;
            color: #b8b8b8;
        }
        
        .player-actions {
            display: flex;
            gap: 10px;
        }
        
        .player-actions button {
            flex: 1;
            padding: 8px;
            font-size: 14px;
        }
        
        .empty-message {
            text-align: center;
            padding: 40px;
            color: #7f8c8d;
            font-style: italic;
            grid-column: 1 / -1;
        }
        
        .instructions {
            background-color: #0f3460;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            font-size: 14px;
        }
        
        .global-actions {
            text-align: center;
            margin-top: 30px;
        }
        
        .team-name-form {
            display: flex;
            gap: 10px;
            align-items: center;
        }
        
        .save-team-name {
            padding: 5px 10px;
            font-size: 14px;
            margin-top: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Base de Datos para Equipos - Estadísticas de Juego</h1>
            <p class="description">Gestiona dos equipos separados con nombres personalizados, información de jugadores, emotes, campeones, torres derribadas y kills.</p>
        </header>
        
        <div class="instructions">
            <p><strong>Instrucciones:</strong> Selecciona un equipo, ingresa los datos del jugador y haz clic en "Agregar". Los emotes se escriben separados por comas (ej: 😊,😂,😍). Puedes personalizar el nombre de cada equipo haciendo clic en el icono de edición junto al nombre.</p>
        </div>
        
        <div class="form-container">
            <h2>Agregar Nuevo Jugador</h2>
            <form id="player-form">
                <div class="form-row">
                    <div class="form-group">
                        <label for="team">Equipo:</label>
                        <select id="team" required>
                            <option value="">Selecciona un equipo</option>
                            <option value="blue">Equipo Azul</option>
                            <option value="red">Equipo Rojo</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="name">Nombre del Jugador:</label>
                        <input type="text" id="name" required placeholder="Ej: Juan Pérez">
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="emotes">Emotes (separados por comas):</label>
                    <textarea id="emotes" required placeholder="Ej: 😊,😂,😍,🤔"></textarea>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="champion">Campeón:</label>
                        <input type="text" id="champion" required placeholder="Ej: Garen, Yasuo, etc.">
                    </div>
                    
                    <div class="form-group">
                        <label for="towers">Torres Derribadas:</label>
                        <input type="number" id="towers" min="0" value="0" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="kills">Kills:</label>
                        <input type="number" id="kills" min="0" value="0" required>
                    </div>
                </div>
                
                <button type="submit">Agregar Jugador</button>
                <button type="button" id="clear-all">Limpiar toda la base de datos</button>
            </form>
        </div>
        
        <div class="teams-container">
            <div class="team-section team-blue">
                <div class="team-header">
                    <div class="team-title-container">
                        <h2 class="team-title" id="blue-team-name">Equipo Azul</h2>
                        <button class="edit-team-name" onclick="editTeamName('blue')">✏️</button>
                    </div>
                    <div class="team-stats">
                        <div class="stat">Jugadores: <span id="blue-player-count">0</span></div>
                        <div class="stat">Torres: <span id="blue-tower-count">0</span></div>
                        <div class="stat">Kills: <span id="blue-kill-count">0</span></div>
                    </div>
                </div>
                <div id="blue-team-container" class="players-grid">
                    <!-- Jugadores del equipo azul se cargarán aquí -->
                </div>
            </div>
            
            <div class="team-section team-red">
                <div class="team-header">
                    <div class="team-title-container">
                        <h2 class="team-title" id="red-team-name">Equipo Rojo</h2>
                        <button class="edit-team-name" onclick="editTeamName('red')">✏️</button>
                    </div>
                    <div class="team-stats">
                        <div class="stat">Jugadores: <span id="red-player-count">0</span></div>
                        <div class="stat">Torres: <span id="red-tower-count">0</span></div>
                        <div class="stat">Kills: <span id="red-kill-count">0</span></div>
                    </div>
                </div>
                <div id="red-team-container" class="players-grid">
                    <!-- Jugadores del equipo rojo se cargarán aquí -->
                </div>
            </div>
        </div>
        
        <div class="global-actions">
            <button id="swap-teams" class="btn-blue">Intercambiar Equipos</button>
            <button id="reset-stats" class="btn-red">Reiniciar Estadísticas</button>
        </div>
    </div>

    <script>
        // Estructura de datos inicial
        const defaultData = {
            blue: {
                name: "Equipo Azul",
                players: [
                    { name: "Ana", emotes: "😊,😂,😍", champion: "Lux", towers: 2, kills: 5 },
                    { name: "Carlos", emotes: "😎,🤔,🥳", champion: "Yasuo", towers: 1, kills: 8 }
                ]
            },
            red: {
                name: "Equipo Rojo",
                players: [
                    { name: "María", emotes: "🤯,😭,🤩", champion: "Ahri", towers: 3, kills: 7 },
                    { name: "Pedro", emotes: "😴,🤠,👾", champion: "Garen", towers: 0, kills: 3 }
                ]
            }
        };

        // Obtener datos del localStorage o usar los predeterminados
        let teamsData = JSON.parse(localStorage.getItem('teamsDatabase')) || defaultData;

        // Elementos DOM
        const playerForm = document.getElementById('player-form');
        const clearAllButton = document.getElementById('clear-all');
        const swapTeamsButton = document.getElementById('swap-teams');
        const resetStatsButton = document.getElementById('reset-stats');
        
        const blueTeamContainer = document.getElementById('blue-team-container');
        const redTeamContainer = document.getElementById('red-team-container');
        
        // Contadores de equipo
        const bluePlayerCount = document.getElementById('blue-player-count');
        const blueTowerCount = document.getElementById('blue-tower-count');
        const blueKillCount = document.getElementById('blue-kill-count');
        const blueTeamName = document.getElementById('blue-team-name');
        
        const redPlayerCount = document.getElementById('red-player-count');
        const redTowerCount = document.getElementById('red-tower-count');
        const redKillCount = document.getElementById('red-kill-count');
        const redTeamName = document.getElementById('red-team-name');

        // Función para guardar datos en localStorage
        function saveData() {
            localStorage.setItem('teamsDatabase', JSON.stringify(teamsData));
        }

        // Función para actualizar las estadísticas de los equipos
        function updateTeamStats() {
            // Estadísticas del equipo azul
            const bluePlayers = teamsData.blue.players.length;
            const blueTowers = teamsData.blue.players.reduce((sum, player) => sum + player.towers, 0);
            const blueKills = teamsData.blue.players.reduce((sum, player) => sum + player.kills, 0);
            
            bluePlayerCount.textContent = bluePlayers;
            blueTowerCount.textContent = blueTowers;
            blueKillCount.textContent = blueKills;
            blueTeamName.textContent = teamsData.blue.name;
            
            // Estadísticas del equipo rojo
            const redPlayers = teamsData.red.players.length;
            const redTowers = teamsData.red.players.reduce((sum, player) => sum + player.towers, 0);
            const redKills = teamsData.red.players.reduce((sum, player) => sum + player.kills, 0);
            
            redPlayerCount.textContent = redPlayers;
            redTowerCount.textContent = redTowers;
            redKillCount.textContent = redKills;
            redTeamName.textContent = teamsData.red.name;
        }

        // Función para mostrar los jugadores en la página
        function renderPlayers() {
            // Limpiar contenedores
            blueTeamContainer.innerHTML = '';
            redTeamContainer.innerHTML = '';
            
            // Mostrar jugadores del equipo azul
            if (teamsData.blue.players.length === 0) {
                blueTeamContainer.innerHTML = '<div class="empty-message">No hay jugadores en el equipo azul</div>';
            } else {
                teamsData.blue.players.forEach((player, index) => {
                    const playerCard = createPlayerCard(player, index, 'blue');
                    blueTeamContainer.appendChild(playerCard);
                });
            }
            
            // Mostrar jugadores del equipo rojo
            if (teamsData.red.players.length === 0) {
                redTeamContainer.innerHTML = '<div class="empty-message">No hay jugadores en el equipo rojo</div>';
            } else {
                teamsData.red.players.forEach((player, index) => {
                    const playerCard = createPlayerCard(player, index, 'red');
                    redTeamContainer.appendChild(playerCard);
                });
            }
            
            // Actualizar estadísticas
            updateTeamStats();
        }

        // Función para crear una tarjeta de jugador
        function createPlayerCard(player, index, team) {
            const playerCard = document.createElement('div');
            playerCard.className = 'player-card';
            playerCard.innerHTML = `
                <div class="player-header">
                    <div class="player-name">${player.name}</div>
                    <button class="btn-danger" onclick="deletePlayer('${team}', ${index})">Eliminar</button>
                </div>
                <div class="player-champion">Campeón: ${player.champion}</div>
                <div class="player-emotes">${player.emotes}</div>
                <div class="player-stats">
                    <div class="player-stat">
                        <div class="stat-value">${player.towers}</div>
                        <div class="stat-label">Torres</div>
                    </div>
                    <div class="player-stat">
                        <div class="stat-value">${player.kills}</div>
                        <div class="stat-label">Kills</div>
                    </div>
                </div>
                <div class="player-actions">
                    <button class="btn-blue" onclick="movePlayer('${team}', ${index}, '${team === 'blue' ? 'red' : 'blue'}')">
                        Mover a ${team === 'blue' ? teamsData.red.name : teamsData.blue.name}
                    </button>
                    <button onclick="editPlayer('${team}', ${index})">Editar</button>
                </div>
            `;
            return playerCard;
        }

        // Función para agregar un nuevo jugador
        function addPlayer(team, name, emotes, champion, towers, kills) {
            teamsData[team].players.push({ name, emotes, champion, towers: parseInt(towers), kills: parseInt(kills) });
            saveData();
            renderPlayers();
        }

        // Función para eliminar un jugador
        function deletePlayer(team, index) {
            if (confirm('¿Estás seguro de que quieres eliminar este jugador?')) {
                teamsData[team].players.splice(index, 1);
                saveData();
                renderPlayers();
            }
        }

        // Función para mover un jugador entre equipos
        function movePlayer(fromTeam, index, toTeam) {
            const player = teamsData[fromTeam].players[index];
            teamsData[fromTeam].players.splice(index, 1);
            teamsData[toTeam].players.push(player);
            saveData();
            renderPlayers();
        }

        // Función para editar un jugador
        function editPlayer(team, index) {
            const player = teamsData[team].players[index];
            
            // Llenar el formulario con los datos del jugador
            document.getElementById('team').value = team;
            document.getElementById('name').value = player.name;
            document.getElementById('emotes').value = player.emotes;
            document.getElementById('champion').value = player.champion;
            document.getElementById('towers').value = player.towers;
            document.getElementById('kills').value = player.kills;
            
            // Eliminar el jugador actual (será reemplazado con los datos editados)
            teamsData[team].players.splice(index, 1);
            saveData();
            renderPlayers();
        }

        // Función para editar el nombre de un equipo
        function editTeamName(team) {
            const teamNameElement = document.getElementById(`${team}-team-name`);
            const currentName = teamNameElement.textContent;
            
            // Crear formulario de edición
            teamNameElement.outerHTML = `
                <form class="team-name-form" onsubmit="saveTeamName('${team}', this); return false;">
                    <input type="text" class="team-name-input" value="${currentName}" required>
                    <button type="submit" class="save-team-name">Guardar</button>
                </form>
            `;
        }

        // Función para guardar el nombre de un equipo
        function saveTeamName(team, form) {
            const newName = form.querySelector('.team-name-input').value;
            teamsData[team].name = newName;
            saveData();
            renderPlayers();
        }

        // Función para limpiar toda la base de datos
        function clearAllData() {
            if (confirm('¿Estás seguro de que quieres eliminar TODOS los registros? Esta acción no se puede deshacer.')) {
                teamsData = { 
                    blue: { name: "Equipo Azul", players: [] }, 
                    red: { name: "Equipo Rojo", players: [] } 
                };
                saveData();
                renderPlayers();
            }
        }

        // Función para intercambiar equipos
        function swapTeams() {
            if (confirm('¿Estás seguro de que quieres intercambiar los equipos?')) {
                const temp = teamsData.blue;
                teamsData.blue = teamsData.red;
                teamsData.red = temp;
                saveData();
                renderPlayers();
            }
        }

        // Función para reiniciar estadísticas
        function resetStats() {
            if (confirm('¿Estás seguro de que quieres reiniciar todas las estadísticas (torres y kills)?')) {
                teamsData.blue.players.forEach(player => {
                    player.towers = 0;
                    player.kills = 0;
                });
                
                teamsData.red.players.forEach(player => {
                    player.towers = 0;
                    player.kills = 0;
                });
                
                saveData();
                renderPlayers();
            }
        }

        // Manejar el envío del formulario
        playerForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const teamInput = document.getElementById('team');
            const nameInput = document.getElementById('name');
            const emotesInput = document.getElementById('emotes');
            const championInput = document.getElementById('champion');
            const towersInput = document.getElementById('towers');
            const killsInput = document.getElementById('kills');
            
            const team = teamInput.value;
            const name = nameInput.value.trim();
            const emotes = emotesInput.value.trim();
            const champion = championInput.value.trim();
            const towers = towersInput.value;
            const kills = killsInput.value;
            
            if (team && name && emotes && champion) {
                addPlayer(team, name, emotes, champion, towers, kills);
                
                // Limpiar el formulario
                nameInput.value = '';
                emotesInput.value = '';
                championInput.value = '';
                towersInput.value = '0';
                killsInput.value = '0';
                teamInput.focus();
            }
        });

        // Asignar event listeners a los botones globales
        clearAllButton.addEventListener('click', clearAllData);
        swapTeamsButton.addEventListener('click', swapTeams);
        resetStatsButton.addEventListener('click', resetStats);

        // Hacer las funciones disponibles globalmente para los eventos onclick
        window.deletePlayer = deletePlayer;
        window.movePlayer = movePlayer;
        window.editPlayer = editPlayer;
        window.editTeamName = editTeamName;
        window.saveTeamName = saveTeamName;

        // Inicializar la página
        document.addEventListener('DOMContentLoaded', function() {
            renderPlayers();
        });
    </script>
</body>
</html>
