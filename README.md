# MWAD_EX05_image-carousel-in-react
## Date:09-11-2025

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
## App.jsx:
```
import React, { useState, useEffect } from "react";
import "./App.css";

const ImageCarousel = () => {
  const images = [
    "https://picsum.photos/800/400?random=1",
    "https://picsum.photos/800/400?random=2",
    "https://picsum.photos/800/400?random=3",
    "https://picsum.photos/800/400?random=4",
    "https://picsum.photos/800/400?random=5",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prev) => (prev + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  // Random start
  useEffect(() => {
    setCurrentIndex(Math.floor(Math.random() * images.length));
  }, []);

  return (
    <div className="carousel-container">
      <center>
        <h1>Image Carousel</h1>
        <h2>Name:Sharon Harshini L M</h2>
      </center>
      <div className="carousel">
        <img
          src={images[currentIndex]}
          alt="carousel"
          className="carousel-image"
        />
        <button className="nav-button prev" onClick={prevImage}>
          &#10094;
        </button>
        <button className="nav-button next" onClick={nextImage}>
          &#10095;
        </button>
      </div>

      <div className="dots">
        {images.map((_, i) => (
          <span
            key={i}
            className={`dot ${i === currentIndex ? "active" : ""}`}
            onClick={() => setCurrentIndex(i)}
          ></span>
        ))}
      </div>
    </div>
  );
};

export default ImageCarousel;

```
## App.css:
```
/* Overall container */
.carousel-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  background: linear-gradient(to right, #dbeafe, #fce7f3, #f3e8ff);
  min-height: 100vh;
  box-sizing: border-box;
}

/* Carousel box */
.carousel {
  position: relative;
  width: 100%;
  max-width: 800px;
  aspect-ratio: 2 / 1;
  overflow: hidden;
  border-radius: 20px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
  transition: transform 0.5s ease;
}

/* Image styling */
.carousel-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 20px;
  transition: transform 0.5s ease, filter 0.5s ease;
}

/* Navigation buttons */
.nav-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  color: white;
  font-size: 28px;
  background-color: rgba(0, 0, 0, 0.4);
  border: none;
  padding: 12px 16px;
  cursor: pointer;
  border-radius: 50%;
  transition: background-color 0.3s, transform 0.3s;
  z-index: 10;
}

.nav-button:hover {
  background-color: rgba(0, 0, 0, 0.6);
  transform: translateY(-50%) scale(1.1);
}

/* Button positions */
.prev {
  left: 10px;
}
.next {
  right: 10px;
}

/* Dots */
.dots {
  margin-top: 15px;
  text-align: center;
}

.dot {
  height: 14px;
  width: 14px;
  margin: 0 6px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.3s, transform 0.3s;
  cursor: pointer;
}

.dot.active {
  background-color: #2563eb;
  transform: scale(1.3);
}

/* Responsive adjustments */
@media (max-width: 1024px) {
  .carousel {
    max-width: 700px;
  }
}

@media (max-width: 768px) {
  .carousel {
    max-width: 95%;
  }
  .nav-button {
    font-size: 24px;
    padding: 10px 14px;
  }
  .dot {
    height: 12px;
    width: 12px;
  }
}

@media (max-width: 480px) {
  .nav-button {
    font-size: 20px;
    padding: 8px 12px;
  }
  .dot {
    height: 10px;
    width: 10px;
    margin: 0 4px;
  }
}

```
## OUTPUT
<img width="1912" height="1061" alt="image" src="https://github.com/user-attachments/assets/6ec5fa45-a4fd-4a4a-9040-317a8ba935ed" />
<img width="1919" height="1064" alt="image" src="https://github.com/user-attachments/assets/d2cc9f6b-01a0-415e-8cd5-b729c03bb0cb" />
<img width="1919" height="1063" alt="image" src="https://github.com/user-attachments/assets/65f2cc61-a2cc-47c4-98a2-6986a04d5bce" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
