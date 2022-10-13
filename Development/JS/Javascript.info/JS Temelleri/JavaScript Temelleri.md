- [[#Temel Yapılar|Temel Yapılar]]
- [[#Tip Dönüşümleri|Tip Dönüşümleri]]
	- [[#Tip Dönüşümleri#String Dönüşümü|String Dönüşümü]]
	- [[#Tip Dönüşümleri#Sayı Dönüşümü|Sayı Dönüşümü]]
	- [[#Tip Dönüşümleri#Boolean Dönüşümü|Boolean Dönüşümü]]
	- [[#Tip Dönüşümleri#Temel Operatörler|Temel Operatörler]]
	- [[#Tip Dönüşümleri#Matematiksel Operatörler|Matematiksel Operatörler]]
		- [[#Matematiksel Operatörler#String Toplaması|String Toplaması]]
	- [[#Tip Dönüşümleri#Eşleştirme Operatörü|Eşleştirme Operatörü]]
- [[#Karşılaştırmalar|Karşılaştırmalar]]


<br> 

# Temel Yapılar
JavaScript içinde 8 farklı değişken tipi vardır. Bunlar `number, bigInt, string, boolean, null, undefined, object, symbol` şeklindedir. Tanımladığımız değişkenin tipini `typeof()` fonksiyonu ile öğrenebiliriz.

Değişkenleri string içinde göstermek için ters tırnak kullanabiliriz

```js
let myName = "Furkan"
alert(`Welcome ${myName}`) // Welcome Furkan dönecektir
```

Ekrana yazdırmak için çeşitli yöntemler vardır. Bunlar `alert, prompt, confirm` fonksiyonlarıdır. Bu fonksiyonlar modal açacaktır ve bu modallar ise siteyle etkileşimi engelleyecektir. Alert fonksiyonu input almadan ekrana veri basar.

```js
alert("Hello World") // Ekrana sadece yazı basar
```

`prompt()` input alarak işlem yapar. Opsiyonel olarak input verisi de eklenebilir. Bu input verisi gelen modalda varsayılan değer olarak gösterilecektir.

```js
prompt("Şu anki yaşınız", 100) 
```

`confirm()` ise true false döndürecek şekilde bir modal açar. Modalda ok butonu true, modalı kapatmak veya iptal etmek ise false döndürecektir.

```js
let areYouGay = confirm("Why are you gay?")
alert(areYouGay) // OK butonu true ve cancel butonu false döndürecektir
```

# Tip Dönüşümleri

## String Dönüşümü
JS dinamik bir dildir. Bundan dolayı da değişkenlerin türleri, değişken tanımlandığı anda belirlenir. Bu belirlemeye göre işlemler yapılır, ancak bazı durumlarda tip dönüşümleri gerekebileceği için JS bu duruma izin vermektedir.

Örnek olarak `String(degisken)` şeklinde bir yapı ile kolay bir şekilde değişkenin türü stringe çevrilebilir.

## Sayı Dönüşümü
Eğer iki string içinde matematiksel işlem yapılırsa bu sonuç direkt olarak numerik değerlendirilir. Örneğin `alert("6" / "2")` şekildeki bir işlemin çıkışı numerik olabilir. Ayrıca string için yapılan işlemin aynısı bu kısımda da yapılabilir. Yani `Number(degisken)` şeklinde de dönüşüm yapılabilir. Ancak değişkenin numerik dönüşümü içerisinde alfabetik yapı bulursa dönüş NaN (Not a Number) dönebilecektir. Number dönüşümlerinin bazı sonuçları vardır.

| Değer            | Sonuç                                                                                                                                                                                                                    |
| :----------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| `undefined`      | `NaN`                                                                                                                                                                                                                    |
| `null`           | 0                                                                                                                                                                                                                        |
| `true and false` | 1 ve 0                                                                                                                                                                                                                   |
| `string`         | Baştan sona kadar olan tüm boşluklar silinir. Eğer kalan string boş ise sonuç 0 döner. Eğer metin varsa ve metin içerisinde alfabetik karakter yoksa sonuç içerideki sayı olacaktır. Bu da yoksa sonuç `NaN` dönecektir. |


## Boolean Dönüşümü
String gibi hızlı bir dönüşüm yapılabilir. Değişkenin tanımlı olma veya boş olma durumuna göre sonuçları `true` ve `false` olur.

```js
Boolean(1) // true
Boolean(0) // false
Booelan("Hello") // true
Boolean("") // false
```
Boş metin, 0 değeri, `null` , `undefined` ve `NaN` değerlerinin false döndürürken diğer tüm değerler true döner.


## Temel Operatörler
JS içerisinde operatörlerin çalışma mantığı, JS’nin tip dönüşümleri de hesaba katılırsa kafa karıştırabilecek alanlardan birisidir. Burada bilinmesi gereken üç terim işleri kolaylaştıracaktır.

**Operand:** Elimizdeki operatörler veya argümanların karşılığıdır. Örnek olarak `5*2` şeklindeki bir işlemde 5 ve 2 operand olarak tanımlanır.

**Unary:** Operatör eğer tek bir operand alıyorsa bunun adı unary olur. Yani `let x = 1; x = -x` dersek buradaki eksi işareti unary olacaktır.

**Binary:** Operatör eğer iki operand alıyorsa bunun adı binary olur. Yani `5*2` için çarpım operatörü binary olacaktır.

## Matematiksel Operatörler

JS içerisinde 6 matematiksel operatör vardır. Bunalr sırasıyla toplama, çıkarma, çarpma, bölme, kalan bulma ve üs almadır. Sırasıyla işaretleri `+, - , *, /, %, **` şeklindedir.

String içerisindeki matematiksel operatörlerin çalışma mantığı biraz değişiktir. Veri tiplerine göre matematiksel öperatörler tuhaf davranabilir.

### String Toplaması

Eğer operandlardan herhangi birisi veya ikisi string ise toplam da string olacaktır.

```js
"2" + "3" // Çıktısı "23" olur

"2" + 3 // Çıktısı "23" olur

2+2+"1" 
// Çıktısı "41" olur. Çünkü işlem önceliği ile önce sayılar toplanır sonra dönüşüm olur 

"1" + 2 + 2 
// Çıktısı "122" olur çünkü ilk operand string olduğu için diğer operatörler de string olacaktır.
```

## Eşleştirme Operatörü
```js
let a,b,c
a=b=c=2+2
//Yukarıdaki işlem aşağıdaki gibi yazılabilir

let a,b,c
c = 2+2
b=c
a=c
```

>[!info] Örnek Sorular
>```js
>"" + 1 + 0 // "10"
"" - 1 + 0 // -1
true + false // true
6 / "3" // 2
"2" * "3" // 6
4 + 5 + "px" // "9px"
"$" + 4 + 5 // "$45"
"4" - 2 // 2
"4px" - 2 // NaN
"  -9  " + 5 // " -9 5"
"  -9  " - 5 // -14
null + 1 // 1
undefined + 1 // 1 Hata: undefined değeri NaN olur
" \t \n" - 2 // -1 Hata: \t ve \n değerleri de boşluktur. Çıktı 0-2 olur
>```

# Karşılaştırmalar
Numerik karşılaştırmalarda normal matematiksel işlemler yapılabilirken string karşılaştırmasında işler değişir. Eğer iki string karşılaştırıyorsa iki stringin ilk karakterlerinden son karakterlerine kadar karşılaştırma yapılır. Tüm harfler aynı ise uzun olan, veya farklı olan harf varsa harfin numerik karşılığı büyük olan büyüktür. Alttaki kod örnek verilebilir. Karşılaştırmada unicode karakteri değerlendirilir.

```js
'Z' > 'A' // true, Z harfi sonra gelir
'Glow' > "Glee" // true, üçüncü harf olan o, e'den büyüktür
"Bee" > "Be" // true, ilk harf daha uzundur
```
Farklı tipte karşılaştırmalarda dönüşümler gerçekleştirilir. Değerler sayıya dönüştürülür.

Ayrıca strict equality dediğimiz sıkı karşılaştırma vardır. her ne kadar ` '' ` ifadesi false olsa da `==` operatörü ile karşılaştırma yapılması durumunda değer 0’a dönecektir. Bundan dolayı da `'' ==` false ifadesi true sonucu verecektir. Bunlar için `===` kullanılır. Örnek olarak

```js
null === undefined // false
0 === false // false
```

Yani türler arası dönüşüm olmadan karşılaştırma yapılır.