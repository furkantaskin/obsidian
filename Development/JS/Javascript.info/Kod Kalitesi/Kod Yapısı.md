# Syntax Yapısı

Mümkün olduğunca temiz ve okunabilir bir kod yazmak ileri aşamalarda bakım ve geliştirmeleri kolaylaştıracaktır.

Genel C++ ve Python kod yapısının yanı sıra lojik bloklar arasında birer satır boşluk bırakmak uygun olacaktır. Çok uzun satırlarda yeni satır kullanılabilir.

Eğer tek komutluk bir blok varsa süslü paranteze gerek yoktur. Tüm işlemler tek sarıda yapılabilir. Birden fazla işlem yapılacaksa süslü parantez ve alt satır uygun olacaktır. Ancak tek komutluk işlem uzunsa alt satıra inmek kaubl edilebilir.

Eğer if içerisinde uzun karşılaştırmalar varsa alt alta bu karşılaştırmaların yapılması daha iyi olacaktır. Diğer türlü kod uzuyacak ve takibi zorlaşacaktır.

```js
if (
  id === 123 &&
  moonPhase === 'Waning Gibbous' &&
  zodiacSign === 'Libra'
) {
  letTheSorceryBegin();
}
```