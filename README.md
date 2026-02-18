<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Museum Experience</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: #2c2c2c;
            font-family: Arial, sans-serif;
            overflow: hidden;
        }

        #gameContainer {
            position: relative;
            width: 100vw;
            height: 100vh;
            background: linear-gradient(45deg, #1a1a1a, #2a2a2a);
        }

        #museum {
            position: relative;
            width: 100%;
            height: 100%;
            overflow: hidden;
            cursor: none;
        }

        .room {
            position: absolute;
            background: #f0f0f0;
            border: 3px solid #8B4513;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.3);
        }

        .wall {
            position: absolute;
            background: #e8e8e8;
            border: 2px solid #999;
        }

        .artwork {
            position: absolute;
            background: #fff;
            border: 3px solid #8B4513;
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            color: #333;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .artwork:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 12px rgba(0,0,0,0.4);
        }

        .player {
            position: absolute;
            width: 20px;
            height: 20px;
            background: #4169E1;
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            border: 2px solid #1e3a8a;
            transition: all 0.1s ease;
            z-index: 100;
        }

        .player::before {
            content: '';
            position: absolute;
            top: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 12px;
            height: 8px;
            background: #8B4513;
            border-radius: 50%;
        }

        .controls {
            position: absolute;
            bottom: 20px;
            left: 20px;
            background: rgba(0,0,0,0.8);
            color: white;
            padding: 15px;
            border-radius: 10px;
            font-size: 14px;
        }

        .info-panel {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0,0,0,0.9);
            color: white;
            padding: 20px;
            border-radius: 10px;
            max-width: 300px;
            display: none;
        }

        .minimap {
            position: absolute;
            top: 20px;
            left: 20px;
            width: 150px;
            height: 100px;
            background: rgba(0,0,0,0.8);
            border: 2px solid #666;
            border-radius: 5px;
        }

        .minimap-room {
            position: absolute;
            background: #666;
            border: 1px solid #999;
        }

        .minimap-player {
            position: absolute;
            width: 3px;
            height: 3px;
            background: #4169E1;
            border-radius: 50%;
        }

        @keyframes walking {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-2px); }
        }

        .walking {
            animation: walking 0.3s ease-in-out infinite;
        }
    </style>
