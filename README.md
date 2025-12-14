# Refresh Rate Test 🖥️🔃

[RefreshRate.app](https://refreshrate.app) is a browser-based tool to **measure how your display actually behaves in motion**, not just what the Windows panel says.

It focuses on three things:

- How stable your **frame pacing** really is.
- How many **distinct positions (“ghosts”)** you can see in different time windows.
- How different **FPS targets** (30, 60, 120, 240, etc.) would look on your current panel.

<br>
<div align="center">
  <img src="/refreshrate.png" alt="Desktop Screenshot">
</div>
<br>

---

## Features

- 🧵 **Motion Tracks (ms lanes)**  
  Time-based tracks at 50 ms, 100 ms, 150 ms, 500 ms and 1000 ms. Each one shows a ball crossing the lane; the app estimates how many **ghost positions** you should see at your measured refresh rate.

- 📊 **Live Metrics Panel**  
  - FPS (frames per second)  
  - Frame duration (ms)  
  - Refresh rate (Hz) from measured frame spacing  
  - Pixels per frame / pixels per second  
  - Aspect ratio  
  - Screen resolution  
  - System scale (%)  
  - Screen orientation  

- 👻 **Ghost Counter per lane**  
  Shows how many distinct “snapshots” of the moving ball your display should be able to show in that lane, based on your current measured Hz.

- 🧪 **Frame Rate Preview (canonical FPS lines)**  
  Animated rows for common FPS targets:
  `30, 60, 120, 165, 240, 360, 480, 600`.  
  Only FPS values **at or below your maximum measured refresh rate** this session are shown, plus a **custom line** for your exact panel Hz when it sits between presets.

- 📱 **Responsive and PWA-ready**  
  Works on desktop and mobile, supports installation as a **Progressive Web App** and can run offline once cached.

- 🎛️ **Simple controls**  
  Change:
  - Background lane color  
  - Number of decimals for the metrics  
  - Metrics update interval

---

## How to Use

1. **Open the app**  
   Go to:  
   [https://refreshrate.app](https://refreshrate.app)

2. **Put the window where it matters**  
   - Move the browser to the monitor you actually care about.
   - Use the **Fullscreen** button for more consistent timing and motion.

3. **Read the Motion Tracks (left panel)**  
   - Each lane has a label: `50 ms`, `100 ms`, `150 ms`, `500 ms`, `1000 ms`.  
   - The ball crosses the lane in exactly that time.  
   - Under each lane you see **“Expected ghosts”**: this is  
     `refreshRate(Hz) × laneDuration(seconds)` rounded.
   - On a good high-refresh panel, you should see **many clean, distinct positions** even on the short lanes (50 ms, 100 ms).  
   - If everything looks like a smeared streak or you barely see steps on the short lanes, your effective motion clarity is worse than the number on the box suggests.

4. **Watch the Live Metrics (right panel)**  
   - `FPS` and `Frame Duration` show how consistent the browser’s render loop is.  
   - `Refresh Rate (Hz)` is computed from actual frame spacing, not from OS settings.  
   - `Pixels per Frame` and `Pixels per Second` show how much work your panel is doing at that configuration.  
   - Aspect ratio, resolution, scale and orientation are pulled from `screen` and `devicePixelRatio`.

5. **Use the Frame Rate Preview (bottom-right)**  
   - Rows like `30 fps`, `60 fps`, `120 fps` etc. are shown **only if they are ≤ your max measured Hz** this session.
   - A **custom row** like `143 fps (your panel)` appears when your measured Hz sits between presets.
   - All rows cover the same distance, but the **update cadence** is tied to the FPS number, so you can visually compare:
     - How choppy 30 looks vs 60  
     - How 60 compares to 120 / 144 / 165  
     - Whether 240 on your panel actually looks meaningfully different from 165, etc.

---

## How the Ghosts Work (Short Version)

The Motion Tracks use a simple idea:

- Your measured refresh rate is `Hz`.
- A lane duration is `T` milliseconds.
- Expected number of distinct positions is:

```text
ghosts ≈ Hz × (T / 1000)
