


# 🌌 Solar System Display — Interactive Animated Model

A visually stunning **animated solar system** built using only **HTML, CSS, and JavaScript**, featuring input-based planet information lookup and **text-to-speech narration**.
Perfect for educational demos, astronomy visualizations, or fun interactive web experiments.

---

## ✨ Features

### 🪐 Solar System Animation

* Realistic **circular orbits** with smooth CSS animations
* Centered glowing **Sun**
* Scaled planets with unique colors
* Accurate orbit speed differences

### 🔍 Planet Information Lookup

Type the name of any planet (or the Sun) and get:

* Title
* Detailed description
* Auto-displayed info box
* **AI narration** using text-to-speech

### 🔊 Built-in Speech Support

Uses the browser’s native **SpeechSynthesis API** to read descriptions aloud.

### 📱 Responsive + Clean UI

* Works on most screen sizes
* Dark space theme
* Soft glowing effects
* Focus on user clarity and immersion

---

## 📁 File Structure

```
/
├── index.html   # Main UI + Solar system markup
├── style.css    # Embedded inside <style>
└── script.js    # Embedded inside <script>
```

---

# 🧠 How the Code Works

## 1. 🌞 Solar System Layout (HTML)

The planets and the sun are positioned inside a `.solar-system` container:

```html
<div class="solar-system">
    <div class="sun"></div>

    <div class="orbit mercury-orbit">
        <div class="planet mercury"></div>
    </div>
    ...
</div>
```

Each orbit contains one planet, which rotates using CSS animations.

---

## 2. 🎨 Styling & Animation (CSS)

### Sun Glow

```css
.sun {
    width: 80px;
    height: 80px;
    background: radial-gradient(circle, #ffe066, #ff8c00);
    box-shadow: 0 0 30px #ff8c00, 0 0 60px #ffa500;
}
```

### Orbit Rotation Animation

All planets rotate using:

```css
@keyframes orbit-rotation {
    to {
        transform: rotate(360deg);
    }
}
```

Each orbit has a different duration, e.g.:

```css
.mercury-orbit { animation-duration: 4s; }
.neptune-orbit { animation-duration: 70s; }
```

This mimics real orbital speed differences.

---

## 3. 🌍 Planet Information Data (JavaScript)

A JavaScript object stores all planet facts:

```js
const planetData = {
    earth: {
        name: "Earth",
        info: "Earth is the third planet from the Sun..."
    },
    mars: { ... }
};
```

---

## 4. 🔎 Handling User Input

As the user types:

```js
input.addEventListener('input', function() {
    const query = input.value.toLowerCase().trim();

    if (planetData[query]) {
        // Show matching planet info
    } else if (query === '') {
        // Hide results
    } else {
        // No match found
    }
});
```

---

## 5. 🔊 Text-to-Speech Narration

When a planet is found, the browser speaks the description:

```js
function speakText(text) {
    const utterance = new SpeechSynthesisUtterance(text);
    window.speechSynthesis.speak(utterance);
}
```

If the input is erased, any ongoing speech stops:

```js
window.speechSynthesis.cancel();
```

---

## 6. 📦 Info Box Rendering

Planet details dynamically appear here:

```js
infoDiv.innerHTML = `<h2>${planet.name}</h2><p>${planet.info}</p>`;
infoDiv.style.display = 'block';
```

If the name doesn’t match:

```js
infoDiv.innerHTML = '<p>No information found...</p>';
```

---

# 🚀 How to Run

✔ Simply open **index.html** in any modern browser.
✔ No build tools required.
✔ Speech synthesis works automatically if supported.

---

# 🧭 Future Ideas (Optional Enhancements)

* Click-to-select planets
* Sound effects or background music
* Realistic planetary textures
* Zoom-in or focus mode
* Moons orbiting planets

---

# 📜 License

MIT — free to use, modify, and share.

