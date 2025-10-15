<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Toby Chen</title>
  <style>
    body {
      font-family: 'Fira Code', monospace;
      background-color: #0f0f0f;
      color: #e5e5e5;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    h1 {
      font-size: 2.5em;
      margin-bottom: 0.5em;
    }
    p {
      font-size: 1.2em;
      color: #8f8f8f;
    }
  </style>
</head>
<body>
  <h1>👋 Hey, I'm <span id="typed"></span></h1>
  <p>Mathematics Student at <strong>Queen Mary University of London</strong></p>

  <script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.12"></script>
  <script>
    new Typed('#typed', {
      strings: ['Toby Chen', 'a Developer', 'a Problem Solver', 'a Creator'],
      typeSpeed: 70,
      backSpeed: 50,
      loop: true
    });
  </script>
</body>
</html>
