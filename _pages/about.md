---
layout: about
title: about
permalink: /
subtitle: 

#profile:
#  align: right
#  image: 11.jpg
#  image_circular: false # crops the image to make it circular

selected_papers: false # includes a list of papers marked as "selected={true}"
social: false # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---
**The Robot Dexterity Lab @ Duke University**

The research goal of the Robot Dexterity Lab (DexLab) is human-level dexterity in robotic manipulation. In the DexLab, we believe that dexterity is a crucial manipulation capability that all robots will have in the future. Dexterity is not just manipulation with complex, high-DoF hands; it is the motion intelligence with vast complexity that still awaits more understanding.

Currently, we are exploring questions such as:

- How do we develop robot manipulation skills that are generalizable across tasks and transferable across robots?
- What new forms of dexterity are possible, and can all robots be dexterous in manipulation?
- What is the fundamental complexity of manipulation? Can we develop a formal framework to characterize its difficulty, robustness, and evaluation methods?
- What infrastructure best supports the development, integration, and benchmarking of generalizable manipulation skills?

<br>

<style>
  .gallery-container {
    max-width: 90vw;
    width: 560px;
    margin: auto;
    position: relative;
    height: 375px;
  }
  
  .gallery-slider {
    width: 100%;
    height: 100%;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .gallery-image {
    width: auto;
    height: 100%;
    max-width: 100%;
    object-fit: contain;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    display: block;
  }
  
  .gallery-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: transparent;
    color: #888;
    border: none;
    font-size: 2.5rem;
    padding: 0 16px;
    cursor: pointer;
    border-radius: 8px;
    height: 60px;
    width: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2;
    transition: all 0.3s ease;
  }
  
  .gallery-btn:hover {
    background: rgba(0,0,0,0.1);
    color: #555;
  }
  
  .gallery-prev {
    left: -60px;
  }
  
  .gallery-next {
    right: -60px;
  }
  
  .gallery-caption {
    text-align: center;
    margin-top: 10px;
    font-size: 1rem;
    color: #444;
  }
  
  .gallery-dots {
    text-align: center;
    margin-top: 10px;
  }
  
  .gallery-dot {
    display: inline-block;
    width: 10px;
    height: 10px;
    margin: 0 3px;
    border-radius: 50%;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  /* Responsive breakpoints */
  @media (max-width: 768px) {
    .gallery-container {
      max-width: 95vw;
      width: 100%;
      height: 300px;
    }
    
    .gallery-btn {
      font-size: 2rem;
      height: 50px;
      width: 50px;
    }
    
    .gallery-prev {
      left: -50px;
    }
    
    .gallery-next {
      right: -50px;
    }
    
    .gallery-caption {
      font-size: 0.9rem;
    }
  }
  
  @media (max-width: 480px) {
    .gallery-container {
      max-width: 98vw;
      height: 250px;
    }
    
    .gallery-btn {
      font-size: 1.5rem;
      height: 40px;
      width: 40px;
    }
    
    .gallery-prev {
      left: -40px;
    }
    
    .gallery-next {
      right: -40px;
    }
    
    .gallery-caption {
      font-size: 0.8rem;
    }
  }
</style>

<div class="gallery-container">
  <div class="gallery-slider">
    <button id="gallery-prev" class="gallery-btn gallery-prev">&#8592;</button>
    <img id="gallery-image" class="gallery-image" src="{{ 'assets/img/1.jpg' | relative_url }}" alt="Gallery Photo">
    <button id="gallery-next" class="gallery-btn gallery-next">&#8594;</button>
  </div>
</div>

<div id="gallery-caption" class="gallery-caption"></div>
<div id="gallery-dots" class="gallery-dots"></div>

<script>
  const images = [
    "{{ 'assets/img/img_4229_720.jpg' | relative_url }}",
    "{{ 'assets/img/img_4235_720.jpg' | relative_url }}",
    "{{ 'assets/img/lab_photos/IMG_4391.jpg' | relative_url }}",
    "{{ 'assets/img/lab_photos/IMG_4403.jpg' | relative_url }}",
    "{{ 'assets/img/lab_photos/IMG_4417.jpg' | relative_url }}",
    "{{ 'assets/img/lab_photos/IMG_4419.jpg' | relative_url }}",
    "{{ 'assets/img/lab_photos/IMG_4423.jpg' | relative_url }}",   

  ];
  const captions = [
    "DexLab Pickleball League, Summer 2025 Season",
    "DexLab Pickleball League, Summer 2025 Season",
    "Lab BBQ Party, Summer 2025",
    "Lab BBQ Party, Summer 2025",
    "Lab BBQ Party, Summer 2025",
    "Lab BBQ Party, Summer 2025", 
    "Lab BBQ Party, Summer 2025", 

  ];
  let current = 0;
  const img = document.getElementById('gallery-image');
  const dots = document.getElementById('gallery-dots');
  const caption = document.getElementById('gallery-caption');
  let timer;

  function showImage(idx) {
    img.src = images[idx];
    caption.textContent = captions[idx];
    dots.innerHTML = images.map((_, i) =>
      `<span class="gallery-dot" style="background:${i===idx?'#888':'#ccc'};" onclick="showImage(${i})"></span>`
    ).join('');
    current = idx;
    resetTimer();
  }

  function nextImage() {
    showImage((current+1)%images.length);
  }

  function resetTimer() {
    clearInterval(timer);
    timer = setInterval(nextImage, 3000); // Change image every 2 seconds
  }

  document.getElementById('gallery-prev').onclick = () => showImage((current-1+images.length)%images.length);
  document.getElementById('gallery-next').onclick = () => nextImage();

  window.showImage = showImage;
  showImage(0);
</script>
