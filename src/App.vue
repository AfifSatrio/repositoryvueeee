<template>
  <div class="container">
    <!-- Click Counter -->
    <div class="click-counter card">
      <h2>Click Counter</h2>
      <p class="counter-value">Counter: {{ counter }}</p>
      <button @click="increaseCounter" class="btn primary-btn">Increase Counter</button>
    </div>

    <!-- Box Color Changer -->
    <div class="box-color-changer card">
      <h2>Box Color Changer</h2>
      <div :style="{ backgroundColor: currentColor }" class="color-box"></div>
      <button @click="changeColor" class="btn secondary-btn">Change Color</button>
    </div>

    <!-- Image Carousel -->
    <div class="image-carousel card">
      <h2>Image Carousel</h2>
      <div class="carousel-container">
        <img :src="images[currentImageIndex]" class="carousel-image" />
      </div>
      <div class="carousel-controls">
        <button @click="prevImage" class="btn secondary-btn">Previous</button>
        <button @click="nextImage" class="btn secondary-btn">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Click Counter State
      counter: 0,

      // Box Color Changer State
      colors: ['red', 'green', 'blue', 'yellow', 'purple'],
      currentColor: 'red',

      // Image Carousel State
      images: [
        'https://via.placeholder.com/300x200/FF0000',
        'https://via.placeholder.com/300x200/00FF00',
        'https://via.placeholder.com/300x200/0000FF',
      ],
      currentImageIndex: 0,
    };
  },
  methods: {
    // Click Counter Method
    increaseCounter() {
      this.counter++;
    },

    // Box Color Changer Method
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.currentColor = this.colors[randomIndex];
    },

    // Image Carousel Methods
    prevImage() {
      if (this.currentImageIndex > 0) {
        this.currentImageIndex--;
      } else {
        this.currentImageIndex = this.images.length - 1;
      }
    },
    nextImage() {
      if (this.currentImageIndex < this.images.length - 1) {
        this.currentImageIndex++;
      } else {
        this.currentImageIndex = 0;
      }
    },
  },
};
</script>

<style scoped>
/* Styling for the entire container */
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  font-family: Arial, sans-serif;
}

/* Styling for the cards */
.card {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: center;
}

/* Click Counter */
.counter-value {
  font-size: 24px;
  font-weight: bold;
  margin: 10px 0;
}

/* Styling for buttons */
.btn {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.primary-btn {
  background-color: #007bff;
  color: white;
}

.primary-btn:hover {
  background-color: #0056b3;
}

.secondary-btn {
  background-color: #28a745;
  color: white;
}

.secondary-btn:hover {
  background-color: #218838;
}

/* Box Color Changer */
.color-box {
  width: 150px;
  height: 150px;
  margin: 20px auto;
  border-radius: 10px;
  transition: background-color 0.5s ease;
  border: 2px solid #ddd;
}

/* Image Carousel */
.carousel-container {
  position: relative;
  margin: 20px auto;
  width: 300px;
  height: 200px;
  overflow: hidden;
  border-radius: 10px;
}

.carousel-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 0.5s ease;
}

.carousel-controls {
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
}
</style>


