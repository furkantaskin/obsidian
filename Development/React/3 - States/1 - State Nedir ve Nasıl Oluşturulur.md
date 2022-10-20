# State Nedir
Komponentlerin üzerinde değerinin değeşme potansiyeli olan bütün verileri tutan bir JS nesnesidir. Örnek vermek elimizde butona basınca değişecek bir görseller serisi olsun. Buradaki görseller için de bir index değeri tutalım. Eğer sonraki butonuna bastığımızda sonraki index değerinde bulunan görselin gelmesini istiyorsak o zaman görselin bulunduğu component yerine bir genel index değerinde güncelleme gerekecektir. İşte bu tür durumlarda kullandığımız nesneye State diyoruz.

>[!note]+ Detay
> State hakkında detaylı bilgi için [React'ın sitesini ziyaret edebiliriz ](https://beta.reactjs.org/learn/state-a-components-memory)

# State Oluşturma

Örneğin butona basılınca elimizdeki ismi değiştiren bir sistem yapalım. Burada basitçe bir state oluşturabiliriz.

```js:App.js
import {useState} from "react";  
  
  
function App() {  
  const [name, setName] = useState('Furkan');  
  return (  
    <div className="App">  
      <h1>Merhaba {name}</h1>  
      <button onClick={() => setName("Şaka")}>Change Name</button>  
    </div>  );  
}  
  
export default App;
```

Bu durumda bastığımız zaman program bizde ismi Merhaba Şaka olarak günceller.

State içinde JS tarafından verilen tüm veri tiplerinde tanımlama yapılabilir. Buradaki tipleri [[JavaScript Temelleri#Temel Yapılar | Temel Yapılar]]  içinde görmüştük.

![[JavaScript Temelleri#^d50320]]

Buradaki state güncellendiği zaman fonksiyon güncelleneceği için App içinde bulunan herhangi bir `console.log()` ibaresi de güncelleme alacaktır.

## Array State Oluşturma
Örneğin burada arkadaşların olduğu bir array düşünelim. Bu array içerisinde ekleme ve çıkarma işlemi yapmamız gerekirse burada takip edeceğimiz adımlar aslında çok basit.

```js:App.js
import {useState} from "react";  
  
  
function App() {  
  const [name, setName] = useState('Furkan');  
  const [friends, setFriends] = useState(["Ahmet", "Murat"])  
  return (  
    <div className="App">  
      <h1>Merhaba {name}</h1>  
      <button onClick={() => setName("Şaka")}>Change Name</button>  
      <br/><br/>      <hr/>      
      <button onClick={() => setFriends([...friends, "Ayşe"])}>Add another friend</button>  
      <h2>Arkadaşlar</h2>  
      {  
        friends.map((friend,index) => <div key={index}>{friend}</div>)  
      }  
    </div>  
  );  
}  
  
export default App;
```

>[!danger]+ DİKKAT
> Burada işlemler basit görünse de açıklamakta fayda var. Örnek olarak burada bir dizi var ve dizi içerisinde butona bastığımızda yeni bir eleman eklemesini istiyoruz. Önümüze iki engel çıkacak
> 1. `button` içerisindeki veriyi köşeli parantez yerine string göndermek. Bu durumda `.map` ile gelen fonksiyon patlayacaktır.
> 2. Dizinin sadece eklenecek elemanla güncellenmesi ve diğerlerinin silinmesi. Diziye eleman ekleme yerine diziiy baştan sonra güncelleyeceğimiz için liste Ahmet, Murat, Ayşe yerine sadece Ayşe olacaktır. Bunu önlemek için `...friends` ibaresini kullanmamız gerekecektir.

## Object State

Bu kısımda bazı durumlarda bir nesne kullanmamız gerekebilir. Bunu da dilersek state ile kontrol edebiliriz.

```js:App.js
import {useState} from "react";  
  
  
function App() {  
  const [name, setName] = useState('Furkan');  
  const [friends, setFriends] = useState(["Ahmet", "Murat"])  
  const [address, setAddress] = useState({title: "Konya", zip: 42060})  
  return (  
    <div className="App">  
      <h1>Merhaba {name}</h1>  
      <button onClick={() => setName("Şaka")}>Change Name</button>  
      <br/><br/>      <hr/>  
      <button onClick={() => setFriends([...friends, "Ayşe"])}>Add another friend</button>  
      <h2>Arkadaşlar</h2>  
      {  
        friends.map((friend,index) => <div key={index}>{friend}</div>)  
      }  
  
      <br/><br/>  
      <hr/>  
      <h2>Adres</h2>  
      <button onClick={() => setAddress({...address, title: "Ankara", zip: parseInt("06332", 10)})}>Change Address</button>  
      <div>{address.title} {address.zip}</div>  
    </div>  );  
}  
  
export default App;
```