# Fetch API
Fetch API, api üzerinden gelen verilerin erişimine ve bu verilerin düzenlenmesine olanak sağlayan bir arayüzdür. Ajax yerine asenkron verip alıp veri göndermemizi sağlar. Asenkron bir yapıdadır.

Örneğin aynı dizinde bulunan bir `settings.json` dosyasından verileri çekip bastırmayı şöyle yapabiliriz. Dosya yapımızın şöyle olduğunu düşünelim

	src
	|--index.js
	|--settings.json

```js:index.js 
fetch("settings.json").then(response => {  
    console.log(response)  
})
```

```json:settings.json
{  
  "userName": "muffinisamuffin",  
  "password": 1234,  
  "serverIP": "127.0.0.1",  
  "serverName": "crater.com.tr",  
  "isAuth": true,  
  "IDs": [1,2,3,4,5]  
}
```

Dilersek buradaki yanıtı ekrana bastırmak yerine return edebiliriz. Yani

```js:index.js
fetch("settings.json")
.then(response => response.json())
.then((data) => console.log(data))
```
Burada dilersek `data` içerisinden `data.userName` gibi alt keyler ile de gereken veriyi çekebiliriz. Yani konsola `data` yerine `data.userName` gönderirsek çıktımız `muffinisamuffin` olacaktır.

# Örnek Fetch API Kullanımı
[JSONPlaceholder](https://jsonplaceholder.typicode.com/) üzerinden örnek bir API kullanımı yapabiliriz. Örneğin tüm todo listesini çekmek istiyoruz.

```js:index.js
fetch("https://jsonplaceholder.typicode.com/posts")
.then(response => response.json())
.then((data) => console.log(data))
```

Bu şekilde konsola bakınca elimizde büyükçe bir liste olacağını görebiliriz. Peki tüm itemleri ayrı ayrı yazdırmak istersek? Onun da çözümü basit

```js:index.js
fetch("https://jsonplaceholder.typicode.com/posts")
.then(response => response.json())
.then((data) => {data.forEach(item => console.log(item))})
```

Bu sayede tüm elemanlarımız ayrı bir satırda gelecektir. Bunu önde düzgün bir şekilde de listelebiliriz. Örneğin bir liste içine tüm başlıkları bastıralım

```js:index.js
let userlist = document.querySelector("ul")  
fetch("https://jsonplaceholder.typicode.com/posts").then(response => response.json()).then((data) => {  
    data.forEach( item => {  
        let lielem = document.createElement("li")  
        lielem.innerHTML = item.title  
        userlist.appendChild(lielem)  
  
    })  
})
```