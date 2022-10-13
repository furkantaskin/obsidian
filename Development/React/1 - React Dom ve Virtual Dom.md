---
title: "React Dom ve Virtual DOM"
description: "DOM ve Virtual DOM'a giriş"
order: 1
---

# React DOM ve Virtual DOM

Bir  internet sayfasına girdiğimizde aslında gördüğümüz html etikletler içindeki yapıya DOM (Document Object Model)[^1] denir.

Virtual DOM ise elimizdeki mevcut DOM değerinin bir kopyasını tutar. Eğer yapılan işlemde VDOM ile DOM arasında fark oluşursa React bunu görüp sadece değişen yeri DOM içerisinde günceller. 

[^1]: [Introduction to the DOM - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)