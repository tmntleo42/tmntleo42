// Initialize the scene, camera, and renderer
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// Basic floor and walls to simulate a 3D room environment
const floorGeometry = new THREE.PlaneGeometry(100, 100);
const floorMaterial = new THREE.MeshBasicMaterial({ color: 0x555555, side: THREE.DoubleSide });
const floor = new THREE.Mesh(floorGeometry, floorMaterial);
floor.rotation.x = -Math.PI / 2;
scene.add(floor);

// Add walls (simple cube for now)
const wallGeometry = new THREE.BoxGeometry(1, 10, 100);
const wallMaterial = new THREE.MeshBasicMaterial({ color: 0x999999 });
const wall1 = new THREE.Mesh(wallGeometry, wallMaterial);
wall1.position.set(50, 5, 0);
scene.add(wall1);

const wall2 = new THREE.Mesh(wallGeometry, wallMaterial);
wall2.position.set(-50, 5, 0);
scene.add(wall2);

// Create the astronaut (player) model (simple cube for simplicity)
const astronautGeometry = new THREE.BoxGeometry(1, 2, 1);
const astronautMaterial = new THREE.MeshBasicMaterial({ color: 0x0000ff });
const astronaut = new THREE.Mesh(astronautGeometry, astronautMaterial);
astronaut.position.y = 1; // Keep it above the floor
scene.add(astronaut);

// Create simple Xenomorph (alien) enemies (simple cylinder for now)
const alienGeometry = new THREE.CylinderGeometry(0.5, 0.5, 2, 8);
const alienMaterial = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const alien = new THREE.Mesh(alienGeometry, alienMaterial);
alien.position.set(10, 1, -10); // Position it in the scene
scene.add(alien);

// Set the camera position (first-person view)
camera.position.set(0, 1.5, 0); // Eye level of the astronaut

// Control variables for movement
let forward = false, backward = false, left = false, right = false;
let moveSpeed = 0.1, rotationSpeed = 0.02;

// Control movement via keyboard
document.addEventListener('keydown', (event) => {
    if (event.key === 'w') forward = true;
    if (event.key === 's') backward = true;
    if (event.key === 'a') left = true;
    if (event.key === 'd') right = true;
});

document.addEventListener('keyup', (event) => {
    if (event.key === 'w') forward = false;
    if (event.key === 's') backward = false;
    if (event.key === 'a') left = false;
    if (event.key === 'd') right = false;
});

// Mouse look functionality (for aiming)
let mouseX = 0, mouseY = 0;
document.addEventListener('mousemove', (event) => {
    mouseX = (event.clientX / window.innerWidth) * 2 - 1;
    mouseY = -(event.clientY / window.innerHeight) * 2 + 1;
});

// Shooting logic (simplified, no bullet physics)
let shooting = false;
document.addEventListener('click', () => {
    shooting = true;
});

// Game loop and update
function animate() {
    requestAnimationFrame(animate);

    // Update the camera and astronaut's movement
    if (forward) astronaut.position.z -= moveSpeed;
    if (backward) astronaut.position.z += moveSpeed;
    if (left) astronaut.position.x -= moveSpeed;
    if (right) astronaut.position.x += moveSpeed;

    // Move camera based on mouse movement (simple mouse look)
    camera.rotation.y += mouseX * rotationSpeed;
    camera.rotation.x += mouseY * rotationSpeed;

    // Handle shooting (simplified logic, no bullet impact yet)
    if (shooting) {
        console.log("Shooting!");
        shooting = false;
    }

    // Render the scene
    renderer.render(scene, camera);
}

animate();
