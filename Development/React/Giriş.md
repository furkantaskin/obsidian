React'a girmeden öncesinde temel Javascript bilgilerinin yerine oturtulması büyük önem arz etmektedir. Bunun için mümkünse [Javascript Info](https://javascript.info) üzerinden veya tuttuğum [[Development/JS/Giriş |Javascript Notları]] üzerinden de inceleyebilirsiniz

# React Nedir

React, bir sanal DOM kullanarak sistem üzerinde anlık güncellemeler yapabilmeyi sağlayan, ara yüzler ve arayüz bileşenleri (biz bunlara component diyeceğiz) türetmeyi sağlayan bir JavaScript kütüphanesidir. Tek sayfa (single-page), mobil veya sunucu taraflu uygulamalar yapmayı sağlar. React kendi başına sadece durum yönetimi ve DOM renderlama işlemleri ile ilgilendiği için burada routing we istemci taraflı birçok işlemde eklentilerin kullanılması gerekmektedir. Bu seride de Reactı seri bir şekilde öğrenip kullanacağız.

# Ne Zaman Kullanılmalı
Eğer arayüz sürekli olarak bir değişime uğruyorsa ve arayüzde çok fazla manüpilasyon varsa React kullanılması uygundur. Çünkü React sanal bir DOM oluşturarak sayfa içinde sadece güncellenecek yeri güncelleyerek yoğun render performans sorunlarından biri kurtarır. 