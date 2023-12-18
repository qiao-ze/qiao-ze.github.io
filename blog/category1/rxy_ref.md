---
title: 化学文摘
keywords: 计划
desc: teedoc 生成静态博客页面, 第一篇博客
author: derk
date: 2023-12-17
tags: hello, blog, teedoc
---

1. 铜催化Suzuki反应SP2-SP3的碳碳连接。https://pubs.acs.org/doi/10.1021/jacs.3c10628


<script src="https://3Dmol.csb.pitt.edu/build/3Dmol-min.js"></script>
  <div id="container-01" class="mol-container"></div>
<style>
.mol-container {
  width:    75%;
  height:   400px;
  position: relative;
}
<html>
</style>
  <script>
$(function() {
	let element = $('#container-01');
	let config = { backgroundColor : 'white' };
	let viewer = $3Dmol.createViewer( element, config );
	viewer.addModel("3\n\nC 0 0 0\nO 1.16 0 0\nO -1.16 0 0", "xyz");
	viewer.addUnitCell();
	viewer.setStyle({}, {sphere : {}});
	viewer.zoomTo();
	viewer.render();
});
</script>
<html>