</head>
<body>
    <div id="gameContainer">
        <div id="museum">
            <div class="room" id="mainRoom"></div>
            <div class="player" id="player"></div>
        </div>
        
        <div class="minimap" id="minimap">
            <div class="minimap-room"></div>
            <div class="minimap-player" id="minimapPlayer"></div>
        </div>
        
        <div class="controls">
            <strong>Controls:</strong><br>
            • Arrow Keys or WASD to move<br>
            • Click on artworks to view details<br>
            • Mouse to look around
        </div>
        
        <div class="info-panel" id="infoPanel">
            <h3 id="artworkTitle">Artwork Title</h3>
            <p id="artworkDescription">Description will appear here...</p>
            <button onclick="closeInfo()">Close</button>
        </div>
    </div>

    <script>
        class Museum {
            constructor() {
                this.player = {
                    x: 400,
                    y: 300,
                    speed: 3,
                    element: document.getElementById('player')
                };
                
                this.museum = document.getElementById('museum');
                this.minimap = document.getElementById('minimap');
                this.minimapPlayer = document.getElementById('minimapPlayer');
                
                this.keys = {};
                this.isMoving = false;
                
                this.artworks = [
                    {
                        title: "The Starry Night",
                        description: "A masterpiece by Vincent van Gogh depicting a swirling night sky over a village.",
                        x: 150, y: 100, width: 80, height: 60
                    },
                    {
                        title: "Mona Lisa",
                        description: "Leonardo da Vinci's enigmatic portrait of a woman with a mysterious smile.",
                        x: 300, y: 100, width: 60, height: 80
                    },
                    {
                        title: "The Persistence of Memory",
                        description: "Salvador Dalí's surreal painting featuring melting clocks in a dreamscape.",
                        x: 500, y: 150, width: 70, height: 50
                    },
                    {
                        title: "Girl with a Pearl Earring",
                        description: "Johannes Vermeer's captivating portrait of a girl with an exotic pearl earring.",
                        x: 650, y: 100, width: 60, height: 75
                    },
                    {
                        title: "The Scream",
                        description: "Edvard Munch's expressionist masterpiece capturing anxiety and existential angst.",
                        x: 200, y: 400, width: 55, height: 70
                    },
                    {
                        title: "American Gothic",
                        description: "Grant Wood's iconic depiction of a farmer and his daughter in rural America.",
                        x: 450, y: 420, width: 65, height: 80
                    }
                ];
                
                this.init();
            }
            
            init() {
                this.createRoom();
                this.createArtworks();
                this.setupEventListeners();
                this.updateMinimap();
                this.gameLoop();
            }
            
            createRoom() {
                const room = document.getElementById('mainRoom');
                room.style.width = '800px';
                room.style.height = '600px';
                room.style.left = '50%';
                room.style.top = '50%';
                room.style.transform = 'translate(-50%, -50%)';
                
                // Create walls for visual depth
                const walls = [
                    { x: 0, y: 0, width: 800, height: 10 }, // top
                    { x: 0, y: 590, width: 800, height: 10 }, // bottom
                    { x: 0, y: 0, width: 10, height: 600 }, // left
                    { x: 790, y: 0, width: 10, height: 600 } // right
                ];
                
                walls.forEach(wall => {
                    const wallElement = document.createElement('div');
                    wallElement.className = 'wall';
                    wallElement.style.left = wall.x + 'px';
                    wallElement.style.top = wall.y + 'px';
                    wallElement.style.width = wall.width + 'px';
                    wallElement.style.height = wall.height + 'px';
                    room.appendChild(wallElement);
                });
            }
            
            createArtworks() {
                const room = document.getElementById('mainRoom');
                
                this.artworks.forEach((artwork, index) => {
                    const artElement = document.createElement('div');
                    artElement.className = 'artwork';
                    artElement.style.left = artwork.x + 'px';
                    artElement.style.top = artwork.y + 'px';
                    artElement.style.width = artwork.width + 'px';
                    artElement.style.height = artwork.height + 'px';
                    artElement.innerHTML = `🖼️<br><small>${artwork.title}</small>`;
                    artElement.onclick = () => this.showArtworkInfo(artwork);
                    room.appendChild(artElement);
                });
            }
            
            setupEventListeners() {
                // Keyboard controls
                document.addEventListener('keydown', (e) => {
                    this.keys[e.key.toLowerCase()] = true;
                });
                
                document.addEventListener('keyup', (e) => {
                    this.keys[e.key.toLowerCase()] = false;
                });
                
                // Mouse movement for camera feel
                document.addEventListener('mousemove', (e) => {
                    const centerX = window.innerWidth / 2;
                    const centerY = window.innerHeight / 2;
                    const offsetX = (e.clientX - centerX) * 0.02;
                    const offsetY = (e.clientY - centerY) * 0.02;
                    
                    this.museum.style.transform = `translate(${offsetX}px, ${offsetY}px)`;
                });
            }
            
            updatePlayer() {
                let deltaX = 0;
                let deltaY = 0;
                
                // Check for movement keys
                if (this.keys['arrowup'] || this.keys['w']) deltaY = -this.player.speed;
                if (this.keys['arrowdown'] || this.keys['s']) deltaY = this.player.speed;
                if (this.keys['arrowleft'] || this.keys['a']) deltaX = -this.player.speed;
                if (this.keys['arrowright'] || this.keys['d']) deltaX = this.player.speed;
                
                // Diagonal movement adjustment
                if (deltaX !== 0 && deltaY !== 0) {
                    deltaX *= 0.707; // cos(45°)
                    deltaY *= 0.707;
                }
                
                // Check if moving
                const wasMoving = this.isMoving;
                this.isMoving = deltaX !== 0 || deltaY !== 0;
                
                if (this.isMoving) {
                    // Boundary checking (accounting for room position)
                    const roomRect = document.getElementById('mainRoom').getBoundingClientRect();
                    const museumRect = this.museum.getBoundingClientRect();
                    
                    const roomLeft = roomRect.left - museumRect.left + 20;
                    const roomTop = roomRect.top - museumRect.top + 20;
                    const roomRight = roomLeft + roomRect.width - 40;
                    const roomBottom = roomTop + roomRect.height - 40;
                    
                    const newX = this.player.x + deltaX;
                    const newY = this.player.y + deltaY;
                    
                    if (newX >= roomLeft && newX <= roomRight) {
                        this.player.x = newX;
                    }
                    if (newY >= roomTop && newY <= roomBottom) {
                        this.player.y = newY;
                    }
                    
                    // Add walking animation
                    if (!wasMoving) {
                        this.player.element.classList.add('walking');
                    }
                } else if (wasMoving) {
                    this.player.element.classList.remove('walking');
                }
                
                // Update player position
                this.player.element.style.left = this.player.x + 'px';
                this.player.element.style.top = this.player.y + 'px';
                
                this.updateMinimap();
            }
            
            updateMinimap() {
                const minimapScale = 0.15;
                const minimapX = this.player.x * minimapScale;
                const minimapY = this.player.y * minimapScale;
                
                this.minimapPlayer.style.left = minimapX + 'px';
                this.minimapPlayer.style.top = minimapY + 'px';
            }
            
            showArtworkInfo(artwork) {
                const infoPanel = document.getElementById('infoPanel');
                const title = document.getElementById('artworkTitle');
                const description = document.getElementById('artworkDescription');
                
                title.textContent = artwork.title;
                description.textContent = artwork.description;
                infoPanel.style.display = 'block';
            }
            
            gameLoop() {
                this.updatePlayer();
                requestAnimationFrame(() => this.gameLoop());
            }
        }
        
        function closeInfo() {
            document.getElementById('infoPanel').style.display = 'none';
        }
        
        // Initialize the museum when the page loads
        window.addEventListener('load', () => {
            new Museum();
        });
    </script>
</body>
</html>
