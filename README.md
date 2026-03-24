# Ex05 Image Carousel
## Date:

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
## Carousel.js
```
import React, { useState, useEffect } from "react";
import "./Carousel.css";

const Carousel = () => {
  const images = [
    "https://picsum.photos/id/1015/600/300",
    "https://picsum.photos/id/1016/600/300",
    "https://picsum.photos/id/1018/600/300",
    "https://picsum.photos/id/1020/600/300"
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prevIndex) => 
      (prevIndex + 1) % images.length
    );
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) => 
      (prevIndex - 1 + images.length) % images.length
    );
  };

  // Auto rotation
  useEffect(() => {
    const interval = setInterval(nextImage, 3000);

    return () => clearInterval(interval);
  }, []);

  return (
    <div className="carousel">
      <button onClick={prevImage}>Prev</button>

      <img 
        src={images[currentIndex]} 
        alt="carousel" 
      />

      <button onClick={nextImage}>Next</button>
    </div>
  );
};

export default Carousel;
```
## App.js
```
import React from "react";
import Carousel from "./Carousel";

function App() {
  return (
    <div>
      <h2>React Image Carousel</h2>
      <Carousel />
    </div>
  );
}

export default App;
```
## Carousel.css
```
.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.carousel img {
  width: 600px;
  height: 300px;
  border-radius: 10px;
}

button {
  padding: 10px;
  cursor: pointer;
}
```
## OUTPUT
<img width="1233" height="582" alt="image" src="https://github.com/user-attachments/assets/756d5f6f-8edf-4467-bed8-29c79dcbc7c0" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
