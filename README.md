# Ex05 Image Carousel
## Date: 28/05/2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
### Carousel.jsx:
```
import React, { useState, useEffect } from "react";
import "./Carousel.css";

import img1 from "./assets/img1.png";
import img2 from "./assets/img2.png";
import img3 from "./assets/img3.png";
import img4 from "./assets/img4.png";

function Carousel() {
  const images = [img1, img2, img3, img4];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);

    return () => clearInterval(interval);
  }, [currentIndex]);

  return (
    <div className="carousel-container">
      <h2>Image Carousel</h2>

      <img
        src={images[currentIndex]}
        alt="carousel"
        className="carousel-image"
      />

      <div className="buttons">
        <button onClick={prevImage}>⬅ Previous</button>
        <button onClick={nextImage}>Next ➡</button>
      </div>
    </div>
  );
}

export default Carousel;

```
### Carousel.css
```
.carousel-container {
  text-align: center;
  margin-top: 50px;
}

.carousel-image {
  width: 600px;
  height: 300px;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0,0,0,0.3);
}

.buttons {
  margin-top: 15px;
}

button {
  margin: 5px;
  padding: 10px 20px;
  border: none;
  background-color: #4CAF50;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
```

### App.jsx
```
import Carousel from "./Carousel";

function App() {
  return (
    <div>
      <Carousel />
    </div>
  );
}

export default App;
```

## OUTPUT

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/69f9b76d-e9da-4a27-b6c1-1e3ac98f9518" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3c7bd33a-c7d2-452b-b59e-d82b8f19cb65" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/16710ab7-e89c-4baf-a95f-fdf48c37b0b1" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1d6a64c6-2c72-496b-b223-a6cc707fdea2" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
