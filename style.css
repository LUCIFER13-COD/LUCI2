const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

canvas.width = 800;
canvas.height = 600;

let spaceship = {
    x: canvas.width / 2 - 25,
    y: canvas.height - 70,
    width: 50,
    height: 50,
    color: 'cyan',
    speed: 15
};

let asteroids = [];
let score = 0;
let gameRunning = true;

function createAsteroid() {
    return {
        x: Math.random() * (canvas.width - 40),
        y: -50,
        width: 40,
        height: 40,
        color: 'gray',
        speed: 5 + Math.random() * 5
    };
}

function spawnAsteroids() {
    if (Math.random() < 0.02) {
        asteroids.push(createAsteroid());
    }
}

document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowLeft' && spaceship.x > 0) {
        spaceship.x -= spaceship.speed;
    } else if (e.key === 'ArrowRight' && spaceship.x < canvas.width - spaceship.width) {
        spaceship.x += spaceship.speed;
    }
});

function detectCollision(obj1, obj2) {
    return (
        obj1.x < obj2.x + obj2.width &&
        obj1.x + obj1.width > obj2.x &&
        obj1.y < obj2.y + obj2.height &&
        obj1.y + obj1.height > obj2.y
    );
}

function updateAsteroids() {
    asteroids.forEach((asteroid, index) => {
        asteroid.y += asteroid.speed;
        if (asteroid.y > canvas.height) {
            asteroids.splice(index, 1);
            score++;
            document.getElementById('score').innerText = `Score: ${score}`;
        }

        if (detectCollision(spaceship, asteroid)) {
            gameRunning = false;
            alert('Game Over!');
        }
    });
}

function drawSpaceship() {
    ctx.fillStyle = spaceship.color;
    ctx.fillRect(spaceship.x, spaceship.y, spaceship.width, spaceship.height);
}

function drawAsteroids() {
    asteroids.forEach((asteroid) => {
        ctx.fillStyle = asteroid.color;
        ctx.fillRect(asteroid.x, asteroid.y, asteroid.width, asteroid.height);
    });
}

function gameLoop() {
    if (!gameRunning) return;

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    drawSpaceship();
    drawAsteroids();

    spawnAsteroids();
    updateAsteroids();

    requestAnimationFrame(gameLoop);
}

gameLoop();
