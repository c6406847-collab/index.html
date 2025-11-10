# index.html


<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Perfil Personalizado Horizontal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        /* Configuraciones de fuente y fondo de pantalla */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #1e1e2e; /* Color de fondo por defecto */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            transition: background-image 0.5s ease-in-out, background-color 0.5s ease-in-out;
            background-size: cover;
            background-position: center;
        }

        /* Estilo para el contenedor principal del perfil (HORIZONTAL) */
        .profile-card {
            background: #282a36; /* Color de tarjeta oscura (similar a Discord/Steam) */
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
            max-width: 1000px; /* Más ancho para el diseño horizontal */
            width: 90%;
            display: flex; /* Habilita el diseño horizontal */
            overflow: hidden;
            min-height: 400px;
        }
        
        /* Contenedor del contenido principal y foto */
        .profile-content {
            flex-grow: 1;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        /* Contenedor de los controles/personalización (Panel derecho) */
        .customizer {
            background: #44475a;
            width: 300px; /* Ancho fijo para el panel de controles */
            padding: 20px;
            border-left: 1px solid #6272a4;
            color: #f8f8f2;
            overflow-y: auto; /* Permite desplazamiento si hay muchos controles */
        }

        /* Estilo para la imagen de perfil */
        #profileImage {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid #50fa7b; /* Borde de color de acento */
            margin-right: 20px;
            flex-shrink: 0; /* Evita que la imagen se achique */
        }

        /* Estilo para la sección de Playlists/Widgets */
        .playlist-widget {
            background: #6272a4;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
        }

        /* Estilo general para los campos de entrada */
        .input-field {
            w-full p-2 rounded-lg bg-[#282a36] border border-[#6272a4] text-[#f8f8f2] focus:ring-[#bd93f9] focus:border-[#bd93f9];
        }

        /* Estilo para el botón de control */
        .control-button {
            padding: 8px 15px;
            margin-top: 5px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s;
        }
    </style>
</head>
<body id="bodyElement">

    <div class="profile-card">
        
        <div class="profile-content">
            <div class="flex items-start mb-6">
                <img id="profileImage" 
                     src="https://placehold.co/100x100/50fa7b/282a36?text=Yo" 
                     alt="Foto de Perfil">
                
                <div>
                    <h1 class="text-4xl font-extrabold text-[#bd93f9]" id="profileName">Nombre de Usuario</h1>
                    <p class="text-[#50fa7b] text-md mt-1">🟢 En línea | Perfil Personal</p>
                    <p class="text-white text-md mt-2 italic" id="profileBio">"Mi biografía simple: Me gusta la música y personalizar cosas."</p>
                </div>
            </div>

            <div class="playlist-widget">
                <h3 class="text-xl font-semibold mb-3 text-white">🎶 Playlists Favoritas</h3>
                
                <p class="text-sm text-[#f8f8f2] mb-2">Espacio para tu reproductor incrustado o enlaces clave:</p>
                
                <a id="playlistLink1" href="https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M" target="_blank" class="block w-full p-2 mb-2 bg-[#ff79c6] hover:bg-[#bd93f9] text-[#282a36] font-semibold text-center rounded-md transition-colors">
                    Link de Playlist 1
                </a>
                
                <a id="playlistLink2" href="http://googleusercontent.com/youtube.com/0" target="_blank" class="block w-full p-2 bg-[#ff79c6] hover:bg-[#bd93f9] text-[#282a36] font-semibold text-center rounded-md transition-colors">
                    Link de Playlist 2 (YouTube)
                </a>
            </div>
        </div>

        <div class="customizer">
            <h3 class="text-xl font-bold mb-5 text-[#f1fa8c]">🔧 Controles de Personalización</h3>
            
            <div class="mb-4">
                <label for="newImageUrl" class="block text-sm font-medium mb-1">URL de la Nueva Foto:</label>
                <input type="url" id="newImageUrl" placeholder="Ej: https://tufoto.com/perfil.jpg" class="input-field">
                <button onclick="updateProfileImage()" class="control-button bg-[#bd93f9] hover:bg-[#ff79c6] text-[#282a36] w-full">Aplicar Foto</button>
            </div>
            
            <div class="mb-4">
                <label for="backgroundSelector" class="block text-sm font-medium mb-1">Elegir Fondo:</label>
                <select id="backgroundSelector" onchange="updateBackground()" class="input-field">
                    <option value="default">Fondo por Defecto (Oscuro)</option>
                    <option value="city">Ciudad Futurista (Imagen)</option>
                    <option value="neon">Grid Neón (Imagen)</option>
                    <option value="forest">Bosque Misterioso (Imagen)</option>
                </select>
            </div>

            <div class="mb-4">
                <label for="newProfileName" class="block text-sm font-medium mb-1">Nuevo Nombre:</label>
                <input type="text" id="newProfileName" placeholder="Tu nuevo alias" class="input-field">
                <button onclick="updateProfileName()" class="control-button bg-[#bd93f9] hover:bg-[#ff79c6] text-[#282a36] w-full">Aplicar Nombre</button>
            </div>
            
            <div class="mb-4">
                <label for="newProfileBio" class="block text-sm font-medium mb-1">Nueva Biografía:</label>
                <input type="text" id="newProfileBio" placeholder="Tu estado o frase favorita" class="input-field">
                <button onclick="updateProfileBio()" class="control-button bg-[#bd93f9] hover:bg-[#ff79c6] text-[#282a36] w-full">Aplicar Biografía</button>
            </div>
            
            <div class="mb-4">
                <label for="newPlaylistLink1" class="block text-sm font-medium mb-1">URL Playlist 1:</label>
                <input type="url" id="newPlaylistLink1" placeholder="URL de Spotify, etc." class="input-field mb-1">
                <label for="newPlaylistName1" class="block text-sm font-medium mb-1">Texto Link 1:</label>
                <input type="text" id="newPlaylistName1" placeholder="Ej: Mi Rock Favorito" class="input-field">
                <button onclick="updatePlaylistLink(1)" class="control-button bg-[#ff79c6] hover:bg-[#bd93f9] text-[#282a36] w-full">Aplicar Link 1</button>
            </div>
            
            <div class="mb-4">
                <label for="newPlaylistLink2" class="block text-sm font-medium mb-1">URL Playlist 2:</label>
                <input type="url" id="newPlaylistLink2" placeholder="URL de YouTube, etc." class="input-field mb-1">
                <label for="newPlaylistName2" class="block text-sm font-medium mb-1">Texto Link 2:</label>
                <input type="text" id="newPlaylistName2" placeholder="Ej: Música para estudiar" class="input-field">
                <button onclick="updatePlaylistLink(2)" class="control-button bg-[#ff79c6] hover:bg-[#bd93f9] text-[#282a36] w-full">Aplicar Link 2</button>
            </div>
        </div>

    </div>

    <script>
        // --- VARIABLES GLOBALES Y ENLACES DE IMAGENES ---
        const backgroundImages = {
            default: 'none',
            city: 'https://placehold.co/1920x1080/000000/F5F5F5/png?text=Ciudad+Futurista', 
            neon: 'https://placehold.co/1920x1080/1a002b/a020f0/png?text=Grid+Neon+Retro', 
            forest: 'https://placehold.co/1920x1080/1e2b1e/3CB371/png?text=Bosque+Misterioso', 
        };

        // Elementos del DOM
        const bodyElement = document.getElementById('bodyElement');
        const profileImageElement = document.getElementById('profileImage');
        const profileNameElement = document.getElementById('profileName');
        const profileBioElement = document.getElementById('profileBio');
        const playlistLink1Element = document.getElementById('playlistLink1');
        const playlistLink2Element = document.getElementById('playlistLink2');


        // --- FUNCIÓN DE INICIALIZACIÓN Y GUARDADO DE DATOS (localStorage) ---
        
        function loadProfile() {
            // Cargar imagen de perfil
            const savedImage = localStorage.getItem('profileImage');
            if (savedImage) { profileImageElement.src = savedImage; }

            // Cargar nombre
            const savedName = localStorage.getItem('profileName');
            if (savedName) { profileNameElement.textContent = savedName; }

            // Cargar biografía
            const savedBio = localStorage.getItem('profileBio');
            if (savedBio) { profileBioElement.textContent = `"${savedBio}"`; }
            
            // Cargar fondo
            const savedBackground = localStorage.getItem('profileBackground');
            if (savedBackground && backgroundImages[savedBackground]) {
                bodyElement.style.backgroundImage = `url('${backgroundImages[savedBackground]}')`;
                bodyElement.style.backgroundColor = 'transparent'; 
                document.getElementById('backgroundSelector').value = savedBackground;
            } else if (savedBackground === 'default') {
                bodyElement.style.backgroundImage = 'none';
                bodyElement.style.backgroundColor = '#1e1e2e';
            }
            
            // Cargar links de playlists
            const savedLink1 = localStorage.getItem('playlistLink1Url');
            const savedName1 = localStorage.getItem('playlistLink1Name');
            if (savedLink1) { playlistLink1Element.href = savedLink1; }
            if (savedName1) { playlistLink1Element.textContent = savedName1; }
            
            const savedLink2 = localStorage.getItem('playlistLink2Url');
            const savedName2 = localStorage.getItem('playlistLink2Name');
            if (savedLink2) { playlistLink2Element.href = savedLink2; }
            if (savedName2) { playlistLink2Element.textContent = savedName2; }
        }

        // --- FUNCIONES DE PERSONALIZACIÓN ---

        function updateProfileImage() {
            const newUrl = document.getElementById('newImageUrl').value.trim();
            if (newUrl) {
                localStorage.setItem('profileImage', newUrl);
                profileImageElement.src = newUrl;
                document.getElementById('newImageUrl').value = '';
            }
        }

        function updateBackground() {
            const selectedKey = document.getElementById('backgroundSelector').value;
            const newBackground = backgroundImages[selectedKey];

            if (selectedKey === 'default') {
                bodyElement.style.backgroundImage = 'none';
                bodyElement.style.backgroundColor = '#1e1e2e';
            } else if (newBackground) {
                bodyElement.style.backgroundImage = `url('${newBackground}')`;
                bodyElement.style.backgroundColor = 'transparent';
            }
            localStorage.setItem('profileBackground', selectedKey);
        }

        function updateProfileName() {
            const newName = document.getElementById('newProfileName').value.trim();
            if (newName) {
                profileNameElement.textContent = newName;
                localStorage.setItem('profileName', newName);
                document.getElementById('newProfileName').value = '';
            }
        }
        
        function updateProfileBio() {
            const newBio = document.getElementById('newProfileBio').value.trim();
            if (newBio) {
                profileBioElement.textContent = `"${newBio}"`;
                localStorage.setItem('profileBio', newBio);
                document.getElementById('newProfileBio').value = '';
            }
        }
        
        function updatePlaylistLink(index) {
            const linkElement = document.getElementById(`playlistLink${index}`);
            const newUrl = document.getElementById(`newPlaylistLink${index}`).value.trim();
            const newName = document.getElementById(`newPlaylistName${index}`).value.trim();

            if (newUrl) {
                linkElement.href = newUrl;
                localStorage.setItem(`playlistLink${index}Url`, newUrl);
            }
            
            if (newName) {
                linkElement.textContent = newName;
                localStorage.setItem(`playlistLink${index}Name`, newName);
            }
            
            document.getElementById(`newPlaylistLink${index}`).value = '';
            document.getElementById(`newPlaylistName${index}`).value = '';
        }

        // Cargar el perfil al cargar la página
        window.onload = loadProfile;
    </script>
</body>
</html>
