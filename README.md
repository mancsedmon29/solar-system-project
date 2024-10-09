# The Solar System

## General Styles:

1. **Background and Colors**:
   ```css
   body {
       background: #000f;
       color: #fffa;
       margin: 0;
       width: 100vw;
   }
   ```
   - `background: #000f;`: Sets a semi-transparent black background (the `f` means 15% opacity), giving a space-like effect.
   - `color: #fffa;`: Text color is set to off-white with some transparency.
   - `margin: 0;`: Removes default margins from the `body`.
   - `width: 100vw;`: The body's width is set to 100% of the viewport width.

2. **Centering Headings and Paragraphs**:
   ```css
   h1, p {
       text-align: center;
       color: #fff;
       margin: 0;
   }
   ```
   - This centers the text of headings (`h1`) and paragraphs (`p`), setting the color to white and removing margins.

3. **Heading Styles**:
   ```css
   h1 {
       font-size: 3rem;
       text-transform: uppercase;
   }
   ```
   - `font-size: 3rem;`: Makes the heading large.
   - `text-transform: uppercase;`: Forces the text in the heading to uppercase.

---

### List and Item (Planet) Styles:

4. **Ordered List Styles**:
   ```css
   ol {
       all: unset;
       aspect-ratio: 1 / 1;
       container-type: inline-size;
       display: grid;
       width: 100%;
   }
   ```
   - `all: unset;`: Resets all default styles for the ordered list (`ol`), removing bullets, padding, etc.
   - `aspect-ratio: 1 / 1;`: Ensures the list container maintains a 1:1 aspect ratio (a square).
   - `container-type: inline-size;`: Defines that the list's container should grow based on the content's size.
   - `display: grid;`: Sets the display to a grid, allowing precise control of element positioning.
   - `width: 100%;`: Makes the list take up the full width of its parent container.

5. **List Item (Planet) Styles**:
   ```css
   li {
       aspect-ratio: 1 / 1;
       border: 1px dashed;
       border-radius: 50%;
       display: grid;
       grid-area: 1 / 1;
       place-self: center;
       width: var(--d, 2cqi);
   }
   ```
   - Each planet (`li`) is a circle due to `border-radius: 50%`.
   - `aspect-ratio: 1 / 1;`: Ensures each planet remains circular.
   - `border: 1px dashed;`: Adds a dashed border around each planet.
   - `display: grid;`: Ensures content inside the planet is centered.
   - `grid-area: 1 / 1;`: Positions the item within the grid area.
   - `place-self: center;`: Centers each planet inside its container.
   - `width: var(--d, 2cqi);`: Sets the planet's width, with a default value of 2 "cqi" (CSS Custom Queries, a modern unit).

---

### Orbiting Animation:

6. **After Element for Orbiting**:
   ```css
   &::after {
       animation: rotate var(--t, 3s) linear infinite;
       aspect-ratio: 1 / 1;
       background: var(--b, hsl(0, 0%, 50%));
       border-radius: 50%;
       box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
       content: '';
       display: block;
       offset-path: content-box;
       width: var(--w, 2cqi);
   }
   ```
   - `&::after`: This pseudo-element represents a smaller circle inside each planet, simulating its orbit around the Sun.
   - `animation: rotate var(--t, 3s) linear infinite;`: This rotates the pseudo-element around the planet. The duration (`var(--t)`) is specific for each planet, defining how fast it orbits.
   - `background: var(--b, hsl(0, 0%, 50%));`: The planet's color is set through the `--b` variable, with a fallback gray shade.
   - `offset-path: content-box;`: The orbiting path is based on the content of the box (centered on the planet).
   - `width: var(--w, 2cqi);`: Sets the width of the orbiting pseudo-element (planet's moon/satellite).

---

### Keyframes for Rotation:

7. **Orbiting Animation**:
   ```css
   @keyframes rotate {
       to {
           offset-distance: 100%;
       }
   }
   ```
   - `@keyframes rotate`: Defines a keyframe animation called `rotate` where the element moves along a circular path.
   - `to { offset-distance: 100%; }`: Moves the element 100% around its defined path (a full orbit).

---

### Specific Styles for Sun and Planets:

Each planet has specific styles, including its size, orbit time, and appearance:

8. **Sun**:
   ```css
   .sun {
       --b: radial-gradient(circle, #f9d71c 0%, #f9a825 50%, #f9a825 100%);
       --d: 10cqi;
       --w: 8cqi;
       border: 0;
       &::after {
           animation: none;
           offset-path: none;
           place-self: center;
       }
   }
   ```
   - `--b`: A radial gradient representing the Sun's bright colors (yellow to orange).
   - `--d`: Defines the Sun's size (`10cqi`).
   - `&::after { animation: none; }`: The Sun doesn’t rotate like the planets.

9. **Planets (Mercury, Venus, Earth, etc.)**:
   Each planet is defined similarly with different values for its size (`--d`), color (`--b`), orbit time (`--t`), and the size of its orbiting moon (`--w`).

For example:

- **Mercury**:
  ```css
  .mercury {
      --b: radial-gradient(circle, #c2c2c2 0%, #8a8a8a 100%);
      --d: 15cqi;
      --t: 2105.26ms;
      --w: 2.0526cqi;
  }
  ```

- **Earth**:
  ```css
  .earth {
      --b: radial-gradient(circle, #3a82f7 0%, #2f9e44 80%, #1a5e20 100%);
      --d: 35cqi;
      --t: 6315.79ms;
      --w: 3.1579cqi;
  }
  ```

Each planet has:
- **`--b`**: A unique radial gradient representing its colors.
- **`--d`**: Its size (in `cqi`).
- **`--t`**: Its orbit duration (in milliseconds).
- **`--w`**: The size of its orbiting moon/satellite (if present).

---

### Final Summary:
This CSS simulates the solar system with the Sun and planets. The `li` elements represent the planets, each with custom animations that simulate orbits using the `::after` pseudo-element. The sizes, colors, and orbit speeds are unique to each planet, reflecting their relative positions and appearances in the solar system.
