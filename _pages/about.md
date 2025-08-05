---
layout: about
title: about
permalink: /
subtitle: The Robot Dexterity Lab @ Duke University

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
The research goal of the Robot Dexterity Lab (DexLab) is human-level dexterity in robotic manipulation. In the DexLab, we believe that dexterity is a crucial manipulation capability that all robots will have in the future. Dexterity is not just manipulation with complex, high-DoF hands; it is the motion intelligence with vast complexity that still awaits more understanding. 

Currently, we are exploring questions such as:
- How do we develop robot manipulation skills that are generalizable across tasks and transferable across robots?
- What new forms of dexterity are possible, and can all robots be dexterous in manipulation?
- What is the fundamental complexity of manipulation? Can we develop a formal framework to characterize its difficulty, robustness, and evaluation methods?
- What infrastructure best supports the development, integration, and benchmarking of generalizable manipulation skills?

<br>

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
    "{{ 'assets/img/img_4229_720.jpg' | relative_url }}",
    "{{ 'assets/img/img_4235_720.jpg' | relative_url }}",
  ];
  const captions = [
    "DexLab Pickleball League, Summer 2025 Season",
    "DexLab Pickleball League, Summer 2025 Season",
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
    timer = setInterval(nextImage, 3000); // Change image every 2 seconds
  }

  document.getElementById('gallery-prev').onclick = () => showImage((current-1+images.length)%images.length);
  document.getElementById('gallery-next').onclick = () => nextImage();

  window.showImage = showImage;
  showImage(0);
</script>
