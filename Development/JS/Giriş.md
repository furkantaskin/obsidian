JavaScript'te dair temel bilgiler bu şekildedir. Ancak dilenirse diğer kaynaklara da ulaşılabilir[^bignote]

[^bignote]: -  [Javascript Info](https://javascript.info)
	- [Github Javascripting](https://github.com/workshopper/javascripting)
	- [W3Schools Javascript](https://www.w3schools.com/js/)

# Değişken Tipleri

JavaScript içinde temel değişken tipleri string, number, boolean, undefined ve nulldur.

# Dizilerde Temel Manipülasyon Yöntemleri

Çeşitli yöntemler var. Örneğin `.(push)` gibi. Burada dizinin sonuna eleman ekliyorsun.

```js
var myArray = [["selam", 1], ["seni", 2]];
myArray.push(["salak şey",3]);
```

Bir diğer yöntem ise `.(pop)` olayı. Bu olayda ise dizideki son elemanı koparıyor ve ekleneceği yer varsa ekliyor. Mesela

```js
var myArray = [["selam", 1], ["seni", 2]];
var newOrphan = myArray.pop();
```

`.pop()` metodunun tam tersi ise `.shift()` olayı. Bunda ise olay dizideki ilk elemanı söküp almak.

```js
var myArray = [["selam", 1], ["seni", 2]];
var newOrphan = myArray.shift();
```

Mesela `.shift()` olayının tam tersi ise `.unshift()` olayı. Bunda ise amaç dizinin başlangıcına eleman eklemek.

```js
var myArray = [["selam", 1], ["seni", 2]];
myArray.shift();
myArray.unshift(["birnevi", "farklı şeyler"]);

```


`map()` kullanımı ile dizi içerisindeki tüm elemanlarda belirtilen fonksiyonu uygular. Örnek olarak elimizde bir dizinin tüm elemanlarının iki katını bulup yeni bir diziye basmak istedik. Bunu `.map()` metodu ile rahatça yapabiliriz. Mesela ^b65988

```js
const array1 = [1, 4, 9, 16];

const map1 = array1.map(x => x * 2);

console.log(map1);
```

^2891a3

Buradaki çıktı [2,8,18,32] şeklinde olacaktır.

---

# Fonksiyonlar

Fonksiyonları zaten diğer programlama dillerinden biliyoruz. Burada syntax yapısı genel olarak değişiyor.

```js
//Fonksiyon tanımlama
function functionName() {
  // Yapılacak işlemler
}

//Fonksiyon çağırma
functionName();
```

Buradaki fonksiyonlarda parantez içi argüman alanı oluyor. Diğer dillerdeki gibi yani. Argümanlı bir fonksiyon kullanılacaksa eğer şu şekilde yaparız:

```js

function functionName(param1, param2) {
  console.log(param1, param2);
}

functionName("Hello", "World");
// Bu durumda ekrana "HelloWorld" yazacaktır.
```

>[!info] Bilgi
>var ifadesi olmadan tanımlanan değişkenler direkt olarak global bir ölçekte tanımlanacaktır. Yani fonksiyon içinde dahi tanımlansalar, başka fonksiyonlarda da kullanılabileceklerdir.


Localdeki değişkenler ile globaldeki değişkenlerin adı aynı olsa da JS içinde fonksiyonlarda lokal değişkenlerin değerleri baz alınacaktır.

```js
var myVar = 1;
function anyFunction(){
	var myVar = 2;
	return myVar;
}

anyFunction();
```

>[!info] Bilgi
>return kısmında sadece sonucu değil, sonucu işlem yaptırarak da döndürebiliriz.


Eğer fonksiyon içinde return yoksa, fonksiyonun çağırılması sonucunda dönecek değer undefined olacaktır. Yani

```js
var total = 1;
function someFunct(){
	total = total + 2;
}

someFunct();
```

Fonksiyonlarda eğer hızlı bir kaşılaştırma varsa if else kullanmadan da işlem yapılabilir. Örneğin iki sayı arasındaki büyüklük küçüklüğü görmek istiyorsak şunu yapabiliriz

```js
function isLess(a,b){
	return a < b
}

isLess(10,15);
```

Rekürsif fonksiyonlarda ise olay, belirli bir kırılma noktası gelene kadar fonksiyonun kendini tekrar etmesidir. Döngüler yerine de kullanılabilirler. Örneğin

```js
function multiply(arr, n) {
    var product = 1;
    for (var i = 0; i < n; i++) {
        product *= arr[i];
    }
    return product;
	  }
```

Örneğin diziye 1'den belirli bir sayıya kadar olan elemanı bastırma fonksiyonu şu şekildedir

```js
function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.push(n);
    return arr;
  }
}

// Bu diziyi tersine yazdırmak için

function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.unshift(n);
    return arr;
  }
}

// İki sayı arasında bir dizi oluşturmak için

function rangeOfNumbers(startNum, endNum) {
   if (startNum > endNum){
     return []
   } else{
     const myArray = rangeOfNumbers(startNum, endNum - 1);
     myArray.push(endNum);
     return myArray;
   }
};
```

---

# If...else Yapısı

C++ diline göre neredeyse bir farkı yok. Syntax yapısı aynı. Boolean tanımlamalarında da true-false olayı var.

```js
var deneme = true;
if(deneme){
	console.log("Şu anda doğru");
} else{
	console.log("Şu anda yanlış");
}
```

Yalnız burada dikkat edilmesi gereken kısım `1 == 1` olsa da aynı şekilde `1 == "1"` ve `"1" == 1` olabiliyor. Bu durumda [**Type Coersion**](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion) adı veriliyor. Bu durumun önüne geçebilmek için üç eşittir kulanmak gerekiyor. Yani `1 === "1"` değeri false dönerken `1 === 1` değeri true dönecektir.

>[!info] Bilgi
>Bir değişkenin türünü öğrenmek için `typeof` kullanabiliriz. Yani `typeof 42 = number` olacaktır.

---

# Switch-Case Yapısı

Aynı şekilde C++ diline benzer bir yapısı var. Şu şekilde gösterebiliriz

```js
var islemeGirecekDegisken;
var cevap;
switch(islemeGirecekDegisken){
	case 1:
		cevap = 1;
		break;
	case 2:
		cevap = 2;
		break;
	case 3:
		cevap = 3;
		break;
	default: 
		cevap = 0;
		break;
}
```

Eğer birden fazla seçenekte aynı şık dönecekse hepsine tek tek case açmak zorunda değiliz. Şu şekilde bir kullanım da uygundur

```js
var islemeGirecekDegisken;
var cevap;
switch(islemeGirecekDegisken){
	case 1:
	case 2:
	case 3:
		cevap = 3;
		break;
	case 4:
		cevap = 4;
		break;
	default: 
		cevap = 0;
		break;
}
```

---

# Nesneler

Nesneler (objects) diziler gibi çalışsa da dizilerden farklı olarak bir de özellik elemanına sahiptir. Yani dizilerde `[1,2,3]` şeklinde giderken nesnelerde `["name": "Furkan", "Surname": "Taşkın"]` şeklinde bir sıralama yapılabilir. Özellikle yapılı bir şekilde veri tutmada avantajları vardır. Örneğin aşağıdaki gibi tutulabilir. Hatta elemanlar bir dizi de olabilir.

```js
var exampleArray = ["Name", "Furkan", "Surname", "Taşkın"]
var exampleObject = {
	"name": "Furkan",
	"surname": "Taşkın",
	"age": 25,
	"gender": "male",
	"aliases": ["Taşkın", "Hacı", "Başkan", "Kanka", "Müdür", "Yeğen"]
};
```

Bu verileri okumak için iki farklı yöntem kullanabiliriz. Bunlar dot ve bracket tanımlamaları olarak geçmektedir. Dot tanımlamasında `object.prop1` şeklinde nesne içindeki elemanı çağırabilirken bracket tanımlamasında `object["prop1"]` olarak çağırabiliriz. Bu kısımda bracket için tırnak gerekirken dot için tırnağa gerek yoktur. Yani

```js
var exampleObject = {
	"name": "Furkan",
	"surname": "Taşkın",
	"age": 25,
	"gender": "male",
	"aliases": ["Taşkın", "Hacı", "Başkan", "Kanka", "Müdür", "Yeğen"]
};

exampleObject.name // Furkan ibaresi dönecektir
exampleObect["name"] // Aynı şekilde Furkan ibaresi dönecektir
```

Ayrıca nesnelerden veri çağırılırken dinamik yapı da kullanılabilir. Örnek olarak kullanıcıdan gelen veri bir değişkende tutularak bu değişkenin özelliği nesne içinde aranabilir.

```js
var testObj = {
  12: "Namath",
  16: "Montana",
  19: "Unitas"
};
var playerNumber = 16;
var player = testObj[playerNumber];
```

Nesnelerin özelliklerini tıpkı diğer değişkenler gibi değiştirebiliriz.

```js
var exampleObject = {
	"name": "Furkan",
	"surname": "Taşkın",
	"age": 25,
	"gender": "male",
	"aliases": ["Taşkın", "Hacı", "Başkan", "Kanka", "Müdür", "Yeğen"]
};

exampleObject.name = "Muffin";
```

Ayrıca nesneler içine tıpkı değişiklikteki koda benzer şekilde yeni elemanlar ekleyebiliriz.

```js
var exampleObject = {
	"name": "Furkan",
	"surname": "Taşkın",
	"age": 25,
	"gender": "male",
	"aliases": ["Taşkın", "Hacı", "Başkan", "Kanka", "Müdür", "Yeğen"]
};

exampleObject.height = 185; // Dot notation
exampleObject["height"] = 185 // Bracket notation
```

Nesnelerden veri silmek içinse `delete` özelliğini kullanırız.

```js
var exampleObject = {
	"name": "Furkan",
	"surname": "Taşkın",
	"age": 25,
	"gender": "male",
	"aliases": ["Taşkın", "Hacı", "Başkan", "Kanka", "Müdür", "Yeğen"],
	"height": 185
};

delete exampleObject.height;
```

Nesneler içinde diziler veya diziler içinde nesneler, hatta diziler içinde nesneler içinde diziler tutulabilir. Örneğin

```js
var myMusic = [
  {
    "artist": "Billy Joel",
    "title": "Piano Man",
    "release_year": 1973,
    "formats": [
      "CD",
      "8T",
      "LP"
    ],
    "gold": true
  },
  {
    "artist": "Furkan",
    "title": "Big Brother",
    "release_year": 2021,
    "formats": [
      "CD",
      "8T",
      "LP"
    ]
  }
];
```

Burada içeriye erişmek için notasyonların birleştirilmesi gerekebilir. Örneğin "**Big Brother**" kısmına erişmek için `myMusic[1].title` şeklinde bir kullanım gerekir. Veya şu şekilde de kullanılabilir

```js
var ourStorage = {
  "desk": {
    "drawer": "stapler"
  },
  "cabinet": {
    "top drawer": { 
      "folder1": "a file",
      "folder2": "secrets"
    },
    "bottom drawer": "soda"
  }
};
ourStorage.cabinet["top drawer"].folder2; // Sonuç: a file
ourStorage.desk.drawer; // Sonuç: stapler

```

Burada eğer bir nesne içinde belirtilen özelliğin olup olmadığını bulmak istiyorsak `object.hasOwnProperty()` metodunu kullanabiliriz. Örneğin

```js
var exampleObject = {
	"name": "Furkan",
	"surname": "Taşkın",
	"age": 25,
	"gender": "male",
	"aliases": ["Taşkın", "Hacı", "Başkan", "Kanka", "Müdür", "Yeğen"],
	"height": 185
};

console.log(exampleObject.hasOwnProperty("name")); // True dönecektir
console.log(exampleObject.hasOwnProperty("relations")); // False dönecektir
```

---

# Döngüler

## While Döngüsü

C++ ile aynı mantıkta çalışıyor. Çok bir fark yok

```js
var i = 0;
while ( i < 6){
	console.log(i);
	i++;
}
```

## For Döngüsü

C++ ile aynı mantıkta çalışıyor. Görünürde fark yok

```js
for(var i = 0; i <=5; i++){
	console.log(i);
}
```

Veri boyutlarına göre de çalışabiliriz. Örneğin

```js

var myArr = [2, 3, 4, 5, 6];
var total = 0;
for (var i = 0; i < myArr.length; i++){
  total += myArr[i];
}
```

---

# Denemeler

Örneğin, rehberde belirli özellikleri ile kayıtlı kişiler olsun. Buraya gönderilen argümanların rehberde olup olmadığı kontrol edilecek ve varsa o veriler dönecek.

```js
var contacts = [
    {
        "firstName": "Akira",
        "lastName": "Laine",
        "number": "0543236543",
        "likes": ["Pizza", "Coding", "Brownie Points"]
    },
    {
        "firstName": "Harry",
        "lastName": "Potter",
        "number": "0994372684",
        "likes": ["Hogwarts", "Magic", "Hagrid"]
    },
    {
        "firstName": "Sherlock",
        "lastName": "Holmes",
        "number": "0487345643",
        "likes": ["Intriguing Cases", "Violin"]
    },
    {
        "firstName": "Kristian",
        "lastName": "Vos",
        "number": "unknown",
        "likes": ["JavaScript", "Gaming", "Foxes"]
    }
];

function lookUpProfile(name, prop) {
 
    for(let i = 0; i < contacts.length; i++){
        if(contacts[i].firstName === name){
            if(contacts[i].hasOwnProperty(prop)){
                return contacts[i][prop];
            } else{
                return "No such property";
            }
        }
    } 
    return "No such contact";
}

lookUpProfile("Akira", "likes"); // ["Pizza", "coding", "Brownie Points"] dönecektir
```

---

# Özel Fonksiyonlar

## Math Random

`Math.random()` fonksiyonu 0 ile 1 arasında (1 dahil olmayacak şekilde) sayı döndürmeyi sağlar. 0'dan sonra 16 basamak şeklinde sayı döndürecektir.

```js
Math.random() // 0 ile 1 arasında dönecektir, yani 0.0612259125356478 dönecektir
console.log(Math.floor(Math.random() * 10)) // 0 ile 9 arasında tam sayı döndürecektir
Math.floor(Math.random() * (max-min + 2)) + min; 
// Max ve Min değer de dahil şekilde sonuç döndürecektir
```

## ParseInt

String değeri integer değere çevirmeyi sağlar. Eğer alınan metin içindeki ilk karakter bir sayı değilse bu durumda NaN (Not a Number) döndürür. 0'dan farklı ilk sayıyı görene kadar tüm sıfırları silecektir. Ayrıca metin içinde eğer harf varsa o harfe gelene kadar olan sayıları yazıp o harften sonrasını es geçecektir.

```js
var a = parseInt("a013") // NaN
var b = parseInt("013a") // 13
var c = parseInt("315a213") // 315
var d = parseInt("0000002") // 2
```

`parseInt()` fonksiyonu ikinci bir argüman alır. Bu argüman'a radix nedir. Radix, girilen değerin hangi tabanda çevrileceğini söyler. Böylece çıktı değişebilir. Örneğin

```js
var a = parseInt("11") // 1
var b = parseInt("11",2) // 3 (2 tabanında işlem yaptı)
```

---

## Ternary Karşılaştırma Operatörü

PHP içinde kullanımına benzer 3 argümanlı bir operatör. Uzun uzun if/else yazmak yerine hızlı bir şekilde karşılaştırma yapıp sonuç döndürmeyi sağlıyor. Örneğin

```js
a == b ? "Bu sayılar eşit" : "Sayılar eşit değil"
```

Bu kısımda soru işaretinin solundaki kısım koşulu içerirken sağdaki kısım sonuçları içerir. İlk sonuç, soldaki koşulun doğru olması durmunda çalışırken son sonuç ise yanlış olması durumunda çalışır.

```js
var a = true
a ? "A is true" : "A is false" // "A is true" dönecektir

var b = false
b ? "B is true" : "B is false" // "B is false" dönecektir

return a == b ? "Equal" : "Not equal" // Döndürülecek değer, koşula göre belirlencektir
```

Ayrıca bu kısımda çoklu olarak da kullanılabilir

```js
var a = 1
var b = 0

a === b ? 
: (a > b) ? "a is greater"
: "b is greater" // A ile b sayısının eşitliğini kontrol ediyor 
```

---

# ES6

`let` ifadesi, `var` ifadesi gibi değişken tanımalamada kullanılır. Ancak farklı olarak değişkendeki verinin değiştirilmesini önler. Eğer değiştirilmesi gereken ifadeler varsa, let ifadesi kullanılabilir. Ayrıca var ifadesi global bir tanımlamadır. Ancak fonksiyon içinde kullanılırsa lokal olur. Ancak let, bulunduğu herhangi bir blok içinde tanımlanması durumunda sadece o blok içinde geçerli olur. Ayrıca bir fonksiyon ve fonksiyon içindeki blokta aynı isimde iki varklı değişken `let` ile tanımlanırsa bu iki değişkenin değeri birbirinden farklı olur.

```js
function letTest() {
  let x = 1;
  {
    let x = 2;
    console.log(x);  // Blok içindeki let olduğundan ötürü 2 olacaktır
  }
  console.log(x);  // Blok içindeki x değeri yerine fonksiyon içindekini alacaktır
}
```

`const` ifadesi, var gibi global olan ama değiştirilemeyen değişkenlere denir. Bu durumda const için verilen değişkenlerin değerleri program içinde tekrar değiştirilemez. Ancak diziler gibi nesnelerde de const tanımı kullanılırsa işler biraz değişir. Tüm diziye müdahale edilmediği sürece dizi içindeki herhangi bir eleman değişebilir. Tüm dizinin elemanları teker teker atama yapılarak değiştirilebilir ancak tek bir tanımlama ile değiştirilemez.

```js
const newArray = [1,2,3]
newArray = [2,3,4] // Hata verir
newArray[2] = 5
console.log(newArray) // [1,2,5] dönecektir. 
```

Eğer tüm dizinin işleme karşı kapatılması gerekiyorsa o zaman `Object.freeze()` metodu kullanılır. Bu metod nesnenin müdahaleye kapanmasını ve mevcut verilerle kalmasını sağar.

```js
let newObj = {
    "name" : "Furkan",
    "age": 25
}

Object.freeze(newObj)
newObj.name = "Muffin"
console.log(newObj) // Name kısmında Muffin yerine Furkan dönecektir
```

Fonksiyon tanımlarında uzun uzun fonksiyon ismi yazmamıza gerek kalmayabilir. Örneğin myFunc şeklindeki bir değişkene fonksiyon atanırken `function()` yerine `const myFunc = () =>` şeklinde bir kullanım da yapabiliriz.

```js
const myFunc = function() {
  const myVar = "value";
  return myVar;
}

// Alternatifi
const myFunc = () => {
  const myVar = "value";
  return myVar;
}

const myFunc = () => "value";
```

Ayrıca bu fonksiyonları parametre ile de oluşturabiliriz

```js
const doubler = (item) => item * 2;
doubler(4); // 8 sonucu dönecektir

const multiplier = (item, multi) => item * multi;
multiplier(4, 2); // Aynı şekild 8 sonucu dönecektir
```

Rest parametresi ile bir fonksiyonda parametre sınırlaması olmadan dilediğimiz kadar veri gönderebiliriz. Burada fonksiyon içine `...args` şeklinde bir gönderim yapmak yeterlidir. Örnek olarak n elemanlı bir dizinin elemanları toplamını bulmak için şu şekilde bir yöntem izlenebilir

```js
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3)); // 6
```

Buradaki `reduce()` metodu, dizinin tüm elemanlarında tıpkı bir for döngüsü gibi dönerek elemanlar üzerinde işlem yapar. Reduce içine yapılacak işlemi gönderebiliriz. Sadece toplama değil çarpma da yapılabilir.

Spread operatörleri tüm elemanlar üzerinde teker teker işlem yapmaktadır. Çoklu parametre bekleyen işlemlerde de rahatlıkla kullanılabilir. Örnek olarak

```js
const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr2;

arr2 = [...arr1]

console.log(arr2);
```

Yıkıcı tanımlama (destructing assignment) bir nesne içinden uzun uzun veri çekmek yerine tek seferde birden fazla veri çekmeyi sağlar. Şöyle ki:

```js
const HIGH_TEMPERATURES = {
  yesterday: 75,
  today: 77,
  tomorrow: 80
};

const {today, tomorrow} = HIGH_TEMPERATURES; // {today: 77, tomorrow: 80} çıktısı gelir

```

Bunu yeni değişkenlere de atayabiliriz. Örnek olarak

```js
const HIGH_TEMPERATURES = {
  yesterday: 75,
  today: 77,
  tomorrow: 80
};

const {today: highToday, tomorrow: highTomorrow} = HIGH_TEMPERATURES; // {today: 77, tomorrow: 80} çıktısı gelir

```