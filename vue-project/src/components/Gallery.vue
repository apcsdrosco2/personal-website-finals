<template>
  <div class="viewer">
    <img :src="images[currentIndex]" alt="Gallery Image" />
    <button class="button prev" @click="prevImage">‹</button>
    <button class="button next" @click="nextImage">›</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        "gallery/FB_IMG_1678370474189.jpg",
        "gallery/IMG_20250112_141404_0879.jpg",
        "gallery/IMG_20250112_141704_0530.jpg",
        "gallery/IMG_20250112_141725_0128.jpg",
        "gallery/IMG_20250115_131337.jpg",
        "gallery/IMG_20250115_131355.jpg",
        "gallery/IMG_20250115_131428.jpg",
        "gallery/IMG_20250115_131448.jpg",
        "gallery/IMG_20250115_131524.jpg",
        "gallery/IMG_20250115_131600.jpg",
        "gallery/IMG_20250115_131617.jpg",
        "gallery/IMG_20250115_131638.jpg",
        "gallery/IMG_20250115_131657.jpg",
        "gallery/IMG_20250115_131727.jpg",
        "gallery/IMG_20250115_131739.jpg",
        "gallery/IMG_20250115_131752.jpg",
        "gallery/IMG_20250115_131835.jpg",
        "gallery/IMG_20250115_131854.jpg",
        "gallery/IMG_20250115_131912.jpg",
        "gallery/IMG_20250115_131929.jpg",
        "gallery/IMG_20250115_131945.jpg",
        "gallery/IMG20230611204028.jpg"
      ],
      currentIndex: 0
    };
  },
  methods: {
    prevImage() {
      this.currentIndex = (this.currentIndex === 0) ? this.images.length - 1 : this.currentIndex - 1;
    },
    nextImage() {
      this.currentIndex = (this.currentIndex === this.images.length - 1) ? 0 : this.currentIndex + 1;
    }
  }
};
</script>

<style scoped>
.viewer {
    position: relative;
    width: 600px;
    height: 600px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
}

.viewer img {
    max-width: 100%;
    max-height: 100%;
    display: block;
}

.button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.6);
    color: #fff;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    font-size: 16px;
    border-radius: 5px;
    opacity: 0;
    transition: opacity 0.3s;
}

.button:hover {
    background-color: rgba(0, 0, 0, 0.8);
}

.viewer:hover .button {
    opacity: 1;
}

.button.prev {
    left: 10px;
}

.button.next {
    right: 10px;
}
</style>
