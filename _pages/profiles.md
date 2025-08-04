---
layout: profiles
permalink: /people/
title: people
hide_title: true
description: 
nav: true
nav_order: 2

profiles:
  - title: "PI"
    members:
      - name: "Dr. Alice Smith"
        position: "Assitant Professor of Robotics"
        image: "2.jpg"

  - title: "PhD Students"
    members:
      - name: "Jane Doe 1"
        position: "PhD student in ML"
        image: "3.jpg"
      - name: "Jane Doe 2"
        position: "PhD student in ML"
        image: "5.jpg"
      - name: "Jane Doe 3"
        position: "PhD student in ML"
        image: "6.jpg"
      - name: "Jane Doe 4"
        position: "PhD student in ML"
        image: "7.jpg"
      
---

## Photo Gallery

<div id="gallery-slider" style="max-width:700px; margin:auto; position:relative; height:375px;">
  <button id="gallery-prev"
    style="position:absolute; left:-60px; top:50%; transform:translateY(-50%); background:transparent; color:#888; border:none; font-size:2.5rem; padding:0 16px; cursor:pointer; border-radius:8px; height:60px; width:60px; display:flex; align-items:center; justify-content:center; z-index:2;">
    &#8592;
  </button>
  <img id="gallery-image" src="{{ 'assets/img/1.jpg' | relative_url }}" alt="Gallery Photo" style="height:100%; width:auto; max-width:680px; object-fit:cover; border-radius:8px; box-shadow:0 2px 8px rgba(0,0,0,0.08); display:block; margin:auto;">
  <button id="gallery-next"
    style="position:absolute; right:-60px; top:50%; transform:translateY(-50%); background:transparent; color:#888; border:none; font-size:2.5rem; padding:0 16px; cursor:pointer; border-radius:8px; height:60px; width:60px; display:flex; align-items:center; justify-content:center; z-index:2;">
    &#8594;
  </button>
</div>

<div id="gallery-caption" style="text-align:center; margin-top:0px; font-size:1rem; color:#444;"></div>
<div id="gallery-dots" style="text-align:center; margin-top:10px;"></div>

<script>
  const images = [
    "{{ 'assets/img/1.jpg' | relative_url }}",
    "{{ 'assets/img/2.jpg' | relative_url }}",
    "{{ 'assets/img/3.jpg' | relative_url }}"
  ];
  const captions = [
    "Lab group photo, 2024",
    "Robotics demo day",
    "Team at conference"
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
      `<span style="display:inline-block;width:10px;height:10px;margin:0 3px;border-radius:50%;background:${i===idx?'#888':'#ccc'};cursor:pointer;" onclick="showImage(${i})"></span>`
    ).join('');
    current = idx;
    resetTimer();
  }

  function nextImage() {
    showImage((current+1)%images.length);
  }

  function resetTimer() {
    clearInterval(timer);
    timer = setInterval(nextImage, 2000); // Change image every 2 seconds
  }

  document.getElementById('gallery-prev').onclick = () => showImage((current-1+images.length)%images.length);
  document.getElementById('gallery-next').onclick = () => nextImage();

  window.showImage = showImage;
  showImage(0);
</script>
