document.addEventListener("DOMContentLoaded", () => {

    // --- 1. Initial Overlay Handling ---
    const overlay = document.getElementById('initial-overlay');

    // Start Fireworks & Audio immediately
    startFireworks();

    // Wait 5 seconds, then fade out the overlay
    setTimeout(() => {
        overlay.classList.add('overlay-hidden');
        // Optional: Enable scrolling on body after overlay is gone if you disabled it initially
        // document.body.style.overflow = 'auto'; 
    }, 5000);


    // --- 2. Countdown Timer Logic ---
    // Set the date we're counting down to (January 5, 2026, assuming 9:30 AM start)
    const countDownDate = new Date("Jan 5, 2026 09:30:00").getTime();

    // Update the count down every 1 second
    const countdownInterval = setInterval(function () {

        // Get today's date and time
        const now = new Date().getTime();

        // Find the distance between now and the count down date
        const distance = countDownDate - now;

        // Time calculations for days, hours, minutes and seconds
        const days = Math.floor(distance / (1000 * 60 * 60 * 24));
        const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((distance % (1000 * 60)) / 1000);

        // Output the result to the specific elements, adding leading zeros if needed
        document.getElementById("days").innerText = days < 10 ? "0" + days : days;
        document.getElementById("hours").innerText = hours < 10 ? "0" + hours : hours;
        document.getElementById("minutes").innerText = minutes < 10 ? "0" + minutes : minutes;
        document.getElementById("seconds").innerText = seconds < 10 ? "0" + seconds : seconds;

        // If the count down is over, write some text 
        if (distance < 0) {
            clearInterval(countdownInterval);
            document.getElementById("countdown-timer").innerHTML = "<h3 class='accent-text'>Event has started!</h3>";
        }
    }, 1000);


    // --- 3. Scroll Animation Observer ---
    // This makes elements fade in and slide up as they scroll into view

    const animatedElements = document.querySelectorAll('.scroll-animate');

    const observerOptions = {
        root: null, // use browser viewport
        rootMargin: '0px',
        threshold: 0.2 // trigger when 20% of the element is visible
    };

    const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('visible');
                // Stop observing once it has animated in
                observer.unobserve(entry.target);
            }
        });
    }, observerOptions);

    animatedElements.forEach(element => {
        observer.observe(element);
    });

    // --- 4. Confetti Animation ---
    startConfetti();

    // --- 5. Typing Effect ---
    typeWriter("Chief Guest Sessions", document.querySelector('.hero-subtitle'), 100);

    // --- 6. Parallax Effect ---
    initParallax();
});

function startConfetti() {
    const canvas = document.createElement('canvas');
    const ctx = canvas.getContext('2d');
    canvas.style.position = 'fixed';
    canvas.style.top = '0';
    canvas.style.left = '0';
    canvas.style.width = '100%';
    canvas.style.height = '100%';
    canvas.style.pointerEvents = 'none';
    canvas.style.zIndex = '99998'; // Below fireworks
    document.body.appendChild(canvas);

    let width = window.innerWidth;
    let height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;

    const particles = [];
    const colors = ['#ff4d29', '#ffffff', '#ff8c00', '#ffbd2e', '#ff5f56'];

    function Particle() {
        this.x = Math.random() * width;
        this.y = Math.random() * height - height;
        this.size = Math.random() * 8 + 4;
        this.speedY = Math.random() * 3 + 2;
        this.speedX = Math.random() * 2 - 1;
        this.color = colors[Math.floor(Math.random() * colors.length)];
        this.rotation = Math.random() * 360;
        this.rotationSpeed = Math.random() * 10 - 5;
    }

    Particle.prototype.update = function () {
        this.y += this.speedY;
        this.x += this.speedX;
        this.rotation += this.rotationSpeed;

        if (this.y > height) {
            this.y = -10;
            this.x = Math.random() * width;
        }
    };

    Particle.prototype.draw = function () {
        ctx.save();
        ctx.translate(this.x, this.y);
        ctx.rotate(this.rotation * Math.PI / 180);
        ctx.fillStyle = this.color;
        ctx.fillRect(-this.size / 2, -this.size / 2, this.size, this.size);
        ctx.restore();
    };

    for (let i = 0; i < 150; i++) {
        particles.push(new Particle());
    }

    let animationId;
    function animate() {
        ctx.clearRect(0, 0, width, height);
        particles.forEach(p => {
            p.update();
            p.draw();
        });
        animationId = requestAnimationFrame(animate);
    }

    animate();

    // Stop confetti after 5 seconds
    setTimeout(() => {
        canvas.style.transition = 'opacity 2s ease';
        canvas.style.opacity = '0';
        setTimeout(() => {
            cancelAnimationFrame(animationId);
            canvas.remove();
        }, 2000);
    }, 5000);

    window.addEventListener('resize', () => {
        width = window.innerWidth;
        height = window.innerHeight;
        canvas.width = width;
        canvas.height = height;
    });
}

