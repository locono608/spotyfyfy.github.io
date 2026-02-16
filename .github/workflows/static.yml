<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SoundPlayer - Lecteur Musical</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #fff;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 30px 0;
        }

        header h1 {
            font-size: 3em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .info-box {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            font-size: 0.9em;
        }

        .info-box strong {
            display: block;
            margin-bottom: 5px;
        }

        .info-box code {
            background: rgba(0, 0, 0, 0.2);
            padding: 2px 6px;
            border-radius: 3px;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 350px;
            gap: 30px;
            margin-bottom: 150px;
        }

        .section {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.2);
        }

        h2 {
            margin-bottom: 20px;
            font-size: 1.8em;
        }

        .add-track-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-bottom: 30px;
        }

        input, select, button {
            padding: 12px 20px;
            border: none;
            border-radius: 10px;
            font-size: 1em;
        }

        input, select {
            background: rgba(255, 255, 255, 0.9);
            color: #333;
        }

        input:focus, select:focus {
            outline: 3px solid #ff6b6b;
        }

        button {
            background: linear-gradient(135deg, #ff6b6b, #ee5a6f);
            color: white;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .track-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .track-item {
            background: rgba(255, 255, 255, 0.15);
            padding: 15px;
            border-radius: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: background 0.3s;
        }

        .track-item:hover {
            background: rgba(255, 255, 255, 0.25);
        }

        .track-item.playing {
            background: rgba(255, 107, 107, 0.4);
            border: 2px solid #ff6b6b;
        }

        .track-info {
            flex: 1;
        }

        .track-title {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .track-url {
            font-size: 0.8em;
            opacity: 0.7;
            word-break: break-all;
        }

        .track-actions {
            display: flex;
            gap: 10px;
        }

        .btn-small {
            padding: 8px 15px;
            font-size: 0.9em;
            background: rgba(255, 255, 255, 0.2);
        }

        .btn-play {
            background: linear-gradient(135deg, #4CAF50, #45a049);
        }

        .btn-delete {
            background: linear-gradient(135deg, #f44336, #da190b);
        }

        .playlist-section {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .create-playlist {
            display: flex;
            gap: 10px;
        }

        .create-playlist input {
            flex: 1;
        }

        .playlist-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .playlist-item {
            background: rgba(255, 255, 255, 0.15);
            padding: 15px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .playlist-item:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateX(5px);
        }

        .playlist-item.active {
            background: rgba(255, 215, 0, 0.3);
            border: 2px solid gold;
        }

        .playlist-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .playlist-name {
            font-weight: bold;
            font-size: 1.1em;
        }

        .playlist-count {
            font-size: 0.9em;
            opacity: 0.8;
        }

        .player {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(20px);
            padding: 20px;
            box-shadow: 0 -5px 20px rgba(0,0,0,0.5);
            z-index: 1000;
        }

        .player-content {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .player-info {
            text-align: center;
        }

        .player-title {
            font-size: 1.2em;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .player-controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            align-items: center;
        }

        .player-controls button {
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.2);
        }

        .player-controls button:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        iframe {
            width: 100%;
            height: 166px;
            border: none;
            border-radius: 10px;
        }

        .empty-state {
            text-align: center;
            padding: 40px;
            opacity: 0.6;
        }

        .error-message {
            background: rgba(255, 0, 0, 0.2);
            border: 1px solid rgba(255, 0, 0, 0.5);
            padding: 10px;
            border-radius: 5px;
            margin-top: 10px;
            display: none;
        }

        @media (max-width: 968px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🎵 SoundPlayer</h1>
            <p>Votre lecteur de musique SoundCloud personnel</p>
        </header>

        <div class="main-content">
            <div class="section">
                <h2>📚 Ma Bibliothèque</h2>
                
                <div class="info-box">
                    <strong>📌 Comment obtenir l'URL correcte :</strong>
                    1. Allez sur SoundCloud et trouvez un morceau<br>
                    2. Cliquez sur "Partager" sous le morceau<br>
                    3. Copiez le lien complet (ex: <code>https://soundcloud.com/artist/track-name</code>)<br>
                    4. Collez-le dans le champ ci-dessous
                </div>

                <div class="add-track-form">
                    <input type="text" id="trackTitle" placeholder="Titre de la musique">
                    <input type="url" id="trackUrl" placeholder="URL SoundCloud complète">
                    <button onclick="addTrack()">➕ Ajouter à la bibliothèque</button>
                    <div id="errorMessage" class="error-message"></div>
                </div>

                <div id="trackList" class="track-list"></div>
            </div>

            <div class="section playlist-section">
                <h2>🎼 Mes Playlists</h2>
                
                <div class="create-playlist">
                    <input type="text" id="playlistName" placeholder="Nom de la playlist">
                    <button onclick="createPlaylist()">Créer</button>
                </div>

                <div id="playlistList" class="playlist-list"></div>

                <div style="margin-top: 20px;">
                    <h3 style="margin-bottom: 10px;">Ajouter à une playlist:</h3>
                    <select id="trackSelect" style="margin-bottom: 10px;">
                        <option value="">Sélectionner une musique</option>
                    </select>
                    <select id="playlistSelect" style="margin-bottom: 10px;">
                        <option value="">Sélectionner une playlist</option>
                    </select>
                    <button onclick="addToPlaylist()">Ajouter</button>
                </div>
            </div>
        </div>
    </div>

    <div class="player">
        <div class="player-content">
            <div class="player-info">
                <div class="player-title" id="currentTitle">Aucune musique en lecture</div>
            </div>
            <div id="playerFrame"></div>
            <div class="player-controls">
                <button onclick="previousTrack()">⏮️ Précédent</button>
                <button onclick="nextTrack()">⏭️ Suivant</button>
            </div>
        </div>
    </div>

    <script>
        let tracks = JSON.parse(localStorage.getItem('tracks')) || [];
        let playlists = JSON.parse(localStorage.getItem('playlists')) || [];
        let currentTrackIndex = -1;
        let currentPlaylist = null;

        function saveData() {
            localStorage.setItem('tracks', JSON.stringify(tracks));
            localStorage.setItem('playlists', JSON.stringify(playlists));
        }

        function showError(message) {
            const errorEl = document.getElementById('errorMessage');
            errorEl.textContent = message;
            errorEl.style.display = 'block';
            setTimeout(() => {
                errorEl.style.display = 'none';
            }, 5000);
        }

        function validateSoundCloudUrl(url) {
            // Nettoyer l'URL
            url = url.trim();
            
            // Vérifier que c'est bien un lien SoundCloud
            if (!url.includes('soundcloud.com/')) {
                return null;
            }

            // Retirer les paramètres inutiles et s'assurer du format correct
            try {
                const urlObj = new URL(url);
                // Format: https://soundcloud.com/artist/track
                if (urlObj.hostname === 'soundcloud.com' || urlObj.hostname === 'www.soundcloud.com') {
                    return urlObj.protocol + '//' + urlObj.hostname + urlObj.pathname;
                }
            } catch (e) {
                return null;
            }
            
            return null;
        }

        function addTrack() {
            const title = document.getElementById('trackTitle').value.trim();
            const url = document.getElementById('trackUrl').value.trim();

            if (!title || !url) {
                showError('Veuillez remplir tous les champs');
                return;
            }

            const validUrl = validateSoundCloudUrl(url);
            if (!validUrl) {
                showError('URL SoundCloud invalide. Utilisez le format: https://soundcloud.com/artist/track-name');
                return;
            }

            tracks.push({ id: Date.now(), title, url: validUrl });
            saveData();
            updateUI();

            document.getElementById('trackTitle').value = '';
            document.getElementById('trackUrl').value = '';
            
            showError('✅ Musique ajoutée avec succès !');
            document.getElementById('errorMessage').style.background = 'rgba(0, 255, 0, 0.2)';
            document.getElementById('errorMessage').style.borderColor = 'rgba(0, 255, 0, 0.5)';
        }

        function deleteTrack(id) {
            if (confirm('Supprimer cette musique ?')) {
                tracks = tracks.filter(t => t.id !== id);
                playlists.forEach(p => {
                    p.tracks = p.tracks.filter(tid => tid !== id);
                });
                saveData();
                updateUI();
            }
        }

        function playTrack(id, playlistId = null) {
            const track = tracks.find(t => t.id === id);
            if (!track) return;

            currentPlaylist = playlistId;
            
            if (currentPlaylist) {
                const playlist = playlists.find(p => p.id === currentPlaylist);
                currentTrackIndex = playlist.tracks.indexOf(id);
            } else {
                currentTrackIndex = tracks.findIndex(t => t.id === id);
            }

            // Encoder l'URL pour l'API SoundCloud
            const encodedUrl = encodeURIComponent(track.url);
            const embedUrl = `https://w.soundcloud.com/player/?url=${encodedUrl}&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true`;
            
            document.getElementById('playerFrame').innerHTML = `
                <iframe scrolling="no" frameborder="no" allow="autoplay" src="${embedUrl}"></iframe>
            `;
            document.getElementById('currentTitle').textContent = track.title;
            
            updateUI();
        }

        function nextTrack() {
            let trackList;
            if (currentPlaylist) {
                const playlist = playlists.find(p => p.id === currentPlaylist);
                trackList = playlist.tracks;
            } else {
                trackList = tracks.map(t => t.id);
            }

            if (trackList.length === 0) return;

            currentTrackIndex = (currentTrackIndex + 1) % trackList.length;
            playTrack(trackList[currentTrackIndex], currentPlaylist);
        }

        function previousTrack() {
            let trackList;
            if (currentPlaylist) {
                const playlist = playlists.find(p => p.id === currentPlaylist);
                trackList = playlist.tracks;
            } else {
                trackList = tracks.map(t => t.id);
            }

            if (trackList.length === 0) return;

            currentTrackIndex = currentTrackIndex - 1;
            if (currentTrackIndex < 0) currentTrackIndex = trackList.length - 1;
            playTrack(trackList[currentTrackIndex], currentPlaylist);
        }

        function createPlaylist() {
            const name = document.getElementById('playlistName').value.trim();
            if (!name) {
                alert('Donnez un nom à votre playlist');
                return;
            }

            playlists.push({ id: Date.now(), name, tracks: [] });
            saveData();
            updateUI();

            document.getElementById('playlistName').value = '';
        }

        function deletePlaylist(id) {
            if (confirm('Supprimer cette playlist ?')) {
                playlists = playlists.filter(p => p.id !== id);
                if (currentPlaylist === id) {
                    currentPlaylist = null;
                }
                saveData();
                updateUI();
            }
        }

        function addToPlaylist() {
            const trackId = parseInt(document.getElementById('trackSelect').value);
            const playlistId = parseInt(document.getElementById('playlistSelect').value);

            if (!trackId || !playlistId) {
                alert('Sélectionnez une musique et une playlist');
                return;
            }

            const playlist = playlists.find(p => p.id === playlistId);
            if (!playlist.tracks.includes(trackId)) {
                playlist.tracks.push(trackId);
                saveData();
                updateUI();
                alert('✅ Musique ajoutée à la playlist !');
            } else {
                alert('Cette musique est déjà dans la playlist');
            }
        }

        function playPlaylist(playlistId) {
            const playlist = playlists.find(p => p.id === playlistId);
            if (playlist.tracks.length === 0) {
                alert('Cette playlist est vide');
                return;
            }

            currentPlaylist = playlistId;
            playTrack(playlist.tracks[0], playlistId);
        }

        function updateUI() {
            // Update track list
            const trackListEl = document.getElementById('trackList');
            if (tracks.length === 0) {
                trackListEl.innerHTML = '<div class="empty-state">Aucune musique. Ajoutez votre première musique !</div>';
            } else {
                trackListEl.innerHTML = tracks.map(track => {
                    const isPlaying = currentPlaylist === null && tracks[currentTrackIndex]?.id === track.id;
                    return `
                        <div class="track-item ${isPlaying ? 'playing' : ''}">
                            <div class="track-info">
                                <div class="track-title">${track.title}</div>
                                <div class="track-url">${track.url}</div>
                            </div>
                            <div class="track-actions">
                                <button class="btn-small btn-play" onclick="playTrack(${track.id})">▶️</button>
                                <button class="btn-small btn-delete" onclick="deleteTrack(${track.id})">🗑️</button>
                            </div>
                        </div>
                    `;
                }).join('');
            }

            // Update playlist list
            const playlistListEl = document.getElementById('playlistList');
            if (playlists.length === 0) {
                playlistListEl.innerHTML = '<div class="empty-state">Aucune playlist. Créez-en une !</div>';
            } else {
                playlistListEl.innerHTML = playlists.map(playlist => {
                    const isActive = currentPlaylist === playlist.id;
                    return `
                        <div class="playlist-item ${isActive ? 'active' : ''}" onclick="playPlaylist(${playlist.id})">
                            <div class="playlist-header">
                                <span class="playlist-name">${playlist.name}</span>
                                <button class="btn-small btn-delete" onclick="event.stopPropagation(); deletePlaylist(${playlist.id})">🗑️</button>
                            </div>
                            <div class="playlist-count">${playlist.tracks.length} morceau(x)</div>
                        </div>
                    `;
                }).join('');
            }

            // Update selects
            const trackSelect = document.getElementById('trackSelect');
            trackSelect.innerHTML = '<option value="">Sélectionner une musique</option>' + 
                tracks.map(t => `<option value="${t.id}">${t.title}</option>`).join('');

            const playlistSelect = document.getElementById('playlistSelect');
            playlistSelect.innerHTML = '<option value="">Sélectionner une playlist</option>' + 
                playlists.map(p => `<option value="${p.id}">${p.name}</option>`).join('');
        }

        // Initialize
        updateUI();
    </script>
</body>
</html>
