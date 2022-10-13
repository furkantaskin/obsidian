# if durumu
Birçok dildeki ile aynı mantıkta çalışır. Genel syntax yapısı şu şekildedir.

```js
// 1TBS yapısı kullanılmıştır

// Tip 1
let a,b
if(a > b)
	alert(a)
else
	alert(b)

// Tip 2
if(a>b) alert(a)

// Tip 3
if(a>b){
	alert(a)
	alert(b)
}
```

Aynı şekilde `else if` ve `else` yapısı mevcuttur.

Eğer yapılacak işlemde sonuc hızlı bir şekilde döndürülecekse uzun uzun if karşılaştırması yapılmasına gerek yoktur. Şu şekilde bir işlem de uygulanabilir (ternary)

```js
let accessAllowed = (age > 18) ? true : false;
```

Burada tek karşılaştırma yerine birden fazla da yapılabilir. Örnek olarak aşğıdaki kod verilebilir:

```js
let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';

alert( message );
```

Buradaki işleme göre önce yaşın üçe göre durumuna bakılır.

1.  Yaş üçten küçükse “Hi, baby” yaz
2.  Değilse
    1.  Yaş 18’den küçükse “Hello!” yaz
    2.  Değilse
        1.  Yaş 100’den küçükse “Greetings!” yaz
        2.  Değilse “What an unusual age!” yaz