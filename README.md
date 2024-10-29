<!DOCTYPE html>
<html lang="zh">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>动画示例</title>
  <style>
    .container {
      position: relative;
      width: 50px;
      /* 根据需要调整宽度 */
      height: 50px;
      /* 根据需要调整高度 */
    }

    .animated {
      position: absolute;
    }

    #image1 {
      top: 0;
      left: 0;
    }

    #image2 {
      top: 200px;
      left: 250px;
    }

    #image3 {
      top: 400px;
      left: 500px;
    }

    @keyframes rotate-scale {
      0% {
        transform: rotate(0deg) scale(1);
      }

      100% {
        transform: rotate(360deg) scale(0);
      }
    }

    .rotate-scale {
      animation: rotate-scale 1s forwards;
    }
  </style>
</head>

<body>
  <div class="container">
    <img src="https://bpic.588ku.com/element_origin_min_pic/19/03/07/91a550a5f58df34f52eb063d085370c5.jpg"
      class="animated" id="image1" height="150" width="300">
    <img src="https://bpic.588ku.com/element_origin_min_pic/19/03/07/91a550a5f58df34f52eb063d085370c5.jpg"
      class="animated" id="image2" height="150" width="300">
    <img src="https://bpic.588ku.com/element_origin_min_pic/19/03/07/91a550a5f58df34f52eb063d085370c5.jpg"
      class="animated" id="image3" height="150" width="300">
  </div>

  <script>
    function animateImage(image) {
      return new Promise((resolve) => {
        image.classList.add('rotate-scale');
        image.addEventListener('animationend', resolve, { once: true });
      });
    }

    async function runAnimations() {
      const images = document.querySelectorAll('.animated');
      for (const image of images) {
        await animateImage(image);
      }
    }

    runAnimations();
  </script>
</body>

</html>
