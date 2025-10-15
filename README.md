HTML + CSS + JavaScript + jQuery
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Dynamic Image Slider</title>
 <!-- jQuery CDN -->
 <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
 <style>
 * {
 margin: 0;
 padding: 0;
 box-sizing: border-box;
 }
 body {
 display: flex;
 justify-content: center;
 align-items: center;
 height: 100vh;
 background: #111;
}
.slider {
 position: relative;
 width: 80%;
 max-width: 700px;
 overflow: hidden;
 border-radius: 10px;
 box-shadow: 0 0 20px rgba(255,255,255,0.3);
 }
 .slides {
 display: flex;
 transition: transform 0.5s ease-in-out;
 }
 .slides img {
 width: 100%;
 border-radius: 10px;
 }
 .btn {
 position: absolute;
 top: 50%;
 transform: translateY(-50%);
 background: rgba(255,255,255,0.6);
 border: none;
padding: 10px;
 cursor: pointer;
 font-size: 18px;
 border-radius: 50%;
 }
 .prev {
 left: 10px;
 }
 .next {
 right: 10px;
 }
 </style>
</head>
<body>
 <div class="slider">
 <div class="slides">
 <img src="https://picsum.photos/700/400?random=1" alt="">
 <img src="https://picsum.photos/700/400?random=2" alt="">
 <img src="https://picsum.photos/700/400?random=3" alt="">
 <img src="https://picsum.photos/700/400?random=4" alt="">
 </div>
 <button class="btn prev">&#10094;</button>
 <button class="btn next">&#10095;</button>
</div>
 <script>
 $(document).ready(function(){
 let currentIndex = 0;
 const slides = $(".slides img");
 const totalSlides = slides.length;
 function showSlide(index) {
 const offset = -index * 100 + "%";
 $(".slides").css("transform", "translateX(" + offset + ")");
 }
 $(".next").click(function(){
 currentIndex = (currentIndex + 1) % totalSlides;
 showSlide(currentIndex);
 });
 $(".prev").click(function(){
 currentIndex = (currentIndex - 1 + totalSlides) % totalSlides;
 showSlide(currentIndex);
 });
 // Auto slide every 3 seconds
 setInterval(function(){
 currentIndex = (currentIndex + 1) % totalSlides;
showSlide(currentIndex);
 }, 3000);
 });
 </script>
</body>
</html>
