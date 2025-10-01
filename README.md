That's a clever script for Logic Pro's Scripter plugin! I've created a simple, clear **README.md** file in markdown format for you.

# Note Randomizer & Range Limiter 🎼

This is a MIDI script for the **Logic Pro X Scripter** plugin. It takes any incoming MIDI note and replaces it with a **random note** within a set range, while also **randomizing its velocity**.

---

## ⚙️ How It Works

This script acts as a creative MIDI effect. Instead of playing the note you press on your keyboard, it does two things:

1.  **Random Note Selection:** It ignores the pitch of the incoming note and selects a completely random new note **pitch** that falls between the **Low Note** and **High Note** settings. It ensures the same note is not played twice in a row.
2.  **Random Velocity:** It gives the new note a **random velocity** (loudness) that falls between the **Min Velocity** and **Max Velocity** settings.

All other MIDI messages (like pedals or control changes) are passed through unchanged.

---

## 🎹 Controls (Parameters)

You can adjust the behavior of the script using these four controls in the Scripter plugin window:

| Control Name | Type | Description | Default Setting |
| :--- | :--- | :--- | :--- |
| **Low Note** | Menu/Slider | Sets the **lowest** possible MIDI note pitch. | C2 |
| **High Note** | Menu/Slider | Sets the **highest** possible MIDI note pitch. | C4 |
| **Min Velocity** | Slider | Sets the **softest** possible note velocity (loudness). | 40 |
| **Max Velocity** | Slider | Sets the **loudest** possible note velocity (loudness). | 100 |

---

## 🛠️ Installation & Usage

1.  **Open Scripter:** In your Logic Pro project, insert the **Scripter** MIDI FX plugin onto a track.
2.  **Load the Script:**
    * Click on the **"Open Script..."** button.
    * Copy the entire script code (JavaScript) into the Scripter editor window.
    * Click **"Run"** to activate it.
3.  **Adjust Settings:** Use the controls in the Scripter plugin to set your desired pitch and velocity ranges.
4.  **Play:** Start playing notes on your MIDI controller. Each note you press will trigger a **random pitch and velocity** within your set range.

---

## 📝 Notes on the Code

* The `generateNoteNames()` function is used to create user-friendly MIDI note names (like C-2, C4, G8) for the **Low Note** and **High Note** menus.
* The `ParameterChanged()` function ensures that the **Low Note** is never higher than the **High Note**, and **Min Velocity** is never higher than **Max Velocity**.
* The `do...while` loop inside `HandleMIDI` makes sure that the new random note pitch is **different** from the one just played (`lastNote`), which prevents repeating the same note back-to-back.
