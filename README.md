

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>For My Baby Danayah 💖</title>
  <style>
    html, body {
      margin: 0;
      height: 100%;
      overflow: hidden;
      background-color: #000;
      font-family: 'Segoe UI', sans-serif;
    }
    canvas {
      display: block;
    }
    .audio-player {
      position: fixed;
      top: 10px;
      left: 10px;
      z-index: 1000;
    }
    #error-msg {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: pink;
      font-size: 1.5rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <audio class="audio-player" autoplay loop>
    <source src="https://youtu.be/Q49pnA4jsp8?si=L-3U9zCCJt28IoVB “audio/mpeg" />
    Your browser does not support the audio element.
  </audio>

  <div id="error-msg"></div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/loaders/FontLoader.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/geometries/TextGeometry.js"></script>

  <script>
    const messages = [
      "I love you so much baby.",
      "You're my one and only baby girl forever.",
      "My pretty girl.",
      "Prettiest girl in the world.",
      "K + D",
      "I adore you baby.",
      "You feel like home.",
      "You're the best thing that's ever happen to me.",
      "I love all the sides you show me.",
      "I'll play roblox with you whenever you want.",
      "I will always be there to support you.",
      "My sweet baby.",
      "I fall in love with you everyday.",
      "I love you even more every second.",
      "I still remember the first time we said I love you to each other.",
      "You're the best girlfriend I could ever ask for.",
      "Little me prayed to have someone like you.",
      "I want to spend the rest of my sunsets with you.",
      "I want to be your first time in everything.",
      "I never knew love had a sound until I heard your voice.",
      "I will love you through your flaws and imperfections.",
      "I love you just as you are.",
      "I love hearing about your day.",
      "I cherish all of your pictures.",
      "You're prettier than this website.",
      "I love talking to you.",
      "I love listening to your stories.",
      "I love being in love with you.",
      "I'll never get tired of you baby.",
      "You're the most special girl to me.",
      "You’re my safe place, Danayah.",
      "Thank you for loving me, baby.",
      "Even in silence, you’re comforting.",
      "You’re the reason I smile randomly.",
      "Every day with you is a dream come true."
    ];

    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 2000);
    camera.position.z = 400;

    const renderer = new THREE.WebGLRenderer({ antialias: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    const controls = new THREE.OrbitControls(camera, renderer.domElement);
    controls.enableDamping = true;
    controls.dampingFactor = 0.1;
    controls.rotateSpeed = 0.5;

    const loader = new THREE.FontLoader();
    loader.load('https://threejs.org/examples/fonts/helvetiker_regular.typeface.json', function (font) {
      const material = new THREE.MeshBasicMaterial({ color: 0xff69b4 });

      messages.forEach(msg => {
        const geometry = new THREE.TextGeometry(msg, {
          font: font,
          size: 10,
          height: 1,
          curveSegments: 4,
        });

        const mesh = new THREE.Mesh(geometry, material);
        mesh.position.x = (Math.random() - 0.5) * 2000;
        mesh.position.y = (Math.random() - 0.5) * 2000;
        mesh.position.z = (Math.random() - 0.5) * 2000;
        scene.add(mesh);
      });

    }, undefined, function (err) {
      document.getElementById('error-msg').innerText = "Something went wrong loading the font.";
    });

    function animate() {
      requestAnimationFrame(animate);
      controls.update();
      renderer.render(scene, camera);
    }

    animate();

    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });
  </script>
</body>
</html>
