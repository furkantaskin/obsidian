- [[#Değişken Tanımlamaları|Değişken Tanımlamaları]]
- [[#Return İşlemi|Return İşlemi]]
- [[#Fonksiyon İsimlendirme|Fonksiyon İsimlendirme]]
- [[#Fonksiyon Tanımlamaları (Expression)|Fonksiyon Tanımlamaları (Expression)]]
- [[#Kısa Fonksiyonlar (Arrow Function)|Kısa Fonksiyonlar (Arrow Function)]]


# Fonksiyonlar Nedir

Fonksiyonlar tıpkı diğer dillerde olduğu gibi parametre alabilecek şekilde tanımlanabiliyor. Ayrıca argümanlar yine parantez içinden gönderiliyor.

```js
//Fonksiyon tanımlama
function functionName() {
  // Yapılacak işlemler
}

//Fonksiyon çağırma
functionName();

//Argümanlık fonksiyon
function functionName(param1, param2) {
  console.log(param1, param2);
}

functionName("Hello", "World");
// Bu durumda ekrana "HelloWorld" yazacaktır.
```

# Değişken Tanımlamaları

Değişkenlerin tanımlamaları JS’nin genel yapısından dolayı bir miktar değişim göstermekte. JS içerisinde local ve olmak üzere iki farklı tanımlama yapılabiliyor. Local tnımlamalarda değerler fonksiyon içinde oluşturulup fonksiyon dışında anlamını yitiriyor. Örneğin aşağıdaki kodda `alert(message)` kısmı hata verecektir çünkü `message` değişkeni fonksiyon içinde tanımlanmıştır.

```js
function showMessage() {
  let message = "Hello, I'm JavaScript!"; // local variable

  alert( message );
}

showMessage(); // Hello, I'm JavaScript!

alert( message ); // <-- Error! The variable is local to the function
```

Ancak burada aynı değişken isimleri kullanılabilir.

```js
let userName = 'John';

function showMessage() {
  userName = "Bob"; // (1) changed the outer variable

  let message = 'Hello, ' + userName;
  alert(message);
}

alert( userName ); // John before the function call

showMessage();

alert( userName ); // Bob, the value was modified by the function
```

Fonksiyon çağırmadan önce `userName` John iken fonksiyon çağırıldıktan sonra artık Bob değerini almıştır. Bunun bir diğer sebebi de `var` kullanılmamasıdır.

>[!info] Bilgi
>var ifadesi olmadan tanımlanan değişkenler direkt olarak global bir ölçekte tanımlanacaktır. Yani fonksiyon içinde dahi tanımlansalar, başka fonksiyonlarda da kullanılabileceklerdir.


# Return İşlemi

Fonksiyon içerisinde `return` komutu ile değer döndürülebilir. Eğer return boş gönderiliyorsa veya hiç return gönderilmiyorsa bu durumda fonksiyondan gelecek değer `undefined` olacaktır.

Return işleminde fonksiyon erişebildiği ilk return değerinden sonra işlemi bırakacaktır. Örnek olarak if ile kontrol edilen bir sistemde iki return varsa ve ilk returne erişilebiliyorsa, ikinci return es geçilecektir. Aşağıdaki kod örnek verilebilir

```js
function checkAge(age) {
  if (age >= 18) {
    return true;
  }
    return confirm('Do you have permission from your parents?');
  
}

let age = prompt('How old are you?', 18);

if ( checkAge(age) ) {
  alert( 'Access granted' );
} else {
  alert( 'Access denied' );
}
```

# Fonksiyon İsimlendirme

Fonksiyonlar genellikle bir işlem yapacağı için eylem bazlı isim alırlar. Örnek olarak kullanıcının yaş bilgilerini alan fonksiyon `getAge()` şeklinde olabilir.

>[!warning] Uyarı
>Eğer bir fonksiyon kullanılacaksa bu fonksiyon mutlak olarak tek bir işlem yapmalıdır. Örnek olarak `getAge()` fonksiyonunda sadece kullanıcının yaşı alınmalıdır. cinsiyetin de alınması ileri aşamalarda fonksiyonun kontrol edilmesini veya complex işlemlerde yanlış sonuçlar gelmesine sebep olacaktır.


# Fonksiyon Tanımlamaları (Expression)

Fonksiyonlar aslında birer değerdir. Yani değişkenlere fonksiyonlar atanabilir. Bu durumda değişken çağırmaya benzer şekilde fonksiyon çağırılabilir. Eğer değişkenin adı farklı ve fonksiyonun adı farklı ise, fonksiyonun tanımladığı değişken de fonksiyon çağırma gibi çağrılabilir.

```js
function sayHi() {   // (1) create
  alert( "Hello" );
}

let func = sayHi;    // (2) copy

func(); // Hello     // (3) run the copy (it works)!
sayHi(); // Hello    //     this still works too (why wouldn't it)
```

Ancak değişken parantezsiz çağrılırsa fonksiyonun kodunu ekrana yazdırabiliriz.

```js
function sayHi() {
  alert( "Hello" );
}

alert( sayHi ); // shows the function code
```

# Kısa Fonksiyonlar (Arrow Function)

Kısa fonksiyonlar hızlı bir şekilde temel fonksiyon oluşumuna izin veren yapılardır. Diğerlerine benzer şekilde argüman alarak bir return değerini hızlıca döndürmeyi sağlar.

```js
let func = (arg1, arg2, ..., argN) => expression; //Alttaki fonksiyon ile aynıdır

let func = function(arg1, arg2, ..., argN) {
  return expression;
};
```

>[!warning] Uyarı
>Eğer kısa fonksiyon çağırılacaksa ve argüman yoksa parantezin yine de konulması gerekir. Yoksa fonksiyon çalışmayacaktır.
