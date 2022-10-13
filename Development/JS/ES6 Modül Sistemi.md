---
title: "ES6 ile Modül Sistemi"
description: "ES6 ile hayatımıza giren modül sistemi"
---

# Modül Sistemi

ES6 ile import ve export sistemi hayatımıza girdi. Bu sayede çok sayıda modülü tıpkı Python gibi kullanabiliyoruz. Burada dilersek kendi modülümüzü yazıp kullanabiliriz.

>[!info] Bilgi
>Öncelikle `npm init` ile bir package.json dosyası oluşturuyoruz. Burada modül yapısı gerekeceği için oluşan package.json içine `"type": "module"` şeklinde bir ekleme yapmamız gerekir yoksa `Cannot use import statement outside a module` hatası ile karşılaşabiliriz.


Artık bu işlemleri yapabiliriz. Öncelikle iki farklı js dosyası açıyoruz.

	src
	| - index.js
	| - my-module.js

Sırasıyla artık dosyalarımızı yazabiliriz

```js:my-module.js
const topla = (a,b) => a+b
 
export default topla
```

```js:index.js
import Topla from './my-module.js'  
  
console.log(Topla(2,4))
```

index dosyasını çalıştırdığımızda bize 6 çıktısını verecektir.

Peki modül içinde iki fonksiyon olursa ne olacak? İşte bu durumda ayırmamız gerekecek

```js:my-mdoule.js
const hello = () => {console.log("Hello")}
```

Artık dışarı aktarırken `export` komutunu kullanabiliriz.

```js:my-module.js
export const topla = (a,b) => a+b
export const hello = () => {console.log("Hello")}
```

```js:index.js
import {hello, topla} from './my-module.js'
console.log(topla(2,4))
hello()
```

Çalıştırdığımızda hello ve 6 değerleri dönecektir. Dilersek bunları topluca export edebiliriz. Örneğin

```js:my-module.js
const topla = (a,b) => a+b
const hello = () => {console.log("Hello")}

export {hello, topla}
```

Ancakl birden fazla fonksiyonumuz varsa burada default olarak alınacağı belirtebiliriz. 

```js:my-module.js
const hello = () => {console.log("Hello")}  
  
export const cikar = (a,b) => a-b  
export const topla = (a,b) => a+b  
  
export default hello
```

```js:index-js
import DefExport from './my-module.js'  
  
DefExport()
```

Bu durumda burada `DefExport` yazan yer otomatik olarak modül içinden default olarak export edilen fonksiyonu baz alacaktır.

Diğer fonksiyonları da alabiliriz.

```js:index.js
import DefExport, {topla, cikar} from './my-module.js'  
  
DefExport()
```

Bu şekilde de yapabiliriz.