Promise, asenkron gerçekleşen bir işlemin başarılı veya başarısız bir şekilde tamamlanmasını belirten bir nesnedir.  Belirli bir süre alabilecek işlemlerin sonuç durumuna göre burada başarılı veya başarısız olacak şekilde dönüşler olur. Burada [bir örnek](https://javascript.info/promise-basics) faydalı olacaktır. Kaynaktaki örneği değiştirip yeni örneği yemek sırası olarak da düşünebiliriz.

Örneğin bir yemek siparişi alıyoruz. Müşteriler bu yemeğe dair bilgi istiyor. İki ihtimal var:
1. Yemek yapılır ve müşteriye teslim edilir. Bu resolve olarak geçer
2. Yemek yaparken bir sorun (malzeme bitmesi, yangın vb.) çıkar ve yemek teslim edilemez, kullanıcı bilgilendirilir. Bu reject olarak geçer.

Bir API üzerinden veri almak gibi işlemlerde Promise bize büyük faydalar sağlayacaktır. Örneğin ürün listesinde olmayan bir ürün için müşterinin sipariş verdiğini düşünelim.

```js
const getOrder = (menu) => {  
    return new Promise((resolve,reject) => {  
        let choice = ['burger', 'pizza', 'wings']  
        if (choice.includes(menu)){  
            (resolve("Here is your order"))  
        }  
        reject("We don't have this menu")  
    })  
}  
getOrder("salad")  
    .then((data) => console.log(data))  
    .catch((e) => console.log(e))




const getOrder = (menu) => {  
    return new Promise((resolve,reject) => {  
        let choice = ['burger', 'pizza', 'wings']  
        if (choice.includes(menu)){  
            (resolve("Here is your order"))  
        }  
        reject("We don't have this menu")  
    })  
}  
getOrder("burger")  
    .then((data) => console.log(data))  
    .catch((e) => console.log(e))
```

Eğer biz burada burger olarak sipariş girersek sistem bize siparişi hazırlarken siparişin salata olarak gelmesi durumunda ellerinde salata olmayacağını söyleyecektir.

>[!info] Bilgi
>Eğer promise içinde iki tane `resolve` varsa sistem ilkini baz alacaktır.


Şimdi elimizdeki bir API üzerinden gelen bilgi başarılı olursa ekrana basalım, sorun çıkarsa hata gelsin.

```js
import axios from "axios";  
  
const getUsers = () => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/users");  
        resolve(data);  
    });  
};  
  
getUsers()  
    .then((data) => console.log(data))  
    .catch((e) => console.log(e));
```

Eğer teknik veya bizim tarafımızda bir hata yoksa karşımıza örnek kullanıcı listesi JSON olarak dönecektir.

Eğer ki biz post ve kullanıcıları ayrı ayrı çektirecek olursak 

```js
import axios from "axios";  
  
const getUsers = () => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/users");  
        resolve(data);  
    });  
};  
  
  
const getPost = (post_id) => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/posts/" + post_id);  
        resolve(data);  
    });  
};  
  
getUsers()  
    .then((data) => console.log(data))  
    .catch((e) => console.log(e));  
  
getPost(1)  
    .then((data) => console.log(data))  
    .catch((e) => console.log(e));
```

Burada elimizde bir sorun var. İki promise da asenkron olduğu için her çalıştırmada hangisinin cevabı ilk döndüreceği net değildir. Bu da sıra gerektiren işlemlerde soruna sebep olacaktır. Dilersek bunu belirli bir sıraya alabiliriz. Bunu bir `async/await` mantığı ile çözebiliriz. 

```js
import axios from "axios";  
  
const getUsers = () => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/users");  
        resolve(data);  
    });  
};  
  
  
const getPost = (post_id) => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/posts/" + post_id);  
        resolve(data);  
    });  
};  
  
(async () => {  
    await getUsers()  
        .then((data) => console.log(data))  
        .catch((e) => console.log(e));  
  
    await getPost(1)  
        .then((data) => console.log(data))  
        .catch((e) => console.log(e));  
})();
```
Son kısım ile artık fonksiyonlarımız sürekli olarak belirli bir sırada çalışacaktır. Buradaki yoğun `.then() / .catch()` sorununu kolay bir şekilde çözebiliriz. Tek yapmamız gereken `await` ve `console.log()` sistemi ile de yapabiliriz.

```js
import axios from "axios";  
  
const getUsers = () => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/users");  
        resolve(data);  
    });  
};  
  
  
const getPost = (post_id) => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/posts/" + post_id);  
        resolve(data);  
    });  
};  
  
(async () => {  
    const users = await getUsers();  
    const post = await getPost(1);  
  
    console.log(users);  
    console.log(post);  
})();
```

Buradaki hataları `.then() / .catch()` yerine `try / catch` ile de yapabiliriz.

```js
import axios from "axios";  
  
const getUsers = () => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/users");  
        resolve(data);  
        reject("Bir sorun oluştu")  
    });  
};  
  
  
const getPost = (post_id) => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/posts/" + post_id);  
        resolve(data);  
        reject("Bir sorun daha oluştu")  
    });  
};  
  
(async () => {  
    try{  
        const users = await getUsers();  
        const post = await getPost(1);  
  
        console.log(users);  
        console.log(post);  
    } catch(e){  
        console.log(e);  
    }  
})();
```

Eğer user içinde bir hata dönerse post çalışmayacağı için ekrana sadece "Bir sorun oluştu" yazacaktır. Ancak `getUser` doğru çalışıp `getPost` hata görürse çıktımız "Bir sorun daha oluştu" olacaktı.

## `Promise.all` kullanımı

Eğer elimizde birden fazla Promise varsa bunu `Promise.all()` ile kullanabiliriz. Bu sayede kod kalabalığı ortadan kalkacaktır. Buradaki mantık tüm sıralı promise yapısını çağırmak ve ilk hatada durumu kullanıcıya iletmekten geçer.

```js
import axios from "axios";  
  
const getUsers = () => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/users");  
        resolve(data);  
        reject("Bir sorun oluştu")  
    });  
};  
  
  
const getPost = (post_id) => {  
    return new Promise(async (resolve, reject) => {  
        const {data} = await axios("https://jsonplaceholder.typicode.com/posts/" + post_id);  
        resolve(data);  
        reject("Bir sorun daha oluştu")  
    });  
};  
  
Promise.all([getUsers(), getPost(1)])  
    .then(console.log)  
    .catch(console.log)
```