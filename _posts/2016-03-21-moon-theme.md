---
layout: project
title:  "Moon Jekyll Theme"
date:   2016-04-06
excerpt: "Minimal, one column Jekyll theme for your blog."
project: true
tag:
- jekyll 
- moon
- blog
- about
- theme
comments: true
---

<html>

<head>
  <meta charset="utf-8" />
  <title>Minesweeper</title>
  <link rel="stylesheet" href="style.css">
</head>

<body>
  <h1>Minesweeper</h1>
  <div id="menuboard">
    <button id="easy">easy</button>
    <button id="normal">normal</button>
    <button id="hard">hard</button>
    <div class="timer three"></div>
    <div class="timer two"></div>
    <div class="timer one"></div>
  </div>
  <div id="gameboard">
    <table id="table">
      <thead>
      </thead>
      <tbody></tbody>
    </table>
    <div id="result"></div>
  </div>
  <script src="./app.js"></script>
</body>

</html>