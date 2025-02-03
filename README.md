<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Green Space - 3D Version</title>
    <style>
        body { margin: 0; overflow: hidden; }
        canvas { display: block; }
    </style>
</head>
<body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // Set up basic scene, camera, and renderer
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        // Add a basic floor
        const geometry = new THREE.PlaneGeometry(500, 500);
        const material = new THREE.MeshBasicMaterial({ color: 0x555555, side: THREE.DoubleSide });
        const plane = new THREE.Mesh(geometry, material);
        plane.rotation.x = - Math.PI / 2;
        scene.add(plane);

        // Create a simple astronaut model (cube for simplicity)
        const astronautGeometry = new THREE.BoxGeometry(1, 2, 1);
        const astronautMaterial = new THREE.MeshBasicMaterial({ color: 0x0000ff });
        const astronaut = new THREE.Mesh(astronautGeometry, astronautMaterial);
        astronaut.position.y = 1; // Keep it above the ground
        scene.add(astronaut);

        // Create simple aliens (cylinder for simplicity)
        const alienGeometry = new THREE.CylinderGeometry(0.5, 0.5, 2, 8);
        const alienMaterial = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
        const alien = new THREE.Mesh(alienGeometry, alienMaterial);
        alien.position.set(5, 1, -5); // Position it in the scene
        scene.add(alien);

        // Set camera position
        camera.position.z = 5;

        // Handle player movement (WASD keys)
        let moveForward = false, moveBackward = false, moveLeft = false, moveRight = false;

        document.addEventListener('keydown', (event) => {
            if (event.key === 'w') moveForward = true;
            if (event.key === 's') moveBackward = true;
            if (event.key === 'a') moveLeft = true;
            if (event.key === 'd') moveRight = true;
        });

        document.addEventListener('keyup', (event) => {
            if (event.key === 'w') moveForward = false;
            if (event.key === 's') moveBackward = false;
            if (event.key === 'a') moveLeft = false;
            if (event.key === 'd') moveRight = false;
        });

        // Update the game scene
        function animate() {
            requestAnimationFrame(animate);

            // Update astronaut position based on user input
            if (moveForward) astronaut.position.z -= 0.1;
            if (moveBackward) astronaut.position.z += 0.1;
            if (moveLeft) astronaut.position.x -= 0.1;
            if (moveRight) astronaut.position.x += 0.1;

            renderer.render(scene, camera);
        }

        animate();
    </script>
</body>
</html>







