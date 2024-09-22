<template>
  <div id="app">
    <header>
    </header>

    <main>
      <div class="content">
        <section class="card">
          <h2>Click Counter</h2>
          <div class="counter">
            <p>Count: {{ count }}</p>
            <div class="counter-buttons">
              <button @click="decrementCount">-</button>
              <button @click="incrementCount">+</button>
            </div>
          </div>
        </section>

        <section class="card">
          <h2>Box Color Changer</h2>
            <div class="current-color-box" :style="boxStyle"></div>
            <div class="color-changer">
            <button class="btn" @click="changeColor">Change Color</button>
          </div>
        </section>

        <section class="card carousel-section">
          <h2>Image Carousel</h2>
          <div class="carousel">
            <img :src="currentImage" alt="Carousel Image" class="carousel-image" />
            <div class="carousel-controls">
              <button class="btn" @click="prevImage">Previous</button>
              <button class="btn" @click="nextImage">Next</button>
            </div>
          </div>
        </section>
        
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,

      colors: ['#007FFF', '#BFECFF', '#3357FF', '#F333FF', '#D6FF00'],
      currentColorIndex: 0,

      images: [
        'https://st5.depositphotos.com/36890770/66204/i/450/depositphotos_662044452-stock-photo-abstract-horizontal-background-any-design.jpg',
        'https://st3.depositphotos.com/11911276/37059/i/450/depositphotos_370597386-stock-photo-abstract-colored-moving-curved-lines.jpg',
        'https://st4.depositphotos.com/10667156/41497/i/450/depositphotos_414970266-stock-illustration-digital-painted-abstract-design-colorful.jpg'
      ],
      currentImageIndex: 0,
    };
  },
  computed: {
    currentImage() {
      return this.images[this.currentImageIndex];
    },
    boxStyle() {
      return {
        width: '100px',
        height: '100px',
        backgroundColor: this.colors[this.currentColorIndex],
        border: '1px solid black',
        margin: '10px 29%'
      };
    }
  },
  methods: {
    incrementCount() {
      this.count++;
    },
    decrementCount() {
      if (this.count > 0) {
        this.count--;
      }
    },
  
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    },
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style>

#app {
  text-align: center;
  color: #ffffff;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

header {
  margin-bottom: 30px;
}

h1 {
  color: #000000;
  margin: 5;
}

.content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  max-width: 1200px;
  width: 100%;
}

.card {
  padding: 20px;
  border-radius: 15px;
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
  color: #000000;
  background-color: #ffffff;
  padding: 75px;
  align-items: center;
}

.counter {
  font-size: 2em;
  margin: 10px 0;
}

.counter-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}


.carousel-section {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel-image {
  width: 100%;
  max-width: 350px;
  height: auto;
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  margin-bottom: 10px;
}


.current-color-box {
  width: 100px;
  height: 100px;
  margin: 10px auto 20px;
  border-radius: 15px;
  border: 2px solid #000000;
}
.btn {
  border-radius: 5px;
}
</style>