function typeWriter(text, element, speed) {
    if (!element) return;
    element.innerHTML = "";
    let i = 0;
    function type() {
        if (i < text.length) {
            element.innerHTML += text.charAt(i);
            i++;
            setTimeout(type, speed);
        }
    }
    type();
}

function initParallax() {
    const hero = document.getElementById('hero');
    const logo = document.querySelector('.hero-logo');

    if (!hero || !logo) return;

    hero.addEventListener('mousemove', (e) => {
        const x = (window.innerWidth - e.pageX * 2) / 90;
        const y = (window.innerHeight - e.pageY * 2) / 90;

        logo.style.transform = `translateX(${x}px) translateY(${y}px)`;
    });
}

function startFireworks() {
    const overlay = document.getElementById('initial-overlay');
    if (!overlay) return;

    const canvas = document.createElement('canvas');
    const ctx = canvas.getContext('2d');
    canvas.style.position = 'absolute';
    canvas.style.top = '0';
    canvas.style.left = '0';
    canvas.style.width = '100%';
    canvas.style.height = '100%';
    canvas.style.pointerEvents = 'none';
    canvas.style.zIndex = '1'; // Behind text
    overlay.appendChild(canvas);

    let width = window.innerWidth;
    let height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;

    // Play Audio with Autoplay Handling
    const audio = new Audio('fireworks.mp3');
    audio.volume = 0.5;

    const playAudio = () => {
        audio.play().catch(e => {
            console.log("Audio autoplay blocked, waiting for interaction:", e);
            // If blocked, play on first interaction
            const playOnInteraction = () => {
                audio.play();
                document.removeEventListener('click', playOnInteraction);
                document.removeEventListener('touchstart', playOnInteraction);
            };
            document.addEventListener('click', playOnInteraction);
            document.addEventListener('touchstart', playOnInteraction);
        });
    };

    playAudio();


    class Firework {
        constructor() {
            this.x = Math.random() * width;
            this.y = height;
            this.targetY = Math.random() * (height * 0.5);
            this.speed = Math.random() * 3 + 5;
            this.angle = -Math.PI / 2 + (Math.random() * 0.2 - 0.1);
            this.vx = Math.cos(this.angle) * this.speed;
            this.vy = Math.sin(this.angle) * this.speed;
            this.color = `hsl(${Math.random() * 360}, 100%, 50%)`;
            this.exploded = false;
            this.particles = [];
        }

        update() {
            if (!this.exploded) {
                this.x += this.vx;
                this.y += this.vy;
                this.vy += 0.05; // Gravity

                if (this.vy >= 0 || this.y <= this.targetY) {
                    this.explode();
                }
            } else {
                for (let i = this.particles.length - 1; i >= 0; i--) {
                    this.particles[i].update();
                    if (this.particles[i].alpha <= 0) {
                        this.particles.splice(i, 1);
                    }
                }
            }
        }

        explode() {
            this.exploded = true;
            for (let i = 0; i < 50; i++) {
                this.particles.push(new Particle(this.x, this.y, this.color));
            }
        }

        draw() {
            if (!this.exploded) {
                ctx.beginPath();
                ctx.arc(this.x, this.y, 3, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
            } else {
                this.particles.forEach(p => p.draw());
            }
        }
    }

    class Particle {
        constructor(x, y, color) {
            this.x = x;
            this.y = y;
            this.color = color;
            const angle = Math.random() * Math.PI * 2;
            const speed = Math.random() * 4 + 1;
            this.vx = Math.cos(angle) * speed;
            this.vy = Math.sin(angle) * speed;
            this.alpha = 1;
            this.decay = Math.random() * 0.02 + 0.01;
        }

        update() {
            this.x += this.vx;
            this.y += this.vy;
            this.vy += 0.05; // Gravity
            this.alpha -= this.decay;
        }

        draw() {
            ctx.save();
            ctx.globalAlpha = this.alpha;
            ctx.beginPath();
            ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
            ctx.fillStyle = this.color;
            ctx.fill();
            ctx.restore();
        }
    }

    let fireworks = [];
    let animationId;

    function animate() {
        ctx.fillStyle = 'rgba(0, 0, 0, 0.1)'; // Trail effect
        ctx.fillRect(0, 0, width, height);

        if (Math.random() < 0.05) { // Spawn rate
            fireworks.push(new Firework());
        }

        for (let i = fireworks.length - 1; i >= 0; i--) {
            fireworks[i].update();
            fireworks[i].draw();
            if (fireworks[i].exploded && fireworks[i].particles.length === 0) {
                fireworks.splice(i, 1);
            }
        }

        animationId = requestAnimationFrame(animate);
    }

    animate();

    // Stop fireworks after 5.5 seconds (matches overlay fade out)
    setTimeout(() => {
        canvas.style.transition = 'opacity 1s ease';
        canvas.style.opacity = '0';
        setTimeout(() => {
            cancelAnimationFrame(animationId);
            canvas.remove();
        }, 1000);
    }, 5500);

    window.addEventListener('resize', () => {
        width = window.innerWidth;
        height = window.innerHeight;
        canvas.width = width;
        canvas.height = height;
    });
}
