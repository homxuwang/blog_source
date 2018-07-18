title: board
date: 2017-08-23 10:30:00
comments: ture

---
<div id="container"></div>
<link rel="stylesheet" href="https://imsun.github.io/gitment/style/default.css">
<script src="https://imsun.github.io/gitment/dist/gitment.browser.js"></script>
<script>
var gitment = new Gitment({
  owner: 'homxuwang', 
  repo: 'Hexo_Blog_Comments', 
  oauth: {
    client_id: '22479164a0e3d5b8e956',
    client_secret: '7ec8ecd84af8fd6769c8b2fecdb9548b4b232991',
  },
})
gitment.render('container')
</script